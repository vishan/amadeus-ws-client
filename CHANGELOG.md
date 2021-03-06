# Release 1.2.0 (Unreleased)
* Added support for requesting rules for specific Fare Components after a pricing request in ``Fare_CheckRules`` (https://github.com/amabnl/amadeus-ws-client/issues/21)
* Added support for requesting parametrized Fare Families in ``Fare_MasterPricerTravelBoardSearch`` and ``Fare_MasterPricerCalendar`` (https://github.com/amabnl/amadeus-ws-client/issues/31)
* Added a Client parameter to disable the population of the XML string in the Result object (https://github.com/amabnl/amadeus-ws-client/issues/33) 
* ``Queue_List``: added new request options:
    - Search Criteria
    - Sort by Creation, Ticketing or Departure date
    - Filter the amount of results
    - Provide different Office ID
* Implemented ``Ticket_DeleteTSMP`` message
* Implemented ``Ticket_DisplayTSMP`` message
* Implemented ``Ticket_DisplayTSMFareElement`` message
* Implemented ``DocIssuance_IssueCombined`` message
* Implemented ``PNR_NameChange`` message
* Implemented ``PointOfRef_Search`` message
* Request Creator split up in 1 dedicated class per message.
* Response Handler split up in 1 dedicated class per message.

# Release 1.1.0 (19 October 2016)

* ``Fare_MasterPricerTravelBoardSearch``: added new request options (https://github.com/amabnl/amadeus-ws-client/issues/20):
    - Preferred/excluded/... airlines option 'airlineOptions'.
    - Itinerary date: support for Date range +/- 1 day.
    - Itinerary date: Specify date &amp; time of segment as departure or arrival date &amp; time.
    - Itinerary date: deprecated 'date' and 'time' properties, replaced by unified 'dateTime' property.
    - Support for flight options such as direct flight, non-stop flight, etc.
    - Support for Cabin Mode (Mandatory, Major, Recommended) when specifying a cabin code.
    - Support for Fare Options such as Published Fares, Unifares, Electronic/Paper ticketing, ...
    - Support for "Price to beat" feature.
* ``PNR_AddMultiElements``: Support for new request options:
    - Add support for adding AIR when creating or updating a PNR.
    - Add support for adding ARNK segments when creating or updating a PNR.
    - Add support for Group PNR in the regular PNR_AddMultiElements call (previously this was only in the pnrCreatePnr)
    - Add support for connected segments in an itinerary (deprecated 'tripSegments' option)
* ``DocIssuance_IssueTicket``: Support for Compound Options in request, such as Consolidator method (https://github.com/amabnl/amadeus-ws-client/issues/23)
* ``Air_RetrieveSeatMap``: Support for new request options:
    - Request prices
    - Cabin code
    - Provide Record Locator
    - Number of passengers
    - Booking status
    - Currency conversion
    - Traveller information
* ``Fare_PricePnrWithBookingClass``: added support for extra request options:
    - Negotiated corporate fares
    - Corporate unifares
    - OB Fees *(message version 13+ only)*
    - Pax/PTC Discounts
    - Point of Sale and Point of Ticketing override
    - Pricing Logic (IATA or other) *(message version 13+ only)*
    - Ticket Type (e-ticket, paper, both)
    - Add taxes
    - Exempt taxes
    - Selective pricing: select segments, passengers and/or TST's
    - Past date pricing
    - Award Pricing

*These pricing options are also available for the* ``Fare_InformativePricingWithoutPNR`` *message version 13+*

* Implemented ``PNR_TransferOwnership``
* Implemented ``Ticket_DisplayTST``
* Implemented ``Ticket_CreateTSMFromPricing``
* Implemented ``Service_IntegratedPricing``
* Implemented ``DocIssuance_IssueMiscellaneousDocuments``
* Implemented ``Fare_MasterPricerCalendar``
* Implemented ``Fare_InformativeBestPricingWithoutPNR``
* Implemented ``Fare_PricePNRWithLowerFares``
* Implemented ``Fare_PricePNRWithLowestFare``
* Implemented ``MiniRule_GetFromPricing``
* Implemented ``Offer_CreateOffer``

# Release 1.0.0 (18 September 2016)

* ``PNR_AddMultiElements``: support for adding OSI elements to a PNR.
* Implemented ``Ticket_DeleteTST``
* Updated docs for 1.0.0 release.
* Released version 1: now following [semantic versioning](http://semver.org/).

# 2016-09

* Implemented ``SalesReports_DisplayQueryReport``
* Implemented ``Air_MultiAvailability``
* Added support for multiple WSDL's (interfaces) in a WSAP (https://github.com/amabnl/amadeus-ws-client/issues/5)
* Fixed a bug while authenticating with SoapHeader 2 (https://github.com/amabnl/amadeus-ws-client/pull/15) - Sergey Gladkovskiy
* PSR-2 code style enforced via StyleCI

# 2016-08

* Implemented ``PNR_DisplayHistory``
* Implemented ``Fare_InformativePricingWithoutPNR`` (https://github.com/amabnl/amadeus-ws-client/issues/13)

# 2016-07

* Implemented ``Air_RetrieveSeatMap``

# 2016-06

* Implemented ``Fare_PricePNRWithBookingClass`` version 13 and up (https://github.com/amabnl/amadeus-ws-client/issues/6)
* Implemented ``DocIssuance_IssueTicket`` (https://github.com/amabnl/amadeus-ws-client/issues/7)
* Implemented ``Info_EncodeDecodeCity``
* Implemented ``Offer_ConfirmCarOffer``
* Implemented checking for response errors for all supported messages _except Command_Cryptic_. For ``Command_Cryptic``, you need to parse the response yourself to check for errors.
* Removed the 'asString' request option - the `Amadeus\Client\Result` object now always contains the result XML in the `responseXml` property.

# 2016-05

Completely re-worked the Result being returned by Web Service calls: the XML or PHP object is now encapsulated in an `Amadeus\Client\Result` object which makes checking for errors or warnings much easier. 

The library now always returns both the PHP object generated by `\SoapClient` as well as the result string. 

The Result object also has a `status` property which contains the status of the message performed: FATAL, OK, WARN or INFO. 

The library will now also convert `\SoapFault` exceptions to a FATAL result status. 

(https://github.com/amabnl/amadeus-ws-client/issues/2)

# 2016-04

* Added support for providing custom `\SoapClient` options (https://github.com/amabnl/amadeus-ws-client/issues/4)
* Implemented Amadeus SoapHeader 2 support (https://github.com/amabnl/amadeus-ws-client/issues/3)
* Changed all references 'tatoo' to 'tattoo' for consistency (https://github.com/amabnl/amadeus-ws-client/issues/1)

# UNSTABLE

The library's API will be unstable until we release the first version.
