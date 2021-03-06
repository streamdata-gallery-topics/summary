swagger: "2.0"
x-collection-name: eBay
x-complete: 1
info:
  title: Ebay
  description: the-ebay-platform-offers-an-unprecedented-opportunity-to-build-a-new-ebay-business-or-expand-your-current-business-reach-new-customers-and-create-a-potential-new-stream-of-revenue--leverage-the-resources-of-the-ebay-developers-program-to-tap-into-the-ebay-marketplace-with-millions-of-active-users-globally-with-tools-and-services-that-meet-the-diverse-needs-of-buyers-and-sellers-
  contact:
    name: eBay Inc.
  version: 1.0.0
host: api.ebay.com
basePath: /
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /item_summary/search:
    get:
      summary: Get Item Summary Search
      description: 'This call performs an advanced search for items. You can search
        by keyword, category, eBay product Id (EPID), or gtin. Or a combination of
        these. Encoding Parameters and Headers As with all query parameter values,
        the fields parameter value and request header values must be URL encoded.
        For better readability, the examples in this document omit the encoding. Example:
        &nbsp;&nbsp;search?q=world cup soccer ball&amp;aspect_filter=categoryId:20863,Brand:{Nike|Wilson}
        Encoded Example: &nbsp;&nbsp; search?q=world cup soccer ball&amp;aspect_filter=categoryId%3A20863%2CBrand%3A%7BNike%7CWilson%7D
        For more information about encoding, see HTML URL Encoding Reference The following
        are examples of using filters: The following call returns 4,330,774 items.
        &nbsp;&nbsp;&nbsp;/buy/browse/v1/item_summary/search?q=phone This call, which
        limits the results to the category &quot;Cell Phones &amp; Smartphones&quot;,
        returns 142,098 items. &nbsp;&nbsp;&nbsp;/buy/browse/v1/item_summary/search?q=phone&amp;category_ids=9355
        These calls, which limit results to a Samsung Galaxy S5, returns 97 items.
        &nbsp;&nbsp;&nbsp;/buy/browse/v1/item_summary/search?q=phone&amp;category_ids=220&amp;epid=182527490
        &nbsp;&nbsp;&nbsp;or &nbsp;&nbsp;&nbsp;/buy/browse/v1/item_summary/search?epid=182527490
        Controlling what is returned You can also control what is returned by using
        the fieldgroups field. In addition to returning items, which is the default,
        you can return refinements (metadata) about an item that enables you to create
        aspect histograms. A histogram enables users to drill down in each refinement
        narrowing the search results. You can return: ASPECT_REFINEMENTS - Lets shoppers
        refine the result set by variation aspects, such as Brand, Color, etc. BUYING_OPTION_REFINEMENT
        - Lets shoppers refine the result set by either FIXED_PRICE or AUCTION CATEGORY_REFINEMENTS
        - Lets shoppers refine the result set by items in a category CONDITION_REFINEMENT
        - Lets shoppers refine the result set by item condition, such as NEW, USED,
        etc. MATCHING_ITEMS - The default, which returns the items. When used with
        one or more of the refinement values above the specified refinements and all
        the matching items are returned. FULL - This returns all the refinement containers
        and all the matching items. Filtering by aspects You can use the aspect refinements
        returned to filter the result set using the aspect_filter field. For example:
        This call gets a list of the aspects pairs for the item and the dominant category
        (category most of the items are in). /buy/browse/v1/item_summary/search?q=world
        cup soccer ball&amp;fieldgroups=ASPECT_REFINEMENTS This call filters the items
        by one of the aspect pairs returned and the dominant category ( categoryId
        is required when using aspect_filter) /buy/browse/v1/item_summary/search?q=world
        cup soccer ball&amp;aspect_filter=categoryId:20863,Brand:{adidas} This call
        filters the items by multiple aspects /buy/browse/v1/item_summary/search?q=world
        cup soccer ball&amp;aspect_filter=categoryId:20863,Brand:{adidas},Featured
        Refinements:{Adidas Match Ball} This call filters the items by multiple aspect
        values /buy/browse/v1/item_summary/search?q=world cup soccer ball&amp;aspect_filter=categoryId:20863,Brand:{Nike|Wilson}
        Additional filters There are also multiple filters you can use to refine the
        result set, such as listing format, item condition, price range, listing end
        date, location, and more. You can use multiple filters in a single call. For
        a list and details of the supported filters, see search Call Field Filters.
        Pagination and sort controls There are pagination controls ( limit and offset
        fields) and sort query parameter that control/sort the data that is returned.
        By default, the results are sorted by &quot;Best Match&quot;. For more information
        about Best Match, see the eBay help page Best Match. Request headers You will
        want to use the X-EBAY-C-ENDUSERCTX request header with this call. If you
        are an eBay Network Partner you must use affiliateCampaignId=ePNCampaignId,affiliateReferenceId=referenceId
        in the header in order to be paid for selling eBay items on your site and
        it is strongly recommended you use contextualLocation to improved the estimated
        delivery window information. For details see, Request headers in the Buy APIs
        Overview. Restrictions For a list of supported sites and other restrictions,
        see API Restrictions. Limitation: This call can return a maximum of 10,000
        items.'
      operationId: search
      x-api-path-slug: item-summarysearch-get
      parameters:
      - in: query
        name: aspect_filter
        description: The aspect name/value pairs and category, which is required,
          to use to limit the results
      - in: query
        name: category_ids
        description: The category Ids to use to limit the results
      - in: query
        name: epid
        description: The EPID is the eBay product identifier of a product from the
          eBay product catalog
      - in: query
        name: fieldgroups
        description: This field lets you control what is to be returned in the response
      - in: query
        name: filter
        description: This field supports multiple field filters that can be used to
          use to limit/customize the result set
      - in: query
        name: gtin
        description: This field lets you search by the Global Trade Item Number of
          the item as defined by http://www
      - in: query
        name: limit
        description: The number of items in a result set
      - in: query
        name: offset
        description: The number of items to skip in the result set
      - in: query
        name: q
        description: A string consisting of one or more words that are used for a
          search of items on eBay
      - in: query
        name: sort
        description: Specifies the order and the field name to use to sort the items
      responses:
        200:
          description: OK
      tags:
      - Auctions
      - Item
      - Summary
      - Search