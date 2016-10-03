# dataLayer-shopify

## Definition
A data layer helps you collect more accurate analytics data, that in turn allows you to better understand what potential buyers are doing on your website and where you can make improvements. It also reduces the time to implement marketing tags on a website, and reduces the need for IT involvement, leaving them to get on with implementing new features and fixing bugs.

## Resources
https://help.shopify.com/themes/liquid/objects

http://www.datalayerdoctor.com/a-gentle-introduction-to-the-data-layer-for-digital-marketers/ 

http://www.simoahava.com/analytics/data-layer/

## Integration Instructions
Please keep note that this is a base template that attempts to exploit Shopify’s data rendering capabilities and create an ease of integration for dataLayers that can be reused across all Shopify sites. Nonetheless, each site could carry variations that may not be completely compatible with this template. There may also be some areas of data we may have missed, may be a new configuration, or we wouldn’t know is necessary for your efforts. It is highly recommended to review the entire implementation and make your own configurations if needed.

Please let us know if you have any questions or concerns and we will be happy to follow up as soon as possible :)

There are 2 types of Installations provided below. Review each option and choose 1 **only**.

### Installation Option 1: 
If the **Checkout page is _can be edited_ editable**, use this option. Note that Checkout page edits are only available on Shopify Plus.

#### Assets
|Assets|Integration Type| Asset Type|
| --------|---------|---------|
|theme.liquid ( or your primary theme template )|Modification|**Layout:** *Online Store > Themes > ... > Edit HTML/CSS > Layout > theme.liquid ( or primary theme template )*|
|confirmation page|Modification|**Admin Setting:** *Settings > Checkout > Order Processing > Additional Pixels & Scripts*|
|dataLayer-allPages|Creation|**Snippet:** *Online Store > Themes > ... > Edit HTML/CSS > Snippets > ( will create Snippet in instructions )*|
|dataLayer-confirmation|Creation|**Snippet:** *Online Store > Themes > ... > Edit HTML/CSS > Snippets > ( will create Snippet in instructions )*|
|prerequisite library|Creation or Modification|This can either be a **Snippet** or **loaded into your own prerequisite library** |
|Google Tag Manager or any other Tag Manager Code|Creation or Modification|This can either be a **Snippet** or added directly into your **Layout**|

#### Instructions ( Option 1 )
1. **GTM / Tag Manager Installation or Modification**
  1. Within the **theme.liquid** layout, place the GTM / Tag Manager container ( snippet or actual code block ) **directly below the opening \<body> tag**.
  2.  Within the **confirmation page** the GTM / Tag Manager container ( snippet or actual code block ) should be placed above all additional scripts.
  
2. **Create the dataLayer Snippets ( _use exact naming and casing!_ )**
  1. Create a snippet called dataLayer-allPages, add the provided dataLayer-allPages.js in the newly created snippet. In the code, navigate to the “Dynamic Dependencies” section and make any necessary changes.


==================

### Installation Option 2: 
If the **Checkout page is _can be edited_**, use this option.

#### Assets
|Assets|Integration Type| Asset Type|
| --------|---------|---------|
|theme.liquid ( or your primary theme template )|Modification|**Layout:** *Online Store > Themes > ... > Edit HTML/CSS > Layout > theme.liquid ( or primary theme template )*|
|checkout.liquid|Modification|**Layout:** *Online Store > Themes > ... > Edit HTML/CSS > Layout > checkout.liquid*|
|dataLayer-allPages|Creation|**Snippet:** *Online Store > Themes > ... > Edit HTML/CSS > Snippets > ( will create Snippet in instructions )*|
|dataLayer-confirmation|Creation|**Snippet:** *Online Store > Themes > ... > Edit HTML/CSS > Snippets > ( will create Snippet in instructions )*|
|prerequisite library|Creation or Modification|This can either be a snippet or loaded into your own prerequisite library |

## Pages & Variables Guide

### Pages
The Page types and descriptions the dataLayer will exist.

|Pages / Actions |Description |
| --------|---------|
|All Pages |Sitewide |
|Landing Page |When a user first lands on the site|
|Homepage|Primary web page|
|Blog Page|Blog Articles ( will not trigger on blog category pages, only within articles )|
|Product List Page ( Collections )|List of your products|
|Product Page|View of a single product|
|Add to Cart|User adds anything to their cart|
|Cart Page|User views their cart|
|Checkout ( Only Available on Shopify Plus )|Triggers on the “Customer Information” section of the Checkout funnel|
|Add Payment Info ( Only Available on Shopify Plus )|Triggers when user lands on “Payment Information” of Checkout funnel|
|Confirmation Page|Successful Purchase|

### Variables
All information the dataLayer is able to extract and the pages they can be extracted from.

|All Variables Collected |Description |Page(s) Available|
| --------|---------|---------|
|Page Type	|The page type ( Landing Page, Blog Page, Product Page, etc )|*All*|
|Event|Same as page type ( used for triggers )|*All* |
|Shopify User ID	|Unique customer ID issued by Shopify either after successful purchase of if customer signs in|*Confirmation Page / All Pages when customer signs in*|
|Log State|If user is logged in or out|*All Pages*|
|Timestamp|Accurately capture time|*All Pages*|
|Blog Author|Author of current article|*Blog Page*|
|Blog Title|Title of current article|*Blog Page*|
|Blog Created|Date current article was created|*Blog Page*|
|Product ID|Unique product ID that defines all variants of single product|*Product Page / Cart / Confirmation Page*|
|Product SKU|Defines the SKU of a product|*Product Page / Cart / Confirmation Page*|
|Product Variant|Defines the variant ID|*Product Page / Cart / Confirmation Page*|
|Product Category ( collections )|Get category of a product|*Product List Page / Product*, **_Cart & Confirmation Page are under construction_**|
|Product Price|Price of a product ( returns price of product regardless of promo discount )|*Product Page / Cart / Confirmation Page*|
|Product Name|Name of a product|*Product Page / Cart / Confirmation Page*|
|Product Quantity|Quantity of a product|*Cart / Confirmation Page*|
|Transaction ID|Unique ID rendered for a successful purchase ( Only accessible via API )|*Confirmation Page*|
|Transaction Number|Unique ID rendered for a successful purchase ( Accessible in Shopify Order Report )|*Confirmation Page*|
|Transaction Affiliation|Shop name|*Confirmation Page*|
|Transaction Total|Total amount of transaction subtracted by discounts|*Confirmation Page*|
|Transaction Tax|Tax of entire transaction|*Confirmation Page*|
|Transaction Shipping|Cost of transaction shipping|*Confirmation Page*|
|Transaction Promo Code|Promotional code |*Confirmation Page*|
|Transaction Promo Discount |Amount of discount promo code provided|*Confirmation Page*|