# mmm-uk-pollen-forecast
A module for MagicMirror<sup>2</sup> that displays pollen data for your area in the UK.

<img src="pollen_forecast.jpg"></img>

British pollen sufferers unite!
This module scrapes the [Met Office website](https://www.metoffice.gov.uk/weather/warnings-and-advice/seasonal-advice/pollen-forecast) for the pollen forecast for your magic mirror, so you have advance notice of what level of misery you can expect in the coming days. Unfortunately the Met Office do not provide a free or low-cost API for pollen data, so we have to resort to more fragile methods. 



Notes: 
- this module maybe useful to anyone who wants to scrape a website for use on a mirror. No iframes here! We parse the target website with cheerio, then dump out the html to a cache file. Then the client-side script picks this up for display. (Is there an XSS vulnerability? Maybe, if the Met Office is hacked.)
- this module only supports the UK.
- the module is likely to break if the Met Office website changes.
- Pull requests, bug reports and feature requests [are welcome.](https://github.com/szech/mmm-uk-pollen-forecast) 
- I am not a js coder, so please don't judge too harshly :)

Thanks to Michael Teeuw for this great platform, and to the other mm modules for inspiration and open source code 
(*・ω・)ﾉ


## Config
| **Option** | **Description** |
| --- | --- |
| `updateIntervalHours` | (optional) Set to desired update interval (in hours), default is `2`. |
| `region` | your region. required. see below for the possible values. |
| `first_display_date_DD_MM` | optional. will show the module from this date onwards. format: DD-MM  |
| `last_display_date_DD_MM` | optional. will hide the module after this date onwards until next year. format: DD-MM. see below for more details |



## Regions

pick the 2-letter code that corresponds to your region and use this in the config.

|  Region | Corresponds to...  |
| --- | --- |
|  os  |  Orkney & Shetland    |
|  ta  |  Central, Tayside & Fife  |
|  he  |  Highlands & Eilean Siar  |
|  gr  |  Grampian  |
|  st  |  Strathclyde  |
|  dg  |  Dumfries, Galloway, Lothian & Borders  |
|  ni  |  Northern Ireland  |
|  wl  |  Wales  |
|  nw  |  North West England  |
|  ne  |  North East England  |
|  yh  |  Yorkshire & Humber  |
|  wm  |  West Midlands  |
|  em  |  East Midlands  |
|  ee  |  East of England  |
|  sw  |  South West England  |
|  se  |  London & South East England  |

## First Display Date & Last Display Date

Since pollen is a seasonal affliction, you can configure when you want the module to be visible using `first_display_date_DD_MM` & `last_display_date_DD_MM` in the config.

The format must be `DD-MM` e.g. `01-04` ==> 1st April.
If you want it to display all year round, you can use a blank entry `''` or `'always'`.

You can check the general seasonality of pollen with the University of Worcester's [seasonal pollen calendar](
https://www.worcester.ac.uk/about/academic-schools/school-of-science-and-the-environment/science-and-the-environment-research/national-pollen-and-aerobiology-research-unit/pollen-calendar.aspx)


## Installation
  1. Clone this repo into your magic mirror `modules` directory. 
  2. cd in there and run `npm install`
  2. Create an entry in your `config.js` file to tell this module where to display on screen.
  3. Make sure you set the region in your config entry. see table for possible values.
  4. Reload/refresh magic mirror
  5. Profit!


 **Example config.js entry:**
```
 {
    module: 'mmm-uk-pollen-forecast',
    position: 'bottom_center',
    config: {
        updateIntervalHours : 2,    // update every 2 hrs
        region : 'se',              // forecast for London & SE England
        first_display_date_DD_MM: '01-04', // show module from 1st April
        last_display_date_DD_MM: '01-09'  // hide module after 1st September

    }
 },
```



## troubleshooting:
- try `npm install -g` in step 2 
- refresh the browser window where the mirror is displayed
- restart the mm server
- double check the config.js entry
- have you configured the module to be hidden?
- do you have enough antihistamines?
- avoid alcohol, it tends to make your hayfever symptoms worse :'(



