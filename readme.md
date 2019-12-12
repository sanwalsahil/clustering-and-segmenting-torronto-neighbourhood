# 1. IMPORTING BASIC LIBRARIES


```python
# importing libraries
import pandas as pd
import numpy as np
import requests
from bs4 import BeautifulSoup
```


```python
!conda install -c conda-forge folium=0.5.0 --yes
```

    Collecting package metadata (repodata.json): ...working... done
    Solving environment: ...working... 
    Warning: 4 possible package resolutions (only showing differing packages):
      - anaconda::ca-certificates-2019.8.28-0, anaconda::openssl-1.1.1d-he774522_2
      - anaconda::ca-certificates-2019.8.28-0, defaults::openssl-1.1.1d-he774522_2
      - anaconda::openssl-1.1.1d-he774522_2, defaults::ca-certificates-2019.8.28-0
      - defaults::ca-certificates-2019.8.28-0, defaults::openssl-1.1.1d-he774522_2done
    
    ## Package Plan ##
    
      environment location: C:\Users\daisycharlie\Anaconda3\envs\tensor2_real
    
      added / updated specs:
        - folium=0.5.0
    
    
    The following packages will be downloaded:
    
        package                    |            build
        ---------------------------|-----------------
        altair-3.3.0               |           py37_0         755 KB  conda-forge
        branca-0.3.1               |             py_0          25 KB  conda-forge
        certifi-2019.9.11          |           py37_0         147 KB  conda-forge
        folium-0.5.0               |             py_0          45 KB  conda-forge
        vincent-0.4.4              |             py_1          28 KB  conda-forge
        ------------------------------------------------------------
                                               Total:        1001 KB
    
    The following NEW packages will be INSTALLED:
    
      altair             conda-forge/win-64::altair-3.3.0-py37_0
      branca             conda-forge/noarch::branca-0.3.1-py_0
      folium             conda-forge/noarch::folium-0.5.0-py_0
      vincent            conda-forge/noarch::vincent-0.4.4-py_1
    
    The following packages will be SUPERSEDED by a higher-priority channel:
    
      certifi                                          anaconda --> conda-forge
    
    
    
    Downloading and Extracting Packages
    
    certifi-2019.9.11    | 147 KB    |            |   0% 
    certifi-2019.9.11    | 147 KB    | #          |  11% 
    certifi-2019.9.11    | 147 KB    | ########## | 100% 
    
    altair-3.3.0         | 755 KB    |            |   0% 
    altair-3.3.0         | 755 KB    | 2          |   2% 
    altair-3.3.0         | 755 KB    | 8          |   8% 
    altair-3.3.0         | 755 KB    | ##3        |  23% 
    altair-3.3.0         | 755 KB    | ####2      |  42% 
    altair-3.3.0         | 755 KB    | ######9    |  70% 
    altair-3.3.0         | 755 KB    | ########6  |  87% 
    altair-3.3.0         | 755 KB    | ########## | 100% 
    
    branca-0.3.1         | 25 KB     |            |   0% 
    branca-0.3.1         | 25 KB     | ########## | 100% 
    
    folium-0.5.0         | 45 KB     |            |   0% 
    folium-0.5.0         | 45 KB     | ###5       |  35% 
    folium-0.5.0         | 45 KB     | ########## | 100% 
    
    vincent-0.4.4        | 28 KB     |            |   0% 
    vincent-0.4.4        | 28 KB     | #####7     |  58% 
    vincent-0.4.4        | 28 KB     | ########## | 100% 
    Preparing transaction: ...working... done
    Verifying transaction: ...working... done
    Executing transaction: ...working... done
    

# 2. FETCHING DATA AND PREPROCESSING IT


```python
website_url = requests.get('https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M').text
```


```python
soup = BeautifulSoup(website_url,'lxml')
print(soup.prettify())
```

    <!DOCTYPE html>
    <html class="client-nojs" dir="ltr" lang="en">
     <head>
      <meta charset="utf-8"/>
      <title>
       List of postal codes of Canada: M - Wikipedia
      </title>
      <script>
       document.documentElement.className="client-js";RLCONF={"wgBreakFrames":!1,"wgSeparatorTransformTable":["",""],"wgDigitTransformTable":["",""],"wgDefaultDateFormat":"dmy","wgMonthNames":["","January","February","March","April","May","June","July","August","September","October","November","December"],"wgMonthNamesShort":["","Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"],"wgRequestId":"XeqcoApAICgAAEWRf8sAAADN","wgCSPNonce":!1,"wgCanonicalNamespace":"","wgCanonicalSpecialPageName":!1,"wgNamespaceNumber":0,"wgPageName":"List_of_postal_codes_of_Canada:_M","wgTitle":"List of postal codes of Canada: M","wgCurRevisionId":929562264,"wgRevisionId":929562264,"wgArticleId":539066,"wgIsArticle":!0,"wgIsRedirect":!1,"wgAction":"view","wgUserName":null,"wgUserGroups":["*"],"wgCategories":["Communications in Ontario","Postal codes in Canada","Toronto","Ontario-related lists"],"wgPageContentLanguage":"en","wgPageContentModel":"wikitext","wgRelevantPageName":
    "List_of_postal_codes_of_Canada:_M","wgRelevantArticleId":539066,"wgIsProbablyEditable":!0,"wgRelevantPageIsProbablyEditable":!0,"wgRestrictionEdit":[],"wgRestrictionMove":[],"wgMediaViewerOnClick":!0,"wgMediaViewerEnabledByDefault":!0,"wgPopupsReferencePreviews":!1,"wgPopupsConflictsWithNavPopupGadget":!1,"wgVisualEditor":{"pageLanguageCode":"en","pageLanguageDir":"ltr","pageVariantFallbacks":"en"},"wgMFDisplayWikibaseDescriptions":{"search":!0,"nearby":!0,"watchlist":!0,"tagline":!1},"wgWMESchemaEditAttemptStepOversample":!1,"wgULSCurrentAutonym":"English","wgNoticeProject":"wikipedia","wgWikibaseItemId":"Q3248240","wgCentralAuthMobileDomain":!1,"wgEditSubmitButtonLabelPublish":!0};RLSTATE={"ext.globalCssJs.user.styles":"ready","site.styles":"ready","noscript":"ready","user.styles":"ready","ext.globalCssJs.user":"ready","user":"ready","user.options":"ready","user.tokens":"loading","ext.cite.styles":"ready","mediawiki.legacy.shared":"ready",
    "mediawiki.legacy.commonPrint":"ready","jquery.tablesorter.styles":"ready","wikibase.client.init":"ready","ext.visualEditor.desktopArticleTarget.noscript":"ready","ext.uls.interlanguage":"ready","ext.wikimediaBadges":"ready","mediawiki.skinning.interface":"ready","skins.vector.styles":"ready"};RLPAGEMODULES=["ext.cite.ux-enhancements","site","mediawiki.page.startup","mediawiki.page.ready","jquery.tablesorter","mediawiki.searchSuggest","ext.gadget.teahouse","ext.gadget.ReferenceTooltips","ext.gadget.watchlist-notice","ext.gadget.DRN-wizard","ext.gadget.charinsert","ext.gadget.refToolbar","ext.gadget.extra-toolbar-buttons","ext.gadget.switcher","ext.centralauth.centralautologin","mmv.head","mmv.bootstrap.autostart","ext.popups","ext.visualEditor.desktopArticleTarget.init","ext.visualEditor.targetLoader","ext.eventLogging","ext.wikimediaEvents","ext.navigationTiming","ext.uls.compactlinks","ext.uls.interface","ext.cx.eventlogging.campaigns","ext.quicksurveys.init",
    "ext.centralNotice.geoIP","ext.centralNotice.startUp","skins.vector.js"];
      </script>
      <script>
       (RLQ=window.RLQ||[]).push(function(){mw.loader.implement("user.tokens@tffin",function($,jQuery,require,module){/*@nomin*/mw.user.tokens.set({"patrolToken":"+\\","watchToken":"+\\","csrfToken":"+\\"});
    });});
      </script>
      <link href="/w/load.php?lang=en&amp;modules=ext.cite.styles%7Cext.uls.interlanguage%7Cext.visualEditor.desktopArticleTarget.noscript%7Cext.wikimediaBadges%7Cjquery.tablesorter.styles%7Cmediawiki.legacy.commonPrint%2Cshared%7Cmediawiki.skinning.interface%7Cskins.vector.styles%7Cwikibase.client.init&amp;only=styles&amp;skin=vector" rel="stylesheet"/>
      <script async="" src="/w/load.php?lang=en&amp;modules=startup&amp;only=scripts&amp;raw=1&amp;skin=vector">
      </script>
      <meta content="" name="ResourceLoaderDynamicStyles"/>
      <link href="/w/load.php?lang=en&amp;modules=site.styles&amp;only=styles&amp;skin=vector" rel="stylesheet"/>
      <meta content="MediaWiki 1.35.0-wmf.5" name="generator"/>
      <meta content="origin" name="referrer"/>
      <meta content="origin-when-crossorigin" name="referrer"/>
      <meta content="origin-when-cross-origin" name="referrer"/>
      <link href="android-app://org.wikipedia/http/en.m.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M" rel="alternate"/>
      <link href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=edit" rel="alternate" title="Edit this page" type="application/x-wiki"/>
      <link href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=edit" rel="edit" title="Edit this page"/>
      <link href="/static/apple-touch/wikipedia.png" rel="apple-touch-icon"/>
      <link href="/static/favicon/wikipedia.ico" rel="shortcut icon"/>
      <link href="/w/opensearch_desc.php" rel="search" title="Wikipedia (en)" type="application/opensearchdescription+xml"/>
      <link href="//en.wikipedia.org/w/api.php?action=rsd" rel="EditURI" type="application/rsd+xml"/>
      <link href="//creativecommons.org/licenses/by-sa/3.0/" rel="license"/>
      <link href="https://en.wikipedia.org/wiki/List_of_postal_codes_of_Canada:_M" rel="canonical"/>
      <link href="//login.wikimedia.org" rel="dns-prefetch"/>
      <link href="//meta.wikimedia.org" rel="dns-prefetch"/>
      <!--[if lt IE 9]><script src="/w/resources/lib/html5shiv/html5shiv.js"></script><![endif]-->
     </head>
     <body class="mediawiki ltr sitedir-ltr mw-hide-empty-elt ns-0 ns-subject mw-editable page-List_of_postal_codes_of_Canada_M rootpage-List_of_postal_codes_of_Canada_M skin-vector action-view">
      <div class="noprint" id="mw-page-base">
      </div>
      <div class="noprint" id="mw-head-base">
      </div>
      <div class="mw-body" id="content" role="main">
       <a id="top">
       </a>
       <div class="mw-body-content" id="siteNotice">
        <!-- CentralNotice -->
       </div>
       <div class="mw-indicators mw-body-content">
       </div>
       <h1 class="firstHeading" id="firstHeading" lang="en">
        List of postal codes of Canada: M
       </h1>
       <div class="mw-body-content" id="bodyContent">
        <div class="noprint" id="siteSub">
         From Wikipedia, the free encyclopedia
        </div>
        <div id="contentSub">
        </div>
        <div id="jump-to-nav">
        </div>
        <a class="mw-jump-link" href="#mw-head">
         Jump to navigation
        </a>
        <a class="mw-jump-link" href="#p-search">
         Jump to search
        </a>
        <div class="mw-content-ltr" dir="ltr" id="mw-content-text" lang="en">
         <div class="mw-parser-output">
          <p>
           This is a list of
           <a href="/wiki/Postal_codes_in_Canada" title="Postal codes in Canada">
            postal codes in Canada
           </a>
           where the first letter is M. Postal codes beginning with M are located within the city of
           <a href="/wiki/Toronto" title="Toronto">
            Toronto
           </a>
           in the province of
           <a href="/wiki/Ontario" title="Ontario">
            Ontario
           </a>
           . Only the first three characters are listed, corresponding to the Forward Sortation Area.
          </p>
          <p>
           <a href="/wiki/Canada_Post" title="Canada Post">
            Canada Post
           </a>
           provides a free postal code look-up tool on its website,
           <sup class="reference" id="cite_ref-1">
            <a href="#cite_note-1">
             [1]
            </a>
           </sup>
           via its
           <a href="/wiki/Mobile_app" title="Mobile app">
            applications
           </a>
           for such
           <a class="mw-redirect" href="/wiki/Smartphones" title="Smartphones">
            smartphones
           </a>
           as the
           <a href="/wiki/IPhone" title="IPhone">
            iPhone
           </a>
           and
           <a href="/wiki/BlackBerry" title="BlackBerry">
            BlackBerry
           </a>
           ,
           <sup class="reference" id="cite_ref-2">
            <a href="#cite_note-2">
             [2]
            </a>
           </sup>
           and sells hard-copy directories and
           <a href="/wiki/CD-ROM" title="CD-ROM">
            CD-ROMs
           </a>
           . Many vendors also sell validation tools, which allow customers to properly match addresses and postal codes. Hard-copy directories can also be consulted in all post offices, and some libraries.
          </p>
          <h2>
           <span class="mw-headline" id="Toronto_-_FSAs">
            <a href="/wiki/Toronto" title="Toronto">
             Toronto
            </a>
            -
            <a href="/wiki/Postal_codes_in_Canada#Forward_sortation_areas" title="Postal codes in Canada">
             FSAs
            </a>
           </span>
           <span class="mw-editsection">
            <span class="mw-editsection-bracket">
             [
            </span>
            <a href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=edit&amp;section=1" title="Edit section: Toronto - FSAs">
             edit
            </a>
            <span class="mw-editsection-bracket">
             ]
            </span>
           </span>
          </h2>
          <p>
           Note: There are no rural FSAs in Toronto, hence no postal codes should start with M0, however, the postal code M0R 8T0 is assigned to an
           <a href="/wiki/Amazon_(company)" title="Amazon (company)">
            Amazon (company)
           </a>
           warehouse in Mississauga, suggesting that Canada Post may be allocating the M0 FSA for high volume addresses.
          </p>
          <table class="wikitable sortable">
           <tbody>
            <tr>
             <th>
              Postcode
             </th>
             <th>
              Borough
             </th>
             <th>
              Neighbourhood
             </th>
            </tr>
            <tr>
             <td>
              M1A
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M2A
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3A
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Parkwoods" title="Parkwoods">
               Parkwoods
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4A
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Victoria_Village" title="Victoria Village">
               Victoria Village
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5A
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Regent_Park" title="Regent Park">
               Harbourfront
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6A
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Lawrence_Heights" title="Lawrence Heights">
               Lawrence Heights
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6A
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Lawrence_Manor" title="Lawrence Manor">
               Lawrence Manor
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M7A
             </td>
             <td>
              <a href="/wiki/Queen%27s_Park_(Toronto)" title="Queen's Park (Toronto)">
               Queen's Park
              </a>
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8A
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9A
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Queen%27s_Park_(Toronto)" title="Queen's Park (Toronto)">
               Queen's Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1B
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Rouge,_Toronto" title="Rouge, Toronto">
               Rouge
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1B
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Malvern,_Toronto" title="Malvern, Toronto">
               Malvern
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2B
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3B
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Don Mills North
             </td>
            </tr>
            <tr>
             <td>
              M4B
             </td>
             <td>
              <a href="/wiki/East_York" title="East York">
               East York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Woodbine_Gardens" title="Woodbine Gardens">
               Woodbine Gardens
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4B
             </td>
             <td>
              <a href="/wiki/East_York" title="East York">
               East York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Parkview_Hill" title="Parkview Hill">
               Parkview Hill
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5B
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Ryerson
             </td>
            </tr>
            <tr>
             <td>
              M5B
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Garden District
             </td>
            </tr>
            <tr>
             <td>
              M6B
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Glencairn
             </td>
            </tr>
            <tr>
             <td>
              M7B
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8B
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9B
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Cloverdale
             </td>
            </tr>
            <tr>
             <td>
              M9B
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Islington,_Toronto" title="Islington, Toronto">
               Islington
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9B
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Martin Grove
             </td>
            </tr>
            <tr>
             <td>
              M9B
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Princess_Gardens" title="Princess Gardens">
               Princess Gardens
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9B
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/West_Deane_Park" title="West Deane Park">
               West Deane Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1C
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Highland_Creek_(Toronto)" title="Highland Creek (Toronto)">
               Highland Creek
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1C
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Rouge_Hill" title="Rouge Hill">
               Rouge Hill
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1C
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Port_Union,_Toronto" title="Port Union, Toronto">
               Port Union
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2C
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3C
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Flemingdon_Park" title="Flemingdon Park">
               Flemingdon Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3C
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Don Mills South
             </td>
            </tr>
            <tr>
             <td>
              M4C
             </td>
             <td>
              <a href="/wiki/East_York" title="East York">
               East York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Woodbine_Heights" title="Woodbine Heights">
               Woodbine Heights
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5C
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/St._James_Town" title="St. James Town">
               St. James Town
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6C
             </td>
             <td>
              York
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Humewood-Cedarvale" title="Humewood-Cedarvale">
               Humewood-Cedarvale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M7C
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8C
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9C
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Bloordale Gardens
             </td>
            </tr>
            <tr>
             <td>
              M9C
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Eringate
             </td>
            </tr>
            <tr>
             <td>
              M9C
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Markland_Wood" title="Markland Wood">
               Markland Wood
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9C
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Old Burnhamthorpe
             </td>
            </tr>
            <tr>
             <td>
              M1E
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              Guildwood
             </td>
            </tr>
            <tr>
             <td>
              M1E
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Morningside,_Toronto" title="Morningside, Toronto">
               Morningside
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1E
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/West_Hill,_Toronto" title="West Hill, Toronto">
               West Hill
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2E
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3E
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4E
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/The_Beaches" title="The Beaches">
               The Beaches
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5E
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Berczy_Park" title="Berczy Park">
               Berczy Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6E
             </td>
             <td>
              York
             </td>
             <td>
              Caledonia-Fairbanks
             </td>
            </tr>
            <tr>
             <td>
              M7E
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8E
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9E
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1G
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Woburn,_Toronto" title="Woburn, Toronto">
               Woburn
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2G
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3G
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4G
             </td>
             <td>
              <a href="/wiki/East_York" title="East York">
               East York
              </a>
             </td>
             <td>
              <a href="/wiki/Leaside" title="Leaside">
               Leaside
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5G
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Central Bay Street
             </td>
            </tr>
            <tr>
             <td>
              M6G
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Christie
             </td>
            </tr>
            <tr>
             <td>
              M7G
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8G
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9G
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1H
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              Cedarbrae
             </td>
            </tr>
            <tr>
             <td>
              M2H
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Hillcrest_Village" title="Hillcrest Village">
               Hillcrest Village
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3H
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Bathurst_Manor" title="Bathurst Manor">
               Bathurst Manor
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3H
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Downsview North
             </td>
            </tr>
            <tr>
             <td>
              M3H
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Wilson_Heights,_Toronto" title="Wilson Heights, Toronto">
               Wilson Heights
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4H
             </td>
             <td>
              <a href="/wiki/East_York" title="East York">
               East York
              </a>
             </td>
             <td>
              <a href="/wiki/Thorncliffe_Park" title="Thorncliffe Park">
               Thorncliffe Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5H
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Adelaide
             </td>
            </tr>
            <tr>
             <td>
              M5H
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              King
             </td>
            </tr>
            <tr>
             <td>
              M5H
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Richmond
             </td>
            </tr>
            <tr>
             <td>
              M6H
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Dovercourt_Village" title="Dovercourt Village">
               Dovercourt Village
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6H
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              Dufferin
             </td>
            </tr>
            <tr>
             <td>
              M7H
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8H
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9H
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1J
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Scarborough_Village" title="Scarborough Village">
               Scarborough Village
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2J
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Fairview
             </td>
            </tr>
            <tr>
             <td>
              M2J
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Henry_Farm" title="Henry Farm">
               Henry Farm
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2J
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Oriole
             </td>
            </tr>
            <tr>
             <td>
              M3J
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Northwood_Park" title="Northwood Park">
               Northwood Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3J
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/York_University" title="York University">
               York University
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4J
             </td>
             <td>
              <a href="/wiki/East_York" title="East York">
               East York
              </a>
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5J
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Harbourfront East
             </td>
            </tr>
            <tr>
             <td>
              M5J
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Toronto_Islands" title="Toronto Islands">
               Toronto Islands
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5J
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Union_Station_(Toronto)" title="Union Station (Toronto)">
               Union Station
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6J
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Little_Portugal,_Toronto" title="Little Portugal, Toronto">
               Little Portugal
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6J
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Trinity%E2%80%93Bellwoods" title="Trinity–Bellwoods">
               Trinity
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M7J
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8J
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9J
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1K
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              East Birchmount Park
             </td>
            </tr>
            <tr>
             <td>
              M1K
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Ionview" title="Ionview">
               Ionview
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1K
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Kennedy_Park,_Toronto" title="Kennedy Park, Toronto">
               Kennedy Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2K
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Bayview_Village" title="Bayview Village">
               Bayview Village
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3K
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/CFB_Toronto" title="CFB Toronto">
               CFB Toronto
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3K
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Downsview East
             </td>
            </tr>
            <tr>
             <td>
              M4K
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
             <td>
              The Danforth West
             </td>
            </tr>
            <tr>
             <td>
              M4K
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Riverdale,_Toronto" title="Riverdale, Toronto">
               Riverdale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5K
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Design_Exchange" title="Design Exchange">
               Design Exchange
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5K
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Toronto_Dominion_Centre" title="Toronto Dominion Centre">
               Toronto Dominion Centre
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6K
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              Brockton
             </td>
            </tr>
            <tr>
             <td>
              M6K
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Exhibition_Place" title="Exhibition Place">
               Exhibition Place
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6K
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Parkdale_Village" title="Parkdale Village">
               Parkdale Village
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M7K
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8K
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9K
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1L
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Clairlea" title="Clairlea">
               Clairlea
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1L
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Golden_Mile,_Toronto" title="Golden Mile, Toronto">
               Golden Mile
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1L
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Oakridge,_Toronto" title="Oakridge, Toronto">
               Oakridge
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2L
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Silver Hills
             </td>
            </tr>
            <tr>
             <td>
              M2L
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/York_Mills" title="York Mills">
               York Mills
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3L
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Downsview" title="Downsview">
               Downsview West
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4L
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
             <td>
              The Beaches West
             </td>
            </tr>
            <tr>
             <td>
              M4L
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/India_Bazaar" title="India Bazaar">
               India Bazaar
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5L
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Commerce_Court" title="Commerce Court">
               Commerce Court
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5L
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Victoria Hotel
             </td>
            </tr>
            <tr>
             <td>
              M6L
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Downsview,_Toronto" title="Downsview, Toronto">
               Downsview
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6L
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              North Park
             </td>
            </tr>
            <tr>
             <td>
              M6L
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Upwood Park
             </td>
            </tr>
            <tr>
             <td>
              M7L
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8L
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9L
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Humber_Summit" title="Humber Summit">
               Humber Summit
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1M
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Cliffcrest" title="Cliffcrest">
               Cliffcrest
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1M
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Cliffside,_Toronto" title="Cliffside, Toronto">
               Cliffside
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1M
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              Scarborough Village West
             </td>
            </tr>
            <tr>
             <td>
              M2M
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Newtonbrook" title="Newtonbrook">
               Newtonbrook
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2M
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Willowdale,_Toronto" title="Willowdale, Toronto">
               Willowdale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3M
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Downsview Central
             </td>
            </tr>
            <tr>
             <td>
              M4M
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
             <td>
              Studio District
             </td>
            </tr>
            <tr>
             <td>
              M5M
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a href="/wiki/Bedford_Park,_Toronto" title="Bedford Park, Toronto">
               Bedford Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5M
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Lawrence Manor East
             </td>
            </tr>
            <tr>
             <td>
              M6M
             </td>
             <td>
              <a href="/wiki/York,_Toronto" title="York, Toronto">
               York
              </a>
             </td>
             <td>
              Del Ray
             </td>
            </tr>
            <tr>
             <td>
              M6M
             </td>
             <td>
              <a href="/wiki/York,_Toronto" title="York, Toronto">
               York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Keelesdale" title="Keelesdale">
               Keelesdale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6M
             </td>
             <td>
              <a href="/wiki/York,_Toronto" title="York, Toronto">
               York
              </a>
             </td>
             <td>
              <a href="/wiki/Mount_Dennis" title="Mount Dennis">
               Mount Dennis
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6M
             </td>
             <td>
              <a href="/wiki/York,_Toronto" title="York, Toronto">
               York
              </a>
             </td>
             <td>
              <a href="/wiki/Silverthorn,_Toronto" title="Silverthorn, Toronto">
               Silverthorn
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M7M
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8M
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9M
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Emery,_Toronto" title="Emery, Toronto">
               Emery
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9M
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Humberlea" title="Humberlea">
               Humberlea
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1N
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Birch_Cliff" title="Birch Cliff">
               Birch Cliff
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1N
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              Cliffside West
             </td>
            </tr>
            <tr>
             <td>
              M2N
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Willowdale South
             </td>
            </tr>
            <tr>
             <td>
              M3N
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              Downsview Northwest
             </td>
            </tr>
            <tr>
             <td>
              M4N
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Lawrence_Park,_Toronto" title="Lawrence Park, Toronto">
               Lawrence Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5N
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              Roselawn
             </td>
            </tr>
            <tr>
             <td>
              M6N
             </td>
             <td>
              <a href="/wiki/York,_Toronto" title="York, Toronto">
               York
              </a>
             </td>
             <td>
              The Junction North
             </td>
            </tr>
            <tr>
             <td>
              M6N
             </td>
             <td>
              <a href="/wiki/York,_Toronto" title="York, Toronto">
               York
              </a>
             </td>
             <td>
              Runnymede
             </td>
            </tr>
            <tr>
             <td>
              M7N
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8N
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9N
             </td>
             <td>
              <a href="/wiki/York,_Toronto" title="York, Toronto">
               York
              </a>
             </td>
             <td>
              <a href="/wiki/Weston,_Toronto" title="Weston, Toronto">
               Weston
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1P
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Dorset_Park" title="Dorset Park">
               Dorset Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1P
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Scarborough_Town_Centre" title="Scarborough Town Centre">
               Scarborough Town Centre
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1P
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Wexford_Heights" title="Wexford Heights">
               Wexford Heights
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2P
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              York Mills West
             </td>
            </tr>
            <tr>
             <td>
              M3P
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4P
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              Davisville North
             </td>
            </tr>
            <tr>
             <td>
              M5P
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Forest_Hill_North" title="Forest Hill North">
               Forest Hill North
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5P
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              Forest Hill West
             </td>
            </tr>
            <tr>
             <td>
              M6P
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/High_Park" title="High Park">
               High Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6P
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              The Junction South
             </td>
            </tr>
            <tr>
             <td>
              M7P
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8P
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9P
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Westmount
             </td>
            </tr>
            <tr>
             <td>
              M1R
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Maryvale,_Toronto" title="Maryvale, Toronto">
               Maryvale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1R
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Wexford,_Toronto" title="Wexford, Toronto">
               Wexford
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2R
             </td>
             <td>
              <a href="/wiki/North_York" title="North York">
               North York
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Willowdale_West" title="Willowdale West">
               Willowdale West
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M3R
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4R
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              North Toronto West
             </td>
            </tr>
            <tr>
             <td>
              M5R
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/The_Annex" title="The Annex">
               The Annex
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5R
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              North Midtown
             </td>
            </tr>
            <tr>
             <td>
              M5R
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Yorkville,_Toronto" title="Yorkville, Toronto">
               Yorkville
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6R
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Parkdale,_Toronto" title="Parkdale, Toronto">
               Parkdale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6R
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Roncesvalles,_Toronto" title="Roncesvalles, Toronto">
               Roncesvalles
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M7R
             </td>
             <td>
              Mississauga
             </td>
             <td>
              Canada Post Gateway Processing Centre
             </td>
            </tr>
            <tr>
             <td>
              M8R
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9R
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Kingsview_Village" title="Kingsview Village">
               Kingsview Village
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9R
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Martin Grove Gardens
             </td>
            </tr>
            <tr>
             <td>
              M9R
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Richview Gardens
             </td>
            </tr>
            <tr>
             <td>
              M9R
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              St. Phillips
             </td>
            </tr>
            <tr>
             <td>
              M1S
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Agincourt,_Toronto" title="Agincourt, Toronto">
               Agincourt
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2S
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3S
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4S
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              Davisville
             </td>
            </tr>
            <tr>
             <td>
              M5S
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Harbord
             </td>
            </tr>
            <tr>
             <td>
              M5S
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/University_of_Toronto" title="University of Toronto">
               University of Toronto
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6S
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Runnymede,_Toronto" title="Runnymede, Toronto">
               Runnymede
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6S
             </td>
             <td>
              <a href="/wiki/West_Toronto" title="West Toronto">
               West Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Swansea,_Toronto" title="Swansea, Toronto">
               Swansea
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M7S
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8S
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9S
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1T
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              Clarks Corners
             </td>
            </tr>
            <tr>
             <td>
              M1T
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              Sullivan
             </td>
            </tr>
            <tr>
             <td>
              M1T
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Tam_O%27Shanter_%E2%80%93_Sullivan" title="Tam O'Shanter – Sullivan">
               Tam O'Shanter
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2T
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3T
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4T
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Moore_Park,_Toronto" title="Moore Park, Toronto">
               Moore Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4T
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              Summerhill East
             </td>
            </tr>
            <tr>
             <td>
              M5T
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Chinatown,_Toronto" title="Chinatown, Toronto">
               Chinatown
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5T
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Grange_Park_(Toronto)" title="Grange Park (Toronto)">
               Grange Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5T
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Kensington_Market" title="Kensington Market">
               Kensington Market
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6T
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M7T
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8T
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M9T
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1V
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Agincourt_North" title="Agincourt North">
               Agincourt North
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1V
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              L'Amoreaux East
             </td>
            </tr>
            <tr>
             <td>
              M1V
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a href="/wiki/Milliken,_Ontario" title="Milliken, Ontario">
               Milliken
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1V
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              Steeles East
             </td>
            </tr>
            <tr>
             <td>
              M2V
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3V
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4V
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Deer_Park,_Toronto" title="Deer Park, Toronto">
               Deer Park
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4V
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              Forest Hill SE
             </td>
            </tr>
            <tr>
             <td>
              M4V
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Rathnelly" title="Rathnelly">
               Rathnelly
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4V
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/South_Hill,_Toronto" title="South Hill, Toronto">
               South Hill
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4V
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">
               Central Toronto
              </a>
             </td>
             <td>
              Summerhill West
             </td>
            </tr>
            <tr>
             <td>
              M5V
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/CN_Tower" title="CN Tower">
               CN Tower
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5V
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Bathurst Quay
             </td>
            </tr>
            <tr>
             <td>
              M5V
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Island airport
             </td>
            </tr>
            <tr>
             <td>
              M5V
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Harbourfront West
             </td>
            </tr>
            <tr>
             <td>
              M5V
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/King_and_Spadina" title="King and Spadina">
               King and Spadina
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5V
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Railway_Lands" title="Railway Lands">
               Railway Lands
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5V
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/South_Niagara" title="South Niagara">
               South Niagara
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6V
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M7V
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Humber Bay Shores
             </td>
            </tr>
            <tr>
             <td>
              M8V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Mimico South
             </td>
            </tr>
            <tr>
             <td>
              M8V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/New_Toronto" title="New Toronto">
               New Toronto
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Albion Gardens
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Beaumond_Heights" title="Beaumond Heights">
               Beaumond Heights
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Humbergate
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Mount_Olive-Silverstone-Jamestown" title="Mount Olive-Silverstone-Jamestown">
               Jamestown
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Mount_Olive-Silverstone-Jamestown" title="Mount Olive-Silverstone-Jamestown">
               Mount Olive
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Silverstone,_Toronto" title="Silverstone, Toronto">
               Silverstone
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/South_Steeles" title="South Steeles">
               South Steeles
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9V
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Thistletown" title="Thistletown">
               Thistletown
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M1W
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              L'Amoreaux West
             </td>
            </tr>
            <tr>
             <td>
              M2W
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3W
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4W
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Rosedale,_Toronto" title="Rosedale, Toronto">
               Rosedale
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5W
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              Stn A PO Boxes 25 The Esplanade
             </td>
            </tr>
            <tr>
             <td>
              M6W
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M7W
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8W
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Alderwood,_Toronto" title="Alderwood, Toronto">
               Alderwood
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8W
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Long_Branch,_Toronto" title="Long Branch, Toronto">
               Long Branch
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9W
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Northwest
             </td>
            </tr>
            <tr>
             <td>
              M1X
             </td>
             <td>
              <a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">
               Scarborough
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Upper_Rouge" title="Upper Rouge">
               Upper Rouge
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M2X
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3X
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4X
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Cabbagetown,_Toronto" title="Cabbagetown, Toronto">
               Cabbagetown
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M4X
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/St._James_Town" title="St. James Town">
               St. James Town
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5X
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/First_Canadian_Place" title="First Canadian Place">
               First Canadian Place
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5X
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Underground_city" title="Underground city">
               Underground city
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M6X
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M7X
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8X
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/The_Kingsway" title="The Kingsway">
               The Kingsway
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8X
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Montgomery Road
             </td>
            </tr>
            <tr>
             <td>
              M8X
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Old Mill North
             </td>
            </tr>
            <tr>
             <td>
              M9X
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1Y
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M2Y
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3Y
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4Y
             </td>
             <td>
              <a href="/wiki/Downtown_Toronto" title="Downtown Toronto">
               Downtown Toronto
              </a>
             </td>
             <td>
              <a href="/wiki/Church_and_Wellesley" title="Church and Wellesley">
               Church and Wellesley
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M5Y
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M6Y
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M7Y
             </td>
             <td>
              <a href="/wiki/East_Toronto" title="East Toronto">
               East Toronto
              </a>
             </td>
             <td>
              Business Reply Mail Processing Centre 969 Eastern
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Humber_Bay" title="Humber Bay">
               Humber Bay
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              King's Mill Park
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Kingsway Park South East
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Mimico" title="Mimico">
               Mimico NE
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Old_Mill,_Toronto" title="Old Mill, Toronto">
               Old Mill South
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/The_Queensway" title="The Queensway">
               The Queensway East
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Fairmont_Royal_York_Hotel" title="Fairmont Royal York Hotel">
               Royal York South East
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8Y
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a class="mw-redirect" href="/wiki/Sunnylea" title="Sunnylea">
               Sunnylea
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M9Y
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M1Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M2Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M3Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M4Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M5Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M6Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M7Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
            <tr>
             <td>
              M8Z
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Kingsway Park South West
             </td>
            </tr>
            <tr>
             <td>
              M8Z
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/Mimico" title="Mimico">
               Mimico NW
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8Z
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              <a href="/wiki/The_Queensway" title="The Queensway">
               The Queensway West
              </a>
             </td>
            </tr>
            <tr>
             <td>
              M8Z
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              Royal York South West
             </td>
            </tr>
            <tr>
             <td>
              M8Z
             </td>
             <td>
              <a href="/wiki/Etobicoke" title="Etobicoke">
               Etobicoke
              </a>
             </td>
             <td>
              South of Bloor
             </td>
            </tr>
            <tr>
             <td>
              M9Z
             </td>
             <td>
              Not assigned
             </td>
             <td>
              Not assigned
             </td>
            </tr>
           </tbody>
          </table>
          <div>
           <table class="multicol" role="presentation" style="border-collapse: collapse; padding: 0; border: 0; background:transparent; width:100%;">
           </table>
           <h2>
            <span id="Most_populated_FSAs.5B3.5D">
            </span>
            <span class="mw-headline" id="Most_populated_FSAs[3]">
             Most populated FSAs
             <sup class="reference" id="cite_ref-statcan_3-0">
              <a href="#cite_note-statcan-3">
               [3]
              </a>
             </sup>
            </span>
            <span class="mw-editsection">
             <span class="mw-editsection-bracket">
              [
             </span>
             <a href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=edit&amp;section=2" title="Edit section: Most populated FSAs[3]">
              edit
             </a>
             <span class="mw-editsection-bracket">
              ]
             </span>
            </span>
           </h2>
           <ol>
            <li>
             M1B, 65,129
            </li>
            <li>
             M2N, 60,124
            </li>
            <li>
             M1V, 55,250
            </li>
            <li>
             M9V, 55,159
            </li>
            <li>
             M2J, 54,391
            </li>
           </ol>
           <p>
           </p>
           <table cellpadding="2" cellspacing="0" rules="all" style="width:100%; border-collapse:collapse; border:1px solid #ccc;">
            <tbody>
             <tr>
              <td>
              </td>
             </tr>
            </tbody>
           </table>
          </div>
          <p>
          </p>
          <h2>
           <span id="Least_populated_FSAs.5B3.5D">
           </span>
           <span class="mw-headline" id="Least_populated_FSAs[3]">
            Least populated FSAs
            <sup class="reference" id="cite_ref-statcan_3-1">
             <a href="#cite_note-statcan-3">
              [3]
             </a>
            </sup>
           </span>
           <span class="mw-editsection">
            <span class="mw-editsection-bracket">
             [
            </span>
            <a href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=edit&amp;section=3" title="Edit section: Least populated FSAs[3]">
             edit
            </a>
            <span class="mw-editsection-bracket">
             ]
            </span>
           </span>
          </h2>
          <ol>
           <li>
            M5K, 5
           </li>
           <li>
            M5L, 5
           </li>
           <li>
            M5W, 5
           </li>
           <li>
            M5X, 5
           </li>
           <li>
            M7A, 5
           </li>
          </ol>
          <p>
          </p>
          <h2>
           <span class="mw-headline" id="References">
            References
           </span>
           <span class="mw-editsection">
            <span class="mw-editsection-bracket">
             [
            </span>
            <a href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=edit&amp;section=4" title="Edit section: References">
             edit
            </a>
            <span class="mw-editsection-bracket">
             ]
            </span>
           </span>
          </h2>
          <div class="mw-references-wrap">
           <ol class="references">
            <li id="cite_note-1">
             <span class="mw-cite-backlink">
              <b>
               <a href="#cite_ref-1">
                ^
               </a>
              </b>
             </span>
             <span class="reference-text">
              <cite class="citation web">
               Canada Post.
               <a class="external text" href="https://www.canadapost.ca/cpotools/apps/fpc/personal/findByCity?execution=e2s1" rel="nofollow">
                "Canada Post - Find a Postal Code"
               </a>
               <span class="reference-accessdate">
                . Retrieved
                <span class="nowrap">
                 9 November
                </span>
                2008
               </span>
               .
              </cite>
              <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook&amp;rft.genre=unknown&amp;rft.btitle=Canada+Post+-+Find+a+Postal+Code&amp;rft.au=Canada+Post&amp;rft_id=https%3A%2F%2Fwww.canadapost.ca%2Fcpotools%2Fapps%2Ffpc%2Fpersonal%2FfindByCity%3Fexecution%3De2s1&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3AList+of+postal+codes+of+Canada%3A+M">
              </span>
              <style data-mw-deduplicate="TemplateStyles:r886058088">
               .mw-parser-output cite.citation{font-style:inherit}.mw-parser-output .citation q{quotes:"\"""\"""'""'"}.mw-parser-output .citation .cs1-lock-free a{background:url("//upload.wikimedia.org/wikipedia/commons/thumb/6/65/Lock-green.svg/9px-Lock-green.svg.png")no-repeat;background-position:right .1em center}.mw-parser-output .citation .cs1-lock-limited a,.mw-parser-output .citation .cs1-lock-registration a{background:url("//upload.wikimedia.org/wikipedia/commons/thumb/d/d6/Lock-gray-alt-2.svg/9px-Lock-gray-alt-2.svg.png")no-repeat;background-position:right .1em center}.mw-parser-output .citation .cs1-lock-subscription a{background:url("//upload.wikimedia.org/wikipedia/commons/thumb/a/aa/Lock-red-alt-2.svg/9px-Lock-red-alt-2.svg.png")no-repeat;background-position:right .1em center}.mw-parser-output .cs1-subscription,.mw-parser-output .cs1-registration{color:#555}.mw-parser-output .cs1-subscription span,.mw-parser-output .cs1-registration span{border-bottom:1px dotted;cursor:help}.mw-parser-output .cs1-ws-icon a{background:url("//upload.wikimedia.org/wikipedia/commons/thumb/4/4c/Wikisource-logo.svg/12px-Wikisource-logo.svg.png")no-repeat;background-position:right .1em center}.mw-parser-output code.cs1-code{color:inherit;background:inherit;border:inherit;padding:inherit}.mw-parser-output .cs1-hidden-error{display:none;font-size:100%}.mw-parser-output .cs1-visible-error{font-size:100%}.mw-parser-output .cs1-maint{display:none;color:#33aa33;margin-left:0.3em}.mw-parser-output .cs1-subscription,.mw-parser-output .cs1-registration,.mw-parser-output .cs1-format{font-size:95%}.mw-parser-output .cs1-kern-left,.mw-parser-output .cs1-kern-wl-left{padding-left:0.2em}.mw-parser-output .cs1-kern-right,.mw-parser-output .cs1-kern-wl-right{padding-right:0.2em}
              </style>
             </span>
            </li>
            <li id="cite_note-2">
             <span class="mw-cite-backlink">
              <b>
               <a href="#cite_ref-2">
                ^
               </a>
              </b>
             </span>
             <span class="reference-text">
              <cite class="citation web">
               <a class="external text" href="https://web.archive.org/web/20110519093024/http://www.canadapost.ca/cpo/mc/personal/tools/mobileapp/default.jsf" rel="nofollow">
                "Mobile Apps"
               </a>
               . Canada Post. Archived from
               <a class="external text" href="http://www.canadapost.ca/cpo/mc/personal/tools/mobileapp/default.jsf" rel="nofollow">
                the original
               </a>
               on 2011-05-19.
              </cite>
              <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook&amp;rft.genre=unknown&amp;rft.btitle=Mobile+Apps&amp;rft.pub=Canada+Post&amp;rft_id=http%3A%2F%2Fwww.canadapost.ca%2Fcpo%2Fmc%2Fpersonal%2Ftools%2Fmobileapp%2Fdefault.jsf&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3AList+of+postal+codes+of+Canada%3A+M">
              </span>
              <link href="mw-data:TemplateStyles:r886058088" rel="mw-deduplicated-inline-style"/>
             </span>
            </li>
            <li id="cite_note-statcan-3">
             <span class="mw-cite-backlink">
              ^
              <a href="#cite_ref-statcan_3-0">
               <sup>
                <i>
                 <b>
                  a
                 </b>
                </i>
               </sup>
              </a>
              <a href="#cite_ref-statcan_3-1">
               <sup>
                <i>
                 <b>
                  b
                 </b>
                </i>
               </sup>
              </a>
             </span>
             <span class="reference-text">
              <cite class="citation web">
               <a class="external text" href="http://www12.statcan.ca/english/census06/data/popdwell/Table.cfm?T=1201&amp;SR=1&amp;S=0&amp;O=A&amp;RPP=9999&amp;PR=0&amp;CMA=0" rel="nofollow">
                "2006 Census of Population"
               </a>
               . 15 October 2008.
              </cite>
              <span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Abook&amp;rft.genre=unknown&amp;rft.btitle=2006+Census+of+Population&amp;rft.date=2008-10-15&amp;rft_id=http%3A%2F%2Fwww12.statcan.ca%2Fenglish%2Fcensus06%2Fdata%2Fpopdwell%2FTable.cfm%3FT%3D1201%26SR%3D1%26S%3D0%26O%3DA%26RPP%3D9999%26PR%3D0%26CMA%3D0&amp;rfr_id=info%3Asid%2Fen.wikipedia.org%3AList+of+postal+codes+of+Canada%3A+M">
              </span>
              <link href="mw-data:TemplateStyles:r886058088" rel="mw-deduplicated-inline-style"/>
             </span>
            </li>
           </ol>
          </div>
          <table class="navbox">
           <tbody>
            <tr>
             <td style="width:36px; text-align:center">
              <a class="image" href="/wiki/File:Flag_of_Canada.svg" title="Flag of Canada">
               <img alt="Flag of Canada" data-file-height="600" data-file-width="1200" decoding="async" height="18" src="//upload.wikimedia.org/wikipedia/en/thumb/c/cf/Flag_of_Canada.svg/36px-Flag_of_Canada.svg.png" srcset="//upload.wikimedia.org/wikipedia/en/thumb/c/cf/Flag_of_Canada.svg/54px-Flag_of_Canada.svg.png 1.5x, //upload.wikimedia.org/wikipedia/en/thumb/c/cf/Flag_of_Canada.svg/72px-Flag_of_Canada.svg.png 2x" width="36"/>
              </a>
             </td>
             <th class="navbox-title" style="font-size:110%">
              <a href="/wiki/Postal_codes_in_Canada" title="Postal codes in Canada">
               Canadian postal codes
              </a>
             </th>
             <td style="width:36px; text-align:center">
              <a class="image" href="/wiki/File:Canadian_postal_district_map_(without_legends).svg">
               <img alt="Canadian postal district map (without legends).svg" data-file-height="846" data-file-width="1000" decoding="async" height="18" src="//upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Canadian_postal_district_map_%28without_legends%29.svg/21px-Canadian_postal_district_map_%28without_legends%29.svg.png" srcset="//upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Canadian_postal_district_map_%28without_legends%29.svg/32px-Canadian_postal_district_map_%28without_legends%29.svg.png 1.5x, //upload.wikimedia.org/wikipedia/commons/thumb/e/eb/Canadian_postal_district_map_%28without_legends%29.svg/43px-Canadian_postal_district_map_%28without_legends%29.svg.png 2x" width="21"/>
              </a>
             </td>
            </tr>
            <tr>
             <td colspan="3" style="text-align:center; font-size: 100%;">
              <table cellspacing="0" style="background-color: #F8F8F8;" width="100%">
               <tbody>
                <tr>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Newfoundland_and_Labrador" title="Newfoundland and Labrador">
                   NL
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Nova_Scotia" title="Nova Scotia">
                   NS
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Prince_Edward_Island" title="Prince Edward Island">
                   PE
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/New_Brunswick" title="New Brunswick">
                   NB
                  </a>
                 </td>
                 <td colspan="3" style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Quebec" title="Quebec">
                   QC
                  </a>
                 </td>
                 <td colspan="5" style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Ontario" title="Ontario">
                   ON
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Manitoba" title="Manitoba">
                   MB
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Saskatchewan" title="Saskatchewan">
                   SK
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Alberta" title="Alberta">
                   AB
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/British_Columbia" title="British Columbia">
                   BC
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Nunavut" title="Nunavut">
                   NU
                  </a>
                  /
                  <a href="/wiki/Northwest_Territories" title="Northwest Territories">
                   NT
                  </a>
                 </td>
                 <td style="text-align:center; border:1px solid #aaa;">
                  <a href="/wiki/Yukon" title="Yukon">
                   YT
                  </a>
                 </td>
                </tr>
                <tr>
                 <td align="center" style="border: 1px solid #FF0000; background-color: #FFE0E0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_A" title="List of postal codes of Canada: A">
                   A
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #FF4000; background-color: #FFE8E0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_B" title="List of postal codes of Canada: B">
                   B
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #FF8000; background-color: #FFF0E0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_C" title="List of postal codes of Canada: C">
                   C
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #FFC000; background-color: #FFF8E0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_E" title="List of postal codes of Canada: E">
                   E
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #FFFF00; background-color: #FFFFE0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_G" title="List of postal codes of Canada: G">
                   G
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #C0FF00; background-color: #F8FFE0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_H" title="List of postal codes of Canada: H">
                   H
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #80FF00; background-color: #F0FFE0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_J" title="List of postal codes of Canada: J">
                   J
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #00FF00; background-color: #E0FFE0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_K" title="List of postal codes of Canada: K">
                   K
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #00FF80; background-color: #E0FFF0; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_L" title="List of postal codes of Canada: L">
                   L
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #E0FFF8; background-color: #00FFC0; font-size: 135%; color: black;" width="5%">
                  <a class="mw-selflink selflink">
                   M
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #00FFE0; background-color: #E0FFFC; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_N" title="List of postal codes of Canada: N">
                   N
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #00FFFF; background-color: #E0FFFF; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_P" title="List of postal codes of Canada: P">
                   P
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #00C0FF; background-color: #E0F8FF; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_R" title="List of postal codes of Canada: R">
                   R
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #0080FF; background-color: #E0F0FF; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_S" title="List of postal codes of Canada: S">
                   S
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #0040FF; background-color: #E0E8FF; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_T" title="List of postal codes of Canada: T">
                   T
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #0000FF; background-color: #E0E0FF; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_V" title="List of postal codes of Canada: V">
                   V
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #A000FF; background-color: #E8E0FF; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_X" title="List of postal codes of Canada: X">
                   X
                  </a>
                 </td>
                 <td align="center" style="border: 1px solid #FF00FF; background-color: #FFE0FF; font-size: 135%;" width="5%">
                  <a href="/wiki/List_of_postal_codes_of_Canada:_Y" title="List of postal codes of Canada: Y">
                   Y
                  </a>
                 </td>
                </tr>
               </tbody>
              </table>
             </td>
            </tr>
           </tbody>
          </table>
          <!-- 
    NewPP limit report
    Parsed by mw1312
    Cached time: 20191206171103
    Cache expiry: 2592000
    Dynamic content: false
    Complications: [vary‐revision‐sha1]
    CPU time usage: 0.284 seconds
    Real time usage: 0.353 seconds
    Preprocessor visited node count: 572/1000000
    Preprocessor generated node count: 0/1500000
    Post‐expand include size: 10232/2097152 bytes
    Template argument size: 13/2097152 bytes
    Highest expansion depth: 5/40
    Expensive parser function count: 0/500
    Unstrip recursion depth: 1/20
    Unstrip post‐expand size: 9025/5000000 bytes
    Number of Wikibase entities loaded: 0/400
    Lua time usage: 0.101/10.000 seconds
    Lua memory usage: 1.75 MB/50 MB
    -->
          <!--
    Transclusion expansion time report (%,ms,calls,template)
    100.00%  206.762      1 -total
     73.26%  151.466      3 Template:Cite_web
      4.62%    9.552      1 Template:Canadian_postal_codes
      3.87%    8.009      1 Template:Col-2
      2.82%    5.822      1 Template:Col-begin
      1.93%    3.982      2 Template:Col-end
      1.53%    3.156      1 Template:Col-break
    -->
          <!-- Saved in parser cache with key enwiki:pcache:idhash:539066-0!canonical and timestamp 20191206171117 and revision id 929562264
     -->
         </div>
         <noscript>
          <img alt="" height="1" src="//en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type=1x1" style="border: none; position: absolute;" title="" width="1"/>
         </noscript>
        </div>
        <div class="printfooter">
         Retrieved from "
         <a dir="ltr" href="https://en.wikipedia.org/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;oldid=929562264">
          https://en.wikipedia.org/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;oldid=929562264
         </a>
         "
        </div>
        <div class="catlinks" data-mw="interface" id="catlinks">
         <div class="mw-normal-catlinks" id="mw-normal-catlinks">
          <a href="/wiki/Help:Category" title="Help:Category">
           Categories
          </a>
          :
          <ul>
           <li>
            <a href="/wiki/Category:Communications_in_Ontario" title="Category:Communications in Ontario">
             Communications in Ontario
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Postal_codes_in_Canada" title="Category:Postal codes in Canada">
             Postal codes in Canada
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Toronto" title="Category:Toronto">
             Toronto
            </a>
           </li>
           <li>
            <a href="/wiki/Category:Ontario-related_lists" title="Category:Ontario-related lists">
             Ontario-related lists
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div class="visualClear">
        </div>
       </div>
      </div>
      <div id="mw-data-after-content">
       <div class="read-more-container">
       </div>
      </div>
      <div id="mw-navigation">
       <h2>
        Navigation menu
       </h2>
       <div id="mw-head">
        <div aria-labelledby="p-personal-label" id="p-personal" role="navigation">
         <h3 id="p-personal-label">
          Personal tools
         </h3>
         <ul>
          <li id="pt-anonuserpage">
           Not logged in
          </li>
          <li id="pt-anontalk">
           <a accesskey="n" href="/wiki/Special:MyTalk" title="Discussion about edits from this IP address [n]">
            Talk
           </a>
          </li>
          <li id="pt-anoncontribs">
           <a accesskey="y" href="/wiki/Special:MyContributions" title="A list of edits made from this IP address [y]">
            Contributions
           </a>
          </li>
          <li id="pt-createaccount">
           <a href="/w/index.php?title=Special:CreateAccount&amp;returnto=List+of+postal+codes+of+Canada%3A+M" title="You are encouraged to create an account and log in; however, it is not mandatory">
            Create account
           </a>
          </li>
          <li id="pt-login">
           <a accesskey="o" href="/w/index.php?title=Special:UserLogin&amp;returnto=List+of+postal+codes+of+Canada%3A+M" title="You're encouraged to log in; however, it's not mandatory. [o]">
            Log in
           </a>
          </li>
         </ul>
        </div>
        <div id="left-navigation">
         <div aria-labelledby="p-namespaces-label" class="vectorTabs" id="p-namespaces" role="navigation">
          <h3 id="p-namespaces-label">
           Namespaces
          </h3>
          <ul>
           <li class="selected" id="ca-nstab-main">
            <a accesskey="c" href="/wiki/List_of_postal_codes_of_Canada:_M" title="View the content page [c]">
             Article
            </a>
           </li>
           <li id="ca-talk">
            <a accesskey="t" href="/wiki/Talk:List_of_postal_codes_of_Canada:_M" rel="discussion" title="Discussion about the content page [t]">
             Talk
            </a>
           </li>
          </ul>
         </div>
         <div aria-labelledby="p-variants-label" class="vectorMenu emptyPortlet" id="p-variants" role="navigation">
          <input aria-labelledby="p-variants-label" class="vectorMenuCheckbox" type="checkbox"/>
          <h3 id="p-variants-label">
           <span>
            Variants
           </span>
          </h3>
          <ul class="menu">
          </ul>
         </div>
        </div>
        <div id="right-navigation">
         <div aria-labelledby="p-views-label" class="vectorTabs" id="p-views" role="navigation">
          <h3 id="p-views-label">
           Views
          </h3>
          <ul>
           <li class="collapsible selected" id="ca-view">
            <a href="/wiki/List_of_postal_codes_of_Canada:_M">
             Read
            </a>
           </li>
           <li class="collapsible" id="ca-edit">
            <a accesskey="e" href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=edit" title="Edit this page [e]">
             Edit
            </a>
           </li>
           <li class="collapsible" id="ca-history">
            <a accesskey="h" href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=history" title="Past revisions of this page [h]">
             View history
            </a>
           </li>
          </ul>
         </div>
         <div aria-labelledby="p-cactions-label" class="vectorMenu emptyPortlet" id="p-cactions" role="navigation">
          <input aria-labelledby="p-cactions-label" class="vectorMenuCheckbox" type="checkbox"/>
          <h3 id="p-cactions-label">
           <span>
            More
           </span>
          </h3>
          <ul class="menu">
          </ul>
         </div>
         <div id="p-search" role="search">
          <h3>
           <label for="searchInput">
            Search
           </label>
          </h3>
          <form action="/w/index.php" id="searchform">
           <div id="simpleSearch">
            <input accesskey="f" id="searchInput" name="search" placeholder="Search Wikipedia" title="Search Wikipedia [f]" type="search"/>
            <input name="title" type="hidden" value="Special:Search"/>
            <input class="searchButton mw-fallbackSearchButton" id="mw-searchButton" name="fulltext" title="Search Wikipedia for this text" type="submit" value="Search"/>
            <input class="searchButton" id="searchButton" name="go" title="Go to a page with this exact name if it exists" type="submit" value="Go"/>
           </div>
          </form>
         </div>
        </div>
       </div>
       <div id="mw-panel">
        <div id="p-logo" role="banner">
         <a class="mw-wiki-logo" href="/wiki/Main_Page" title="Visit the main page">
         </a>
        </div>
        <div aria-labelledby="p-navigation-label" class="portal" id="p-navigation" role="navigation">
         <h3 id="p-navigation-label">
          Navigation
         </h3>
         <div class="body">
          <ul>
           <li id="n-mainpage-description">
            <a accesskey="z" href="/wiki/Main_Page" title="Visit the main page [z]">
             Main page
            </a>
           </li>
           <li id="n-contents">
            <a href="/wiki/Wikipedia:Contents" title="Guides to browsing Wikipedia">
             Contents
            </a>
           </li>
           <li id="n-featuredcontent">
            <a href="/wiki/Portal:Featured_content" title="Featured content – the best of Wikipedia">
             Featured content
            </a>
           </li>
           <li id="n-currentevents">
            <a href="/wiki/Portal:Current_events" title="Find background information on current events">
             Current events
            </a>
           </li>
           <li id="n-randompage">
            <a accesskey="x" href="/wiki/Special:Random" title="Load a random article [x]">
             Random article
            </a>
           </li>
           <li id="n-sitesupport">
            <a href="https://donate.wikimedia.org/wiki/Special:FundraiserRedirector?utm_source=donate&amp;utm_medium=sidebar&amp;utm_campaign=C13_en.wikipedia.org&amp;uselang=en" title="Support us">
             Donate to Wikipedia
            </a>
           </li>
           <li id="n-shoplink">
            <a href="//shop.wikimedia.org" title="Visit the Wikipedia store">
             Wikipedia store
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-interaction-label" class="portal" id="p-interaction" role="navigation">
         <h3 id="p-interaction-label">
          Interaction
         </h3>
         <div class="body">
          <ul>
           <li id="n-help">
            <a href="/wiki/Help:Contents" title="Guidance on how to use and edit Wikipedia">
             Help
            </a>
           </li>
           <li id="n-aboutsite">
            <a href="/wiki/Wikipedia:About" title="Find out about Wikipedia">
             About Wikipedia
            </a>
           </li>
           <li id="n-portal">
            <a href="/wiki/Wikipedia:Community_portal" title="About the project, what you can do, where to find things">
             Community portal
            </a>
           </li>
           <li id="n-recentchanges">
            <a accesskey="r" href="/wiki/Special:RecentChanges" title="A list of recent changes in the wiki [r]">
             Recent changes
            </a>
           </li>
           <li id="n-contactpage">
            <a href="//en.wikipedia.org/wiki/Wikipedia:Contact_us" title="How to contact Wikipedia">
             Contact page
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-tb-label" class="portal" id="p-tb" role="navigation">
         <h3 id="p-tb-label">
          Tools
         </h3>
         <div class="body">
          <ul>
           <li id="t-whatlinkshere">
            <a accesskey="j" href="/wiki/Special:WhatLinksHere/List_of_postal_codes_of_Canada:_M" title="List of all English Wikipedia pages containing links to this page [j]">
             What links here
            </a>
           </li>
           <li id="t-recentchangeslinked">
            <a accesskey="k" href="/wiki/Special:RecentChangesLinked/List_of_postal_codes_of_Canada:_M" rel="nofollow" title="Recent changes in pages linked from this page [k]">
             Related changes
            </a>
           </li>
           <li id="t-upload">
            <a accesskey="u" href="/wiki/Wikipedia:File_Upload_Wizard" title="Upload files [u]">
             Upload file
            </a>
           </li>
           <li id="t-specialpages">
            <a accesskey="q" href="/wiki/Special:SpecialPages" title="A list of all special pages [q]">
             Special pages
            </a>
           </li>
           <li id="t-permalink">
            <a href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;oldid=929562264" title="Permanent link to this revision of the page">
             Permanent link
            </a>
           </li>
           <li id="t-info">
            <a href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;action=info" title="More information about this page">
             Page information
            </a>
           </li>
           <li id="t-wikibase">
            <a accesskey="g" href="https://www.wikidata.org/wiki/Special:EntityPage/Q3248240" title="Link to connected data repository item [g]">
             Wikidata item
            </a>
           </li>
           <li id="t-cite">
            <a href="/w/index.php?title=Special:CiteThisPage&amp;page=List_of_postal_codes_of_Canada%3A_M&amp;id=929562264" title="Information on how to cite this page">
             Cite this page
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-coll-print_export-label" class="portal" id="p-coll-print_export" role="navigation">
         <h3 id="p-coll-print_export-label">
          Print/export
         </h3>
         <div class="body">
          <ul>
           <li id="coll-create_a_book">
            <a href="/w/index.php?title=Special:Book&amp;bookcmd=book_creator&amp;referer=List+of+postal+codes+of+Canada%3A+M">
             Create a book
            </a>
           </li>
           <li id="coll-download-as-rl">
            <a href="/w/index.php?title=Special:ElectronPdf&amp;page=List+of+postal+codes+of+Canada%3A+M&amp;action=show-download-screen">
             Download as PDF
            </a>
           </li>
           <li id="t-print">
            <a accesskey="p" href="/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;printable=yes" title="Printable version of this page [p]">
             Printable version
            </a>
           </li>
          </ul>
         </div>
        </div>
        <div aria-labelledby="p-lang-label" class="portal" id="p-lang" role="navigation">
         <h3 id="p-lang-label">
          Languages
         </h3>
         <div class="body">
          <ul>
           <li class="interlanguage-link interwiki-fr">
            <a class="interlanguage-link-target" href="https://fr.wikipedia.org/wiki/Liste_des_codes_postaux_canadiens_d%C3%A9butant_par_M" hreflang="fr" lang="fr" title="Liste des codes postaux canadiens débutant par M – French">
             Français
            </a>
           </li>
          </ul>
          <div class="after-portlet after-portlet-lang">
           <span class="wb-langlinks-edit wb-langlinks-link">
            <a class="wbc-editpage" href="https://www.wikidata.org/wiki/Special:EntityPage/Q3248240#sitelinks-wikipedia" title="Edit interlanguage links">
             Edit links
            </a>
           </span>
          </div>
         </div>
        </div>
       </div>
      </div>
      <div id="footer" role="contentinfo">
       <ul id="footer-info">
        <li id="footer-info-lastmod">
         This page was last edited on 6 December 2019, at 17:11
         <span class="anonymous-show">
          (UTC)
         </span>
         .
        </li>
        <li id="footer-info-copyright">
         Text is available under the
         <a href="//en.wikipedia.org/wiki/Wikipedia:Text_of_Creative_Commons_Attribution-ShareAlike_3.0_Unported_License" rel="license">
          Creative Commons Attribution-ShareAlike License
         </a>
         <a href="//creativecommons.org/licenses/by-sa/3.0/" rel="license" style="display:none;">
         </a>
         ;
    additional terms may apply.  By using this site, you agree to the
         <a href="//foundation.wikimedia.org/wiki/Terms_of_Use">
          Terms of Use
         </a>
         and
         <a href="//foundation.wikimedia.org/wiki/Privacy_policy">
          Privacy Policy
         </a>
         . Wikipedia® is a registered trademark of the
         <a href="//www.wikimediafoundation.org/">
          Wikimedia Foundation, Inc.
         </a>
         , a non-profit organization.
        </li>
       </ul>
       <ul id="footer-places">
        <li id="footer-places-privacy">
         <a class="extiw" href="https://foundation.wikimedia.org/wiki/Privacy_policy" title="wmf:Privacy policy">
          Privacy policy
         </a>
        </li>
        <li id="footer-places-about">
         <a href="/wiki/Wikipedia:About" title="Wikipedia:About">
          About Wikipedia
         </a>
        </li>
        <li id="footer-places-disclaimer">
         <a href="/wiki/Wikipedia:General_disclaimer" title="Wikipedia:General disclaimer">
          Disclaimers
         </a>
        </li>
        <li id="footer-places-contact">
         <a href="//en.wikipedia.org/wiki/Wikipedia:Contact_us">
          Contact Wikipedia
         </a>
        </li>
        <li id="footer-places-developers">
         <a href="https://www.mediawiki.org/wiki/Special:MyLanguage/How_to_contribute">
          Developers
         </a>
        </li>
        <li id="footer-places-statslink">
         <a href="https://stats.wikimedia.org/v2/#/en.wikipedia.org">
          Statistics
         </a>
        </li>
        <li id="footer-places-cookiestatement">
         <a href="https://foundation.wikimedia.org/wiki/Cookie_statement">
          Cookie statement
         </a>
        </li>
        <li id="footer-places-mobileview">
         <a class="noprint stopMobileRedirectToggle" href="//en.m.wikipedia.org/w/index.php?title=List_of_postal_codes_of_Canada:_M&amp;mobileaction=toggle_view_mobile">
          Mobile view
         </a>
        </li>
       </ul>
       <ul class="noprint" id="footer-icons">
        <li id="footer-copyrightico">
         <a href="https://wikimediafoundation.org/">
          <img alt="Wikimedia Foundation" height="31" src="/static/images/wikimedia-button.png" srcset="/static/images/wikimedia-button-1.5x.png 1.5x, /static/images/wikimedia-button-2x.png 2x" width="88"/>
         </a>
        </li>
        <li id="footer-poweredbyico">
         <a href="https://www.mediawiki.org/">
          <img alt="Powered by MediaWiki" height="31" src="/static/images/poweredby_mediawiki_88x31.png" srcset="/static/images/poweredby_mediawiki_132x47.png 1.5x, /static/images/poweredby_mediawiki_176x62.png 2x" width="88"/>
         </a>
        </li>
       </ul>
       <div style="clear: both;">
       </div>
      </div>
      <script>
       (RLQ=window.RLQ||[]).push(function(){mw.config.set({"wgPageParseReport":{"limitreport":{"cputime":"0.284","walltime":"0.353","ppvisitednodes":{"value":572,"limit":1000000},"ppgeneratednodes":{"value":0,"limit":1500000},"postexpandincludesize":{"value":10232,"limit":2097152},"templateargumentsize":{"value":13,"limit":2097152},"expansiondepth":{"value":5,"limit":40},"expensivefunctioncount":{"value":0,"limit":500},"unstrip-depth":{"value":1,"limit":20},"unstrip-size":{"value":9025,"limit":5000000},"entityaccesscount":{"value":0,"limit":400},"timingprofile":["100.00%  206.762      1 -total"," 73.26%  151.466      3 Template:Cite_web","  4.62%    9.552      1 Template:Canadian_postal_codes","  3.87%    8.009      1 Template:Col-2","  2.82%    5.822      1 Template:Col-begin","  1.93%    3.982      2 Template:Col-end","  1.53%    3.156      1 Template:Col-break"]},"scribunto":{"limitreport-timeusage":{"value":"0.101","limit":"10.000"},"limitreport-memusage":{"value":1836545,"limit":52428800}},"cachereport":{"origin":"mw1312","timestamp":"20191206171103","ttl":2592000,"transientcontent":false}}});});
      </script>
      <script type="application/ld+json">
       {"@context":"https:\/\/schema.org","@type":"Article","name":"List of postal codes of Canada: M","url":"https:\/\/en.wikipedia.org\/wiki\/List_of_postal_codes_of_Canada:_M","sameAs":"http:\/\/www.wikidata.org\/entity\/Q3248240","mainEntity":"http:\/\/www.wikidata.org\/entity\/Q3248240","author":{"@type":"Organization","name":"Contributors to Wikimedia projects"},"publisher":{"@type":"Organization","name":"Wikimedia Foundation, Inc.","logo":{"@type":"ImageObject","url":"https:\/\/www.wikimedia.org\/static\/images\/wmf-hor-googpub.png"}},"datePublished":"2004-03-20T10:02:13Z","dateModified":"2019-12-06T17:11:17Z","headline":"Wikimedia list article"}
      </script>
      <script>
       (RLQ=window.RLQ||[]).push(function(){mw.config.set({"wgBackendResponseTime":82,"wgHostname":"mw1319"});});
      </script>
     </body>
    </html>
    
    


```python
My_table = soup.find('table',{'class':'wikitable sortable'})
```


```python
My_table
```




    <table class="wikitable sortable">
    <tbody><tr>
    <th>Postcode</th>
    <th>Borough</th>
    <th>Neighbourhood
    </th></tr>
    <tr>
    <td>M1A</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M2A</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3A</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Parkwoods" title="Parkwoods">Parkwoods</a>
    </td></tr>
    <tr>
    <td>M4A</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Victoria_Village" title="Victoria Village">Victoria Village</a>
    </td></tr>
    <tr>
    <td>M5A</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Regent_Park" title="Regent Park">Harbourfront</a>
    </td></tr>
    <tr>
    <td>M6A</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Lawrence_Heights" title="Lawrence Heights">Lawrence Heights</a>
    </td></tr>
    <tr>
    <td>M6A</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Lawrence_Manor" title="Lawrence Manor">Lawrence Manor</a>
    </td></tr>
    <tr>
    <td>M7A</td>
    <td><a href="/wiki/Queen%27s_Park_(Toronto)" title="Queen's Park (Toronto)">Queen's Park</a></td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8A</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9A</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Queen%27s_Park_(Toronto)" title="Queen's Park (Toronto)">Queen's Park</a>
    </td></tr>
    <tr>
    <td>M1B</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Rouge,_Toronto" title="Rouge, Toronto">Rouge</a>
    </td></tr>
    <tr>
    <td>M1B</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Malvern,_Toronto" title="Malvern, Toronto">Malvern</a>
    </td></tr>
    <tr>
    <td>M2B</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3B</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Don Mills North
    </td></tr>
    <tr>
    <td>M4B</td>
    <td><a href="/wiki/East_York" title="East York">East York</a></td>
    <td><a class="mw-redirect" href="/wiki/Woodbine_Gardens" title="Woodbine Gardens">Woodbine Gardens</a>
    </td></tr>
    <tr>
    <td>M4B</td>
    <td><a href="/wiki/East_York" title="East York">East York</a></td>
    <td><a class="mw-redirect" href="/wiki/Parkview_Hill" title="Parkview Hill">Parkview Hill</a>
    </td></tr>
    <tr>
    <td>M5B</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Ryerson
    </td></tr>
    <tr>
    <td>M5B</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Garden District
    </td></tr>
    <tr>
    <td>M6B</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Glencairn
    </td></tr>
    <tr>
    <td>M7B</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8B</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9B</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Cloverdale
    </td></tr>
    <tr>
    <td>M9B</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/Islington,_Toronto" title="Islington, Toronto">Islington</a>
    </td></tr>
    <tr>
    <td>M9B</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Martin Grove
    </td></tr>
    <tr>
    <td>M9B</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Princess_Gardens" title="Princess Gardens">Princess Gardens</a>
    </td></tr>
    <tr>
    <td>M9B</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/West_Deane_Park" title="West Deane Park">West Deane Park</a>
    </td></tr>
    <tr>
    <td>M1C</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Highland_Creek_(Toronto)" title="Highland Creek (Toronto)">Highland Creek</a>
    </td></tr>
    <tr>
    <td>M1C</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a class="mw-redirect" href="/wiki/Rouge_Hill" title="Rouge Hill">Rouge Hill</a>
    </td></tr>
    <tr>
    <td>M1C</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Port_Union,_Toronto" title="Port Union, Toronto">Port Union</a>
    </td></tr>
    <tr>
    <td>M2C</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3C</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Flemingdon_Park" title="Flemingdon Park">Flemingdon Park</a>
    </td></tr>
    <tr>
    <td>M3C</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Don Mills South
    </td></tr>
    <tr>
    <td>M4C</td>
    <td><a href="/wiki/East_York" title="East York">East York</a></td>
    <td><a class="mw-redirect" href="/wiki/Woodbine_Heights" title="Woodbine Heights">Woodbine Heights</a>
    </td></tr>
    <tr>
    <td>M5C</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/St._James_Town" title="St. James Town">St. James Town</a>
    </td></tr>
    <tr>
    <td>M6C</td>
    <td>York</td>
    <td><a class="mw-redirect" href="/wiki/Humewood-Cedarvale" title="Humewood-Cedarvale">Humewood-Cedarvale</a>
    </td></tr>
    <tr>
    <td>M7C</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8C</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9C</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Bloordale Gardens
    </td></tr>
    <tr>
    <td>M9C</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Eringate
    </td></tr>
    <tr>
    <td>M9C</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Markland_Wood" title="Markland Wood">Markland Wood</a>
    </td></tr>
    <tr>
    <td>M9C</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Old Burnhamthorpe
    </td></tr>
    <tr>
    <td>M1E</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>Guildwood
    </td></tr>
    <tr>
    <td>M1E</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Morningside,_Toronto" title="Morningside, Toronto">Morningside</a>
    </td></tr>
    <tr>
    <td>M1E</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/West_Hill,_Toronto" title="West Hill, Toronto">West Hill</a>
    </td></tr>
    <tr>
    <td>M2E</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3E</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4E</td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a></td>
    <td><a href="/wiki/The_Beaches" title="The Beaches">The Beaches</a>
    </td></tr>
    <tr>
    <td>M5E</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Berczy_Park" title="Berczy Park">Berczy Park</a>
    </td></tr>
    <tr>
    <td>M6E</td>
    <td>York</td>
    <td>Caledonia-Fairbanks
    </td></tr>
    <tr>
    <td>M7E</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8E</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9E</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1G</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Woburn,_Toronto" title="Woburn, Toronto">Woburn</a>
    </td></tr>
    <tr>
    <td>M2G</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3G</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4G</td>
    <td><a href="/wiki/East_York" title="East York">East York</a></td>
    <td><a href="/wiki/Leaside" title="Leaside">Leaside</a>
    </td></tr>
    <tr>
    <td>M5G</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Central Bay Street
    </td></tr>
    <tr>
    <td>M6G</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Christie
    </td></tr>
    <tr>
    <td>M7G</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8G</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9G</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1H</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>Cedarbrae
    </td></tr>
    <tr>
    <td>M2H</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Hillcrest_Village" title="Hillcrest Village">Hillcrest Village</a>
    </td></tr>
    <tr>
    <td>M3H</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Bathurst_Manor" title="Bathurst Manor">Bathurst Manor</a>
    </td></tr>
    <tr>
    <td>M3H</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Downsview North
    </td></tr>
    <tr>
    <td>M3H</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a class="mw-redirect" href="/wiki/Wilson_Heights,_Toronto" title="Wilson Heights, Toronto">Wilson Heights</a>
    </td></tr>
    <tr>
    <td>M4H</td>
    <td><a href="/wiki/East_York" title="East York">East York</a></td>
    <td><a href="/wiki/Thorncliffe_Park" title="Thorncliffe Park">Thorncliffe Park</a>
    </td></tr>
    <tr>
    <td>M5H</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Adelaide
    </td></tr>
    <tr>
    <td>M5H</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>King
    </td></tr>
    <tr>
    <td>M5H</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Richmond
    </td></tr>
    <tr>
    <td>M6H</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/Dovercourt_Village" title="Dovercourt Village">Dovercourt Village</a>
    </td></tr>
    <tr>
    <td>M6H</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td>Dufferin
    </td></tr>
    <tr>
    <td>M7H</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8H</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9H</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1J</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Scarborough_Village" title="Scarborough Village">Scarborough Village</a>
    </td></tr>
    <tr>
    <td>M2J</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Fairview
    </td></tr>
    <tr>
    <td>M2J</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Henry_Farm" title="Henry Farm">Henry Farm</a>
    </td></tr>
    <tr>
    <td>M2J</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Oriole
    </td></tr>
    <tr>
    <td>M3J</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a class="mw-redirect" href="/wiki/Northwood_Park" title="Northwood Park">Northwood Park</a>
    </td></tr>
    <tr>
    <td>M3J</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/York_University" title="York University">York University</a>
    </td></tr>
    <tr>
    <td>M4J</td>
    <td><a href="/wiki/East_York" title="East York">East York</a></td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a>
    </td></tr>
    <tr>
    <td>M5J</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Harbourfront East
    </td></tr>
    <tr>
    <td>M5J</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Toronto_Islands" title="Toronto Islands">Toronto Islands</a>
    </td></tr>
    <tr>
    <td>M5J</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Union_Station_(Toronto)" title="Union Station (Toronto)">Union Station</a>
    </td></tr>
    <tr>
    <td>M6J</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/Little_Portugal,_Toronto" title="Little Portugal, Toronto">Little Portugal</a>
    </td></tr>
    <tr>
    <td>M6J</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/Trinity%E2%80%93Bellwoods" title="Trinity–Bellwoods">Trinity</a>
    </td></tr>
    <tr>
    <td>M7J</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8J</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9J</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1K</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>East Birchmount Park
    </td></tr>
    <tr>
    <td>M1K</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Ionview" title="Ionview">Ionview</a>
    </td></tr>
    <tr>
    <td>M1K</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a class="mw-redirect" href="/wiki/Kennedy_Park,_Toronto" title="Kennedy Park, Toronto">Kennedy Park</a>
    </td></tr>
    <tr>
    <td>M2K</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Bayview_Village" title="Bayview Village">Bayview Village</a>
    </td></tr>
    <tr>
    <td>M3K</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/CFB_Toronto" title="CFB Toronto">CFB Toronto</a>
    </td></tr>
    <tr>
    <td>M3K</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Downsview East
    </td></tr>
    <tr>
    <td>M4K</td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a></td>
    <td>The Danforth West
    </td></tr>
    <tr>
    <td>M4K</td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a></td>
    <td><a href="/wiki/Riverdale,_Toronto" title="Riverdale, Toronto">Riverdale</a>
    </td></tr>
    <tr>
    <td>M5K</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Design_Exchange" title="Design Exchange">Design Exchange</a>
    </td></tr>
    <tr>
    <td>M5K</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/Toronto_Dominion_Centre" title="Toronto Dominion Centre">Toronto Dominion Centre</a>
    </td></tr>
    <tr>
    <td>M6K</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td>Brockton
    </td></tr>
    <tr>
    <td>M6K</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/Exhibition_Place" title="Exhibition Place">Exhibition Place</a>
    </td></tr>
    <tr>
    <td>M6K</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/Parkdale_Village" title="Parkdale Village">Parkdale Village</a>
    </td></tr>
    <tr>
    <td>M7K</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8K</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9K</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1L</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Clairlea" title="Clairlea">Clairlea</a>
    </td></tr>
    <tr>
    <td>M1L</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Golden_Mile,_Toronto" title="Golden Mile, Toronto">Golden Mile</a>
    </td></tr>
    <tr>
    <td>M1L</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Oakridge,_Toronto" title="Oakridge, Toronto">Oakridge</a>
    </td></tr>
    <tr>
    <td>M2L</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Silver Hills
    </td></tr>
    <tr>
    <td>M2L</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/York_Mills" title="York Mills">York Mills</a>
    </td></tr>
    <tr>
    <td>M3L</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Downsview" title="Downsview">Downsview West</a>
    </td></tr>
    <tr>
    <td>M4L</td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a></td>
    <td>The Beaches West
    </td></tr>
    <tr>
    <td>M4L</td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/India_Bazaar" title="India Bazaar">India Bazaar</a>
    </td></tr>
    <tr>
    <td>M5L</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Commerce_Court" title="Commerce Court">Commerce Court</a>
    </td></tr>
    <tr>
    <td>M5L</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Victoria Hotel
    </td></tr>
    <tr>
    <td>M6L</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a class="mw-redirect" href="/wiki/Downsview,_Toronto" title="Downsview, Toronto">Downsview</a>
    </td></tr>
    <tr>
    <td>M6L</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>North Park
    </td></tr>
    <tr>
    <td>M6L</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Upwood Park
    </td></tr>
    <tr>
    <td>M7L</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8L</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9L</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Humber_Summit" title="Humber Summit">Humber Summit</a>
    </td></tr>
    <tr>
    <td>M1M</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Cliffcrest" title="Cliffcrest">Cliffcrest</a>
    </td></tr>
    <tr>
    <td>M1M</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Cliffside,_Toronto" title="Cliffside, Toronto">Cliffside</a>
    </td></tr>
    <tr>
    <td>M1M</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>Scarborough Village West
    </td></tr>
    <tr>
    <td>M2M</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Newtonbrook" title="Newtonbrook">Newtonbrook</a>
    </td></tr>
    <tr>
    <td>M2M</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Willowdale,_Toronto" title="Willowdale, Toronto">Willowdale</a>
    </td></tr>
    <tr>
    <td>M3M</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Downsview Central
    </td></tr>
    <tr>
    <td>M4M</td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a></td>
    <td>Studio District
    </td></tr>
    <tr>
    <td>M5M</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a href="/wiki/Bedford_Park,_Toronto" title="Bedford Park, Toronto">Bedford Park</a>
    </td></tr>
    <tr>
    <td>M5M</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Lawrence Manor East
    </td></tr>
    <tr>
    <td>M6M</td>
    <td><a href="/wiki/York,_Toronto" title="York, Toronto">York</a></td>
    <td>Del Ray
    </td></tr>
    <tr>
    <td>M6M</td>
    <td><a href="/wiki/York,_Toronto" title="York, Toronto">York</a></td>
    <td><a class="mw-redirect" href="/wiki/Keelesdale" title="Keelesdale">Keelesdale</a>
    </td></tr>
    <tr>
    <td>M6M</td>
    <td><a href="/wiki/York,_Toronto" title="York, Toronto">York</a></td>
    <td><a href="/wiki/Mount_Dennis" title="Mount Dennis">Mount Dennis</a>
    </td></tr>
    <tr>
    <td>M6M</td>
    <td><a href="/wiki/York,_Toronto" title="York, Toronto">York</a></td>
    <td><a href="/wiki/Silverthorn,_Toronto" title="Silverthorn, Toronto">Silverthorn</a>
    </td></tr>
    <tr>
    <td>M7M</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8M</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9M</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a class="mw-redirect" href="/wiki/Emery,_Toronto" title="Emery, Toronto">Emery</a>
    </td></tr>
    <tr>
    <td>M9M</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a class="mw-redirect" href="/wiki/Humberlea" title="Humberlea">Humberlea</a>
    </td></tr>
    <tr>
    <td>M1N</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Birch_Cliff" title="Birch Cliff">Birch Cliff</a>
    </td></tr>
    <tr>
    <td>M1N</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>Cliffside West
    </td></tr>
    <tr>
    <td>M2N</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Willowdale South
    </td></tr>
    <tr>
    <td>M3N</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>Downsview Northwest
    </td></tr>
    <tr>
    <td>M4N</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a href="/wiki/Lawrence_Park,_Toronto" title="Lawrence Park, Toronto">Lawrence Park</a>
    </td></tr>
    <tr>
    <td>M5N</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>Roselawn
    </td></tr>
    <tr>
    <td>M6N</td>
    <td><a href="/wiki/York,_Toronto" title="York, Toronto">York</a></td>
    <td>The Junction North
    </td></tr>
    <tr>
    <td>M6N</td>
    <td><a href="/wiki/York,_Toronto" title="York, Toronto">York</a></td>
    <td>Runnymede
    </td></tr>
    <tr>
    <td>M7N</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8N</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9N</td>
    <td><a href="/wiki/York,_Toronto" title="York, Toronto">York</a></td>
    <td><a href="/wiki/Weston,_Toronto" title="Weston, Toronto">Weston</a>
    </td></tr>
    <tr>
    <td>M1P</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Dorset_Park" title="Dorset Park">Dorset Park</a>
    </td></tr>
    <tr>
    <td>M1P</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Scarborough_Town_Centre" title="Scarborough Town Centre">Scarborough Town Centre</a>
    </td></tr>
    <tr>
    <td>M1P</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a class="mw-redirect" href="/wiki/Wexford_Heights" title="Wexford Heights">Wexford Heights</a>
    </td></tr>
    <tr>
    <td>M2P</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td>York Mills West
    </td></tr>
    <tr>
    <td>M3P</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4P</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>Davisville North
    </td></tr>
    <tr>
    <td>M5P</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/Forest_Hill_North" title="Forest Hill North">Forest Hill North</a>
    </td></tr>
    <tr>
    <td>M5P</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>Forest Hill West
    </td></tr>
    <tr>
    <td>M6P</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/High_Park" title="High Park">High Park</a>
    </td></tr>
    <tr>
    <td>M6P</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td>The Junction South
    </td></tr>
    <tr>
    <td>M7P</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8P</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9P</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Westmount
    </td></tr>
    <tr>
    <td>M1R</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Maryvale,_Toronto" title="Maryvale, Toronto">Maryvale</a>
    </td></tr>
    <tr>
    <td>M1R</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Wexford,_Toronto" title="Wexford, Toronto">Wexford</a>
    </td></tr>
    <tr>
    <td>M2R</td>
    <td><a href="/wiki/North_York" title="North York">North York</a></td>
    <td><a class="mw-redirect" href="/wiki/Willowdale_West" title="Willowdale West">Willowdale West</a>
    </td></tr>
    <tr>
    <td>M3R</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4R</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>North Toronto West
    </td></tr>
    <tr>
    <td>M5R</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a href="/wiki/The_Annex" title="The Annex">The Annex</a>
    </td></tr>
    <tr>
    <td>M5R</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>North Midtown
    </td></tr>
    <tr>
    <td>M5R</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a href="/wiki/Yorkville,_Toronto" title="Yorkville, Toronto">Yorkville</a>
    </td></tr>
    <tr>
    <td>M6R</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/Parkdale,_Toronto" title="Parkdale, Toronto">Parkdale</a>
    </td></tr>
    <tr>
    <td>M6R</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/Roncesvalles,_Toronto" title="Roncesvalles, Toronto">Roncesvalles</a>
    </td></tr>
    <tr>
    <td>M7R</td>
    <td>Mississauga</td>
    <td>Canada Post Gateway Processing Centre
    </td></tr>
    <tr>
    <td>M8R</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9R</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Kingsview_Village" title="Kingsview Village">Kingsview Village</a>
    </td></tr>
    <tr>
    <td>M9R</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Martin Grove Gardens
    </td></tr>
    <tr>
    <td>M9R</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Richview Gardens
    </td></tr>
    <tr>
    <td>M9R</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>St. Phillips
    </td></tr>
    <tr>
    <td>M1S</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Agincourt,_Toronto" title="Agincourt, Toronto">Agincourt</a>
    </td></tr>
    <tr>
    <td>M2S</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3S</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4S</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>Davisville
    </td></tr>
    <tr>
    <td>M5S</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Harbord
    </td></tr>
    <tr>
    <td>M5S</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/University_of_Toronto" title="University of Toronto">University of Toronto</a>
    </td></tr>
    <tr>
    <td>M6S</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/Runnymede,_Toronto" title="Runnymede, Toronto">Runnymede</a>
    </td></tr>
    <tr>
    <td>M6S</td>
    <td><a href="/wiki/West_Toronto" title="West Toronto">West Toronto</a></td>
    <td><a href="/wiki/Swansea,_Toronto" title="Swansea, Toronto">Swansea</a>
    </td></tr>
    <tr>
    <td>M7S</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8S</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9S</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1T</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>Clarks Corners
    </td></tr>
    <tr>
    <td>M1T</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>Sullivan
    </td></tr>
    <tr>
    <td>M1T</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Tam_O%27Shanter_%E2%80%93_Sullivan" title="Tam O'Shanter – Sullivan">Tam O'Shanter</a>
    </td></tr>
    <tr>
    <td>M2T</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3T</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4T</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a href="/wiki/Moore_Park,_Toronto" title="Moore Park, Toronto">Moore Park</a>
    </td></tr>
    <tr>
    <td>M4T</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>Summerhill East
    </td></tr>
    <tr>
    <td>M5T</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Chinatown,_Toronto" title="Chinatown, Toronto">Chinatown</a>
    </td></tr>
    <tr>
    <td>M5T</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Grange_Park_(Toronto)" title="Grange Park (Toronto)">Grange Park</a>
    </td></tr>
    <tr>
    <td>M5T</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Kensington_Market" title="Kensington Market">Kensington Market</a>
    </td></tr>
    <tr>
    <td>M6T</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M7T</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8T</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M9T</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1V</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a class="mw-redirect" href="/wiki/Agincourt_North" title="Agincourt North">Agincourt North</a>
    </td></tr>
    <tr>
    <td>M1V</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>L'Amoreaux East
    </td></tr>
    <tr>
    <td>M1V</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a href="/wiki/Milliken,_Ontario" title="Milliken, Ontario">Milliken</a>
    </td></tr>
    <tr>
    <td>M1V</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>Steeles East
    </td></tr>
    <tr>
    <td>M2V</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3V</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4V</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a href="/wiki/Deer_Park,_Toronto" title="Deer Park, Toronto">Deer Park</a>
    </td></tr>
    <tr>
    <td>M4V</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>Forest Hill SE
    </td></tr>
    <tr>
    <td>M4V</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/Rathnelly" title="Rathnelly">Rathnelly</a>
    </td></tr>
    <tr>
    <td>M4V</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td><a href="/wiki/South_Hill,_Toronto" title="South Hill, Toronto">South Hill</a>
    </td></tr>
    <tr>
    <td>M4V</td>
    <td><a class="mw-redirect" href="/wiki/Central_Toronto" title="Central Toronto">Central Toronto</a></td>
    <td>Summerhill West
    </td></tr>
    <tr>
    <td>M5V</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/CN_Tower" title="CN Tower">CN Tower</a>
    </td></tr>
    <tr>
    <td>M5V</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Bathurst Quay
    </td></tr>
    <tr>
    <td>M5V</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Island airport
    </td></tr>
    <tr>
    <td>M5V</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Harbourfront West
    </td></tr>
    <tr>
    <td>M5V</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/King_and_Spadina" title="King and Spadina">King and Spadina</a>
    </td></tr>
    <tr>
    <td>M5V</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Railway_Lands" title="Railway Lands">Railway Lands</a>
    </td></tr>
    <tr>
    <td>M5V</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a class="mw-redirect" href="/wiki/South_Niagara" title="South Niagara">South Niagara</a>
    </td></tr>
    <tr>
    <td>M6V</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M7V</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Humber Bay Shores
    </td></tr>
    <tr>
    <td>M8V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Mimico South
    </td></tr>
    <tr>
    <td>M8V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/New_Toronto" title="New Toronto">New Toronto</a>
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Albion Gardens
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/Beaumond_Heights" title="Beaumond Heights">Beaumond Heights</a>
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Humbergate
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/Mount_Olive-Silverstone-Jamestown" title="Mount Olive-Silverstone-Jamestown">Jamestown</a>
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/Mount_Olive-Silverstone-Jamestown" title="Mount Olive-Silverstone-Jamestown">Mount Olive</a>
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/Silverstone,_Toronto" title="Silverstone, Toronto">Silverstone</a>
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/South_Steeles" title="South Steeles">South Steeles</a>
    </td></tr>
    <tr>
    <td>M9V</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Thistletown" title="Thistletown">Thistletown</a>
    </td></tr>
    <tr>
    <td>M1W</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td>L'Amoreaux West
    </td></tr>
    <tr>
    <td>M2W</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3W</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4W</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Rosedale,_Toronto" title="Rosedale, Toronto">Rosedale</a>
    </td></tr>
    <tr>
    <td>M5W</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td>Stn A PO Boxes 25 The Esplanade
    </td></tr>
    <tr>
    <td>M6W</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M7W</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8W</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Alderwood,_Toronto" title="Alderwood, Toronto">Alderwood</a>
    </td></tr>
    <tr>
    <td>M8W</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Long_Branch,_Toronto" title="Long Branch, Toronto">Long Branch</a>
    </td></tr>
    <tr>
    <td>M9W</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Northwest
    </td></tr>
    <tr>
    <td>M1X</td>
    <td><a href="/wiki/Scarborough,_Toronto" title="Scarborough, Toronto">Scarborough</a></td>
    <td><a class="mw-redirect" href="/wiki/Upper_Rouge" title="Upper Rouge">Upper Rouge</a>
    </td></tr>
    <tr>
    <td>M2X</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3X</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4X</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Cabbagetown,_Toronto" title="Cabbagetown, Toronto">Cabbagetown</a>
    </td></tr>
    <tr>
    <td>M4X</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/St._James_Town" title="St. James Town">St. James Town</a>
    </td></tr>
    <tr>
    <td>M5X</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/First_Canadian_Place" title="First Canadian Place">First Canadian Place</a>
    </td></tr>
    <tr>
    <td>M5X</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Underground_city" title="Underground city">Underground city</a>
    </td></tr>
    <tr>
    <td>M6X</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M7X</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8X</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/The_Kingsway" title="The Kingsway">The Kingsway</a>
    </td></tr>
    <tr>
    <td>M8X</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Montgomery Road
    </td></tr>
    <tr>
    <td>M8X</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Old Mill North
    </td></tr>
    <tr>
    <td>M9X</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1Y</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M2Y</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3Y</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4Y</td>
    <td><a href="/wiki/Downtown_Toronto" title="Downtown Toronto">Downtown Toronto</a></td>
    <td><a href="/wiki/Church_and_Wellesley" title="Church and Wellesley">Church and Wellesley</a>
    </td></tr>
    <tr>
    <td>M5Y</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M6Y</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M7Y</td>
    <td><a href="/wiki/East_Toronto" title="East Toronto">East Toronto</a></td>
    <td>Business Reply Mail Processing Centre 969 Eastern
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Humber_Bay" title="Humber Bay">Humber Bay</a>
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>King's Mill Park
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Kingsway Park South East
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Mimico" title="Mimico">Mimico NE</a>
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Old_Mill,_Toronto" title="Old Mill, Toronto">Old Mill South</a>
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/The_Queensway" title="The Queensway">The Queensway East</a>
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/Fairmont_Royal_York_Hotel" title="Fairmont Royal York Hotel">Royal York South East</a>
    </td></tr>
    <tr>
    <td>M8Y</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a class="mw-redirect" href="/wiki/Sunnylea" title="Sunnylea">Sunnylea</a>
    </td></tr>
    <tr>
    <td>M9Y</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M1Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M2Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M3Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M4Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M5Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M6Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M7Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    <tr>
    <td>M8Z</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Kingsway Park South West
    </td></tr>
    <tr>
    <td>M8Z</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/Mimico" title="Mimico">Mimico NW</a>
    </td></tr>
    <tr>
    <td>M8Z</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td><a href="/wiki/The_Queensway" title="The Queensway">The Queensway West</a>
    </td></tr>
    <tr>
    <td>M8Z</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>Royal York South West
    </td></tr>
    <tr>
    <td>M8Z</td>
    <td><a href="/wiki/Etobicoke" title="Etobicoke">Etobicoke</a></td>
    <td>South of Bloor
    </td></tr>
    <tr>
    <td>M9Z</td>
    <td>Not assigned</td>
    <td>Not assigned
    </td></tr>
    </tbody></table>




```python
data_frame = pd.read_html(str(My_table))[0]
```


```python
data_frame
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1A</td>
      <td>Not assigned</td>
      <td>Not assigned</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M2A</td>
      <td>Not assigned</td>
      <td>Not assigned</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Harbourfront</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>282</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>Mimico NW</td>
    </tr>
    <tr>
      <td>283</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>The Queensway West</td>
    </tr>
    <tr>
      <td>284</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>Royal York South West</td>
    </tr>
    <tr>
      <td>285</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>South of Bloor</td>
    </tr>
    <tr>
      <td>286</td>
      <td>M9Z</td>
      <td>Not assigned</td>
      <td>Not assigned</td>
    </tr>
  </tbody>
</table>
<p>287 rows × 3 columns</p>
</div>



#### 2.a) Working on Boroughs with value not assigned 


```python
# checking for not assigned boroughs
data_frame['Borough'].value_counts()
```




    Not assigned        77
    Etobicoke           44
    North York          38
    Scarborough         37
    Downtown Toronto    37
    Central Toronto     17
    West Toronto        13
    York                 9
    East Toronto         7
    East York            6
    Mississauga          1
    Queen's Park         1
    Name: Borough, dtype: int64




```python
#there are 77 not assigned boroughs
df = data_frame[data_frame.Borough != 'Not assigned']
```


```python
#checking if all rows ave been removed properly
df['Borough'].value_counts()
```




    Etobicoke           44
    North York          38
    Scarborough         37
    Downtown Toronto    37
    Central Toronto     17
    West Toronto        13
    York                 9
    East Toronto         7
    East York            6
    Mississauga          1
    Queen's Park         1
    Name: Borough, dtype: int64




```python
# as we can see all boroughs with not assigned have been removed
```


```python
#there are 107 duplicated Postcode
df['Postcode'][df['Postcode'].duplicated()].shape
```




    (107,)




```python
df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Harbourfront</td>
    </tr>
    <tr>
      <td>5</td>
      <td>M6A</td>
      <td>North York</td>
      <td>Lawrence Heights</td>
    </tr>
    <tr>
      <td>6</td>
      <td>M6A</td>
      <td>North York</td>
      <td>Lawrence Manor</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>281</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>Kingsway Park South West</td>
    </tr>
    <tr>
      <td>282</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>Mimico NW</td>
    </tr>
    <tr>
      <td>283</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>The Queensway West</td>
    </tr>
    <tr>
      <td>284</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>Royal York South West</td>
    </tr>
    <tr>
      <td>285</td>
      <td>M8Z</td>
      <td>Etobicoke</td>
      <td>South of Bloor</td>
    </tr>
  </tbody>
</table>
<p>210 rows × 3 columns</p>
</div>



#### 2.b) replacing not assing Neighbourhood by borough name


```python
df.Neighbourhood.replace('Not assigned',df.Borough,inplace=True)
```


```python
df.head(10)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>2</td>
      <td>M3A</td>
      <td>North York</td>
      <td>Parkwoods</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M4A</td>
      <td>North York</td>
      <td>Victoria Village</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M5A</td>
      <td>Downtown Toronto</td>
      <td>Harbourfront</td>
    </tr>
    <tr>
      <td>5</td>
      <td>M6A</td>
      <td>North York</td>
      <td>Lawrence Heights</td>
    </tr>
    <tr>
      <td>6</td>
      <td>M6A</td>
      <td>North York</td>
      <td>Lawrence Manor</td>
    </tr>
    <tr>
      <td>7</td>
      <td>M7A</td>
      <td>Queen's Park</td>
      <td>Queen's Park</td>
    </tr>
    <tr>
      <td>9</td>
      <td>M9A</td>
      <td>Downtown Toronto</td>
      <td>Queen's Park</td>
    </tr>
    <tr>
      <td>10</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Rouge</td>
    </tr>
    <tr>
      <td>11</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Malvern</td>
    </tr>
    <tr>
      <td>13</td>
      <td>M3B</td>
      <td>North York</td>
      <td>Don Mills North</td>
    </tr>
  </tbody>
</table>
</div>




```python
# combining groups with same postcode
df_group = df.groupby('Postcode').agg({'Borough' : 'first', 'Neighbourhood' : ','.join}).reset_index().reindex(columns=df.columns)
```


```python
df_group
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Rouge,Malvern</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>Scarborough</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>Scarborough</td>
      <td>Guildwood,Morningside,West Hill</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>Scarborough</td>
      <td>Woburn</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
    </tr>
    <tr>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <td>98</td>
      <td>M9N</td>
      <td>York</td>
      <td>Weston</td>
    </tr>
    <tr>
      <td>99</td>
      <td>M9P</td>
      <td>Etobicoke</td>
      <td>Westmount</td>
    </tr>
    <tr>
      <td>100</td>
      <td>M9R</td>
      <td>Etobicoke</td>
      <td>Kingsview Village,Martin Grove Gardens,Richvie...</td>
    </tr>
    <tr>
      <td>101</td>
      <td>M9V</td>
      <td>Etobicoke</td>
      <td>Albion Gardens,Beaumond Heights,Humbergate,Jam...</td>
    </tr>
    <tr>
      <td>102</td>
      <td>M9W</td>
      <td>Etobicoke</td>
      <td>Northwest</td>
    </tr>
  </tbody>
</table>
<p>103 rows × 3 columns</p>
</div>




```python
df_group.shape
```




    (103, 3)




```python
df_l = pd.read_csv('Geospatial_Coordinates.csv')
```

#### 2.c) adding latitude and longitude to dataframe


```python
df_l.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postal Code</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>43.806686</td>
      <td>-79.194353</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>43.784535</td>
      <td>-79.160497</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>43.763573</td>
      <td>-79.188711</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>43.770992</td>
      <td>-79.216917</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>43.773136</td>
      <td>-79.239476</td>
    </tr>
  </tbody>
</table>
</div>




```python
df_l.shape
```




    (103, 3)




```python
df_new = pd.concat([df_group,df_l],axis=1)
```


```python
df_new.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
      <th>Postal Code</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Rouge,Malvern</td>
      <td>M1B</td>
      <td>43.806686</td>
      <td>-79.194353</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>Scarborough</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>M1C</td>
      <td>43.784535</td>
      <td>-79.160497</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>Scarborough</td>
      <td>Guildwood,Morningside,West Hill</td>
      <td>M1E</td>
      <td>43.763573</td>
      <td>-79.188711</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>Scarborough</td>
      <td>Woburn</td>
      <td>M1G</td>
      <td>43.770992</td>
      <td>-79.216917</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
      <td>M1H</td>
      <td>43.773136</td>
      <td>-79.239476</td>
    </tr>
  </tbody>
</table>
</div>




```python
#dropping extra postal code column
df_new = df_new.drop(['Postal Code'],axis=1)
df_new.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Rouge,Malvern</td>
      <td>43.806686</td>
      <td>-79.194353</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>Scarborough</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>43.784535</td>
      <td>-79.160497</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>Scarborough</td>
      <td>Guildwood,Morningside,West Hill</td>
      <td>43.763573</td>
      <td>-79.188711</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>Scarborough</td>
      <td>Woburn</td>
      <td>43.770992</td>
      <td>-79.216917</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
      <td>43.773136</td>
      <td>-79.239476</td>
    </tr>
  </tbody>
</table>
</div>



## Mapping


```python
import folium
```


```python
#latitude and longitude of toronto
latitude = 43.6532
longitude = -79.3832

map_toronto = folium.Map(location=[latitude,longitude], zoom_start=10)

#add markers to map
for lat,lng,borough, neighborhood in zip(df_new['Latitude'], df_new['Longitude'], df_new['Borough'], df_new['Neighbourhood']):
    label = '{}, {}'.format(neighborhood, borough)
    label = folium.Popup(label, parse_html=True)
    folium.CircleMarker(
        [lat, lng],
        radius=5,
        popup=label,
        color='blue',
        fill=True,
        fill_color='#3186cc',
        fill_opacity=0.7,
        parse_html=False
    ).add_to(map_toronto)
    
map_toronto
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><iframe src="data:text/html;charset=utf-8;base64,PCFET0NUWVBFIGh0bWw+CjxoZWFkPiAgICAKICAgIDxtZXRhIGh0dHAtZXF1aXY9ImNvbnRlbnQtdHlwZSIgY29udGVudD0idGV4dC9odG1sOyBjaGFyc2V0PVVURi04IiAvPgogICAgPHNjcmlwdD5MX1BSRUZFUl9DQU5WQVMgPSBmYWxzZTsgTF9OT19UT1VDSCA9IGZhbHNlOyBMX0RJU0FCTEVfM0QgPSBmYWxzZTs8L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmpzIj48L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2FqYXguZ29vZ2xlYXBpcy5jb20vYWpheC9saWJzL2pxdWVyeS8xLjExLjEvanF1ZXJ5Lm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvanMvYm9vdHN0cmFwLm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9jZG5qcy5jbG91ZGZsYXJlLmNvbS9hamF4L2xpYnMvTGVhZmxldC5hd2Vzb21lLW1hcmtlcnMvMi4wLjIvbGVhZmxldC5hd2Vzb21lLW1hcmtlcnMuanMiPjwvc2NyaXB0PgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL21heGNkbi5ib290c3RyYXBjZG4uY29tL2Jvb3RzdHJhcC8zLjIuMC9jc3MvYm9vdHN0cmFwLm1pbi5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvY3NzL2Jvb3RzdHJhcC10aGVtZS5taW4uY3NzIi8+CiAgICA8bGluayByZWw9InN0eWxlc2hlZXQiIGhyZWY9Imh0dHBzOi8vbWF4Y2RuLmJvb3RzdHJhcGNkbi5jb20vZm9udC1hd2Vzb21lLzQuNi4zL2Nzcy9mb250LWF3ZXNvbWUubWluLmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2NkbmpzLmNsb3VkZmxhcmUuY29tL2FqYXgvbGlicy9MZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy8yLjAuMi9sZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9yYXdnaXQuY29tL3B5dGhvbi12aXN1YWxpemF0aW9uL2ZvbGl1bS9tYXN0ZXIvZm9saXVtL3RlbXBsYXRlcy9sZWFmbGV0LmF3ZXNvbWUucm90YXRlLmNzcyIvPgogICAgPHN0eWxlPmh0bWwsIGJvZHkge3dpZHRoOiAxMDAlO2hlaWdodDogMTAwJTttYXJnaW46IDA7cGFkZGluZzogMDt9PC9zdHlsZT4KICAgIDxzdHlsZT4jbWFwIHtwb3NpdGlvbjphYnNvbHV0ZTt0b3A6MDtib3R0b206MDtyaWdodDowO2xlZnQ6MDt9PC9zdHlsZT4KICAgIAogICAgICAgICAgICA8c3R5bGU+ICNtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUgewogICAgICAgICAgICAgICAgcG9zaXRpb24gOiByZWxhdGl2ZTsKICAgICAgICAgICAgICAgIHdpZHRoIDogMTAwLjAlOwogICAgICAgICAgICAgICAgaGVpZ2h0OiAxMDAuMCU7CiAgICAgICAgICAgICAgICBsZWZ0OiAwLjAlOwogICAgICAgICAgICAgICAgdG9wOiAwLjAlOwogICAgICAgICAgICAgICAgfQogICAgICAgICAgICA8L3N0eWxlPgogICAgICAgIAo8L2hlYWQ+Cjxib2R5PiAgICAKICAgIAogICAgICAgICAgICA8ZGl2IGNsYXNzPSJmb2xpdW0tbWFwIiBpZD0ibWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1IiA+PC9kaXY+CiAgICAgICAgCjwvYm9keT4KPHNjcmlwdD4gICAgCiAgICAKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGJvdW5kcyA9IG51bGw7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgdmFyIG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSA9IEwubWFwKAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJ21hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNScsCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7Y2VudGVyOiBbNDMuNjUzMiwtNzkuMzgzMl0sCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB6b29tOiAxMCwKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIG1heEJvdW5kczogYm91bmRzLAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgbGF5ZXJzOiBbXSwKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHdvcmxkQ29weUp1bXA6IGZhbHNlLAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgY3JzOiBMLkNSUy5FUFNHMzg1NwogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9KTsKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHRpbGVfbGF5ZXJfYzIwNzZlNmZlZmE1NGQ4MDhiNjgzZDBkM2E3ZmVkMmIgPSBMLnRpbGVMYXllcigKICAgICAgICAgICAgICAgICdodHRwczovL3tzfS50aWxlLm9wZW5zdHJlZXRtYXAub3JnL3t6fS97eH0ve3l9LnBuZycsCiAgICAgICAgICAgICAgICB7CiAgImF0dHJpYnV0aW9uIjogbnVsbCwKICAiZGV0ZWN0UmV0aW5hIjogZmFsc2UsCiAgIm1heFpvb20iOiAxOCwKICAibWluWm9vbSI6IDEsCiAgIm5vV3JhcCI6IGZhbHNlLAogICJzdWJkb21haW5zIjogImFiYyIKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzA2YmFlNWMxMDRjNDQyNWFhMDI0ZjBkMWZiZjUzZDUzID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuODA2Njg2Mjk5OTk5OTk2LC03OS4xOTQzNTM0MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9lYjU1MzZiODhiYzQ0MjViODA4OTg1OGQ4NzI2ZDM1MCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF85MTBiZjQwMzkxMzE0YjQwYTQ0YmNkYzkzN2U2MmFiZSA9ICQoJzxkaXYgaWQ9Imh0bWxfOTEwYmY0MDM5MTMxNGI0MGE0NGJjZGM5MzdlNjJhYmUiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlJvdWdlLE1hbHZlcm4sIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9lYjU1MzZiODhiYzQ0MjViODA4OTg1OGQ4NzI2ZDM1MC5zZXRDb250ZW50KGh0bWxfOTEwYmY0MDM5MTMxNGI0MGE0NGJjZGM5MzdlNjJhYmUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMDZiYWU1YzEwNGM0NDI1YWEwMjRmMGQxZmJmNTNkNTMuYmluZFBvcHVwKHBvcHVwX2ViNTUzNmI4OGJjNDQyNWI4MDg5ODU4ZDg3MjZkMzUwKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2NhY2U5Y2Y0MmM2YzRmNDVhYmJlMjhkZWMwM2UwNGNjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzg0NTM1MSwtNzkuMTYwNDk3MDk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfY2ViN2Y3Y2QxMDkxNDUxNjlkYjA4NzE2M2JiOTRmMmIgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYjc2OWU0YTE2MWU0NGRhNDlkNjkwNTA3YWRjYzM4MTcgPSAkKCc8ZGl2IGlkPSJodG1sX2I3NjllNGExNjFlNDRkYTQ5ZDY5MDUwN2FkY2MzODE3IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5IaWdobGFuZCBDcmVlayxSb3VnZSBIaWxsLFBvcnQgVW5pb24sIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9jZWI3ZjdjZDEwOTE0NTE2OWRiMDg3MTYzYmI5NGYyYi5zZXRDb250ZW50KGh0bWxfYjc2OWU0YTE2MWU0NGRhNDlkNjkwNTA3YWRjYzM4MTcpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfY2FjZTljZjQyYzZjNGY0NWFiYmUyOGRlYzAzZTA0Y2MuYmluZFBvcHVwKHBvcHVwX2NlYjdmN2NkMTA5MTQ1MTY5ZGIwODcxNjNiYjk0ZjJiKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzcyMzg5OGRjZjYwYTQ4OGE4MmVhNmUwOGQ2OTk3NmViID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzYzNTcyNiwtNzkuMTg4NzExNV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9kMGVmNDMxYzM2ODA0NWQ1YTQzZGYwNWIwMGJhMDAzZSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8yMTc2ZTkzZDZkNWE0NWE1YTBmOTczMzQzZDc5ZTQxMSA9ICQoJzxkaXYgaWQ9Imh0bWxfMjE3NmU5M2Q2ZDVhNDVhNWEwZjk3MzM0M2Q3OWU0MTEiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkd1aWxkd29vZCxNb3JuaW5nc2lkZSxXZXN0IEhpbGwsIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9kMGVmNDMxYzM2ODA0NWQ1YTQzZGYwNWIwMGJhMDAzZS5zZXRDb250ZW50KGh0bWxfMjE3NmU5M2Q2ZDVhNDVhNWEwZjk3MzM0M2Q3OWU0MTEpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNzIzODk4ZGNmNjBhNDg4YTgyZWE2ZTA4ZDY5OTc2ZWIuYmluZFBvcHVwKHBvcHVwX2QwZWY0MzFjMzY4MDQ1ZDVhNDNkZjA1YjAwYmEwMDNlKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2MyNjE2NmFmODBmNDRlNGU4Mjc4ZmY5MTFlMWFiNDY3ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzcwOTkyMSwtNzkuMjE2OTE3NDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfN2Q3NDZhYzEwNjMwNDliMTljZTI2MTVmZDJlMjIzMTEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfN2JjMTlmNDkwNTM2NDY4YWJhOGQ2Njc1N2YyOTAwZTUgPSAkKCc8ZGl2IGlkPSJodG1sXzdiYzE5ZjQ5MDUzNjQ2OGFiYThkNjY3NTdmMjkwMGU1IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Xb2J1cm4sIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF83ZDc0NmFjMTA2MzA0OWIxOWNlMjYxNWZkMmUyMjMxMS5zZXRDb250ZW50KGh0bWxfN2JjMTlmNDkwNTM2NDY4YWJhOGQ2Njc1N2YyOTAwZTUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYzI2MTY2YWY4MGY0NGU0ZTgyNzhmZjkxMWUxYWI0NjcuYmluZFBvcHVwKHBvcHVwXzdkNzQ2YWMxMDYzMDQ5YjE5Y2UyNjE1ZmQyZTIyMzExKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzdhMTMxMmMwY2Y4YTQ4ODU5YjliMTRmZDdiMmEyMGYxID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzczMTM2LC03OS4yMzk0NzYwOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8wMDljMjJiZjM4YTM0NWYxOTQzY2FmOGIyMjQwOTZmYiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF83YTZlNDg3ZWIwZDY0ZWQ1YjUzMTVkNTViNWMwM2E2YyA9ICQoJzxkaXYgaWQ9Imh0bWxfN2E2ZTQ4N2ViMGQ2NGVkNWI1MzE1ZDU1YjVjMDNhNmMiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNlZGFyYnJhZSwgU2NhcmJvcm91Z2g8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzAwOWMyMmJmMzhhMzQ1ZjE5NDNjYWY4YjIyNDA5NmZiLnNldENvbnRlbnQoaHRtbF83YTZlNDg3ZWIwZDY0ZWQ1YjUzMTVkNTViNWMwM2E2Yyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl83YTEzMTJjMGNmOGE0ODg1OWI5YjE0ZmQ3YjJhMjBmMS5iaW5kUG9wdXAocG9wdXBfMDA5YzIyYmYzOGEzNDVmMTk0M2NhZjhiMjI0MDk2ZmIpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfYWFjOGFhMjAzMzIzNDNhNGIzNzk4Y2E5MmRkMDM0YzggPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43NDQ3MzQyLC03OS4yMzk0NzYwOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8wNTlhNWJkMGYyZjE0ZGZmOTMyZjQ3YjY2NDAyOTAxOCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF85MDc2YTVlZjY0ODk0OTk3YmQ0MGU5YWU4ZTNkZDUzOCA9ICQoJzxkaXYgaWQ9Imh0bWxfOTA3NmE1ZWY2NDg5NDk5N2JkNDBlOWFlOGUzZGQ1MzgiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlNjYXJib3JvdWdoIFZpbGxhZ2UsIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8wNTlhNWJkMGYyZjE0ZGZmOTMyZjQ3YjY2NDAyOTAxOC5zZXRDb250ZW50KGh0bWxfOTA3NmE1ZWY2NDg5NDk5N2JkNDBlOWFlOGUzZGQ1MzgpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYWFjOGFhMjAzMzIzNDNhNGIzNzk4Y2E5MmRkMDM0YzguYmluZFBvcHVwKHBvcHVwXzA1OWE1YmQwZjJmMTRkZmY5MzJmNDdiNjY0MDI5MDE4KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2Y0MzI5ODJjNmY3MzRiOWZhMDZjZWE5NmE1Yzg3NDNkID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzI3OTI5MiwtNzkuMjYyMDI5NDAwMDAwMDJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNDlkNmMwM2Q3ZGZkNGU0OGI1MDU1NDdmMjViYTRmNWIgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfOWU1ODU2MGMyNmQ5NDA5MDk2MGMwMzg0ZDJkMzk1ZWEgPSAkKCc8ZGl2IGlkPSJodG1sXzllNTg1NjBjMjZkOTQwOTA5NjBjMDM4NGQyZDM5NWVhIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5FYXN0IEJpcmNobW91bnQgUGFyayxJb252aWV3LEtlbm5lZHkgUGFyaywgU2NhcmJvcm91Z2g8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzQ5ZDZjMDNkN2RmZDRlNDhiNTA1NTQ3ZjI1YmE0ZjViLnNldENvbnRlbnQoaHRtbF85ZTU4NTYwYzI2ZDk0MDkwOTYwYzAzODRkMmQzOTVlYSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9mNDMyOTgyYzZmNzM0YjlmYTA2Y2VhOTZhNWM4NzQzZC5iaW5kUG9wdXAocG9wdXBfNDlkNmMwM2Q3ZGZkNGU0OGI1MDU1NDdmMjViYTRmNWIpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfNzA3ZjY3MzA1ODhkNGY4OGIyY2NhNDIyYjNlZjNiMWYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43MTExMTE3MDAwMDAwMDQsLTc5LjI4NDU3NzJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfYzI5ZDNmZTkzZjViNGVhNWE4MWVhZWNjYjZkMzE0MGUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYjFjZmQxZTM3MWY5NDA3Njg4MTY4ZDA0NjE1ZDZmNDUgPSAkKCc8ZGl2IGlkPSJodG1sX2IxY2ZkMWUzNzFmOTQwNzY4ODE2OGQwNDYxNWQ2ZjQ1IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5DbGFpcmxlYSxHb2xkZW4gTWlsZSxPYWtyaWRnZSwgU2NhcmJvcm91Z2g8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2MyOWQzZmU5M2Y1YjRlYTVhODFlYWVjY2I2ZDMxNDBlLnNldENvbnRlbnQoaHRtbF9iMWNmZDFlMzcxZjk0MDc2ODgxNjhkMDQ2MTVkNmY0NSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl83MDdmNjczMDU4OGQ0Zjg4YjJjY2E0MjJiM2VmM2IxZi5iaW5kUG9wdXAocG9wdXBfYzI5ZDNmZTkzZjViNGVhNWE4MWVhZWNjYjZkMzE0MGUpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfZTI3YzE2YmM5YzcxNDI2OTg2OWQ3YTM2OTBlOTU0ODggPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43MTYzMTYsLTc5LjIzOTQ3NjA5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2E3YWVmNDk4YzM0OTRjYjI5ZTliYzNiZjFkMzZhZGI3ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2QwYzk2YWVlMWQyMzRkMTg5ZmI3NGM4OWQ5Yjc3NTFlID0gJCgnPGRpdiBpZD0iaHRtbF9kMGM5NmFlZTFkMjM0ZDE4OWZiNzRjODlkOWI3NzUxZSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Q2xpZmZjcmVzdCxDbGlmZnNpZGUsU2NhcmJvcm91Z2ggVmlsbGFnZSBXZXN0LCBTY2FyYm9yb3VnaDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfYTdhZWY0OThjMzQ5NGNiMjllOWJjM2JmMWQzNmFkYjcuc2V0Q29udGVudChodG1sX2QwYzk2YWVlMWQyMzRkMTg5ZmI3NGM4OWQ5Yjc3NTFlKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2UyN2MxNmJjOWM3MTQyNjk4NjlkN2EzNjkwZTk1NDg4LmJpbmRQb3B1cChwb3B1cF9hN2FlZjQ5OGMzNDk0Y2IyOWU5YmMzYmYxZDM2YWRiNyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9hZjg2ZjhjNDljMTY0ZGQzOTIzMjM1NmRlOGNlZGQ4NyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY5MjY1NzAwMDAwMDAwNCwtNzkuMjY0ODQ4MV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9mYTgzNWVhODkzY2M0MzIzODdjOWNhNjZkNTE0YTU0OSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9jNjgzMTU2ZTFiNzQ0ZTA5YTY5YjViZjllYjMxYjgxZiA9ICQoJzxkaXYgaWQ9Imh0bWxfYzY4MzE1NmUxYjc0NGUwOWE2OWI1YmY5ZWIzMWI4MWYiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkJpcmNoIENsaWZmLENsaWZmc2lkZSBXZXN0LCBTY2FyYm9yb3VnaDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZmE4MzVlYTg5M2NjNDMyMzg3YzljYTY2ZDUxNGE1NDkuc2V0Q29udGVudChodG1sX2M2ODMxNTZlMWI3NDRlMDlhNjliNWJmOWViMzFiODFmKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2FmODZmOGM0OWMxNjRkZDM5MjMyMzU2ZGU4Y2VkZDg3LmJpbmRQb3B1cChwb3B1cF9mYTgzNWVhODkzY2M0MzIzODdjOWNhNjZkNTE0YTU0OSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9mZWFhMzgzNDdjODY0NmVmYmM4YzMxOTVhZDRiYWI0MCA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc1NzQwOTYsLTc5LjI3MzMwNDAwMDAwMDAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzA0ZThiNjk3NGVhYTQ1MmFhNzM4ZTM2NDY2MTgyYjgxID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzg4ZjA5NGE2OWQ5ZjQ1YWFhZjU0ZmYxYjc3MGJlM2E3ID0gJCgnPGRpdiBpZD0iaHRtbF84OGYwOTRhNjlkOWY0NWFhYWY1NGZmMWI3NzBiZTNhNyIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+RG9yc2V0IFBhcmssU2NhcmJvcm91Z2ggVG93biBDZW50cmUsV2V4Zm9yZCBIZWlnaHRzLCBTY2FyYm9yb3VnaDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMDRlOGI2OTc0ZWFhNDUyYWE3MzhlMzY0NjYxODJiODEuc2V0Q29udGVudChodG1sXzg4ZjA5NGE2OWQ5ZjQ1YWFhZjU0ZmYxYjc3MGJlM2E3KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2ZlYWEzODM0N2M4NjQ2ZWZiYzhjMzE5NWFkNGJhYjQwLmJpbmRQb3B1cChwb3B1cF8wNGU4YjY5NzRlYWE0NTJhYTczOGUzNjQ2NjE4MmI4MSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl82N2VkY2JkYjk4NzU0MjdkOTllOGU5NDJkY2Q3YWQ5MiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc1MDA3MTUwMDAwMDAwNCwtNzkuMjk1ODQ5MV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9mNDI2MjlkOTQwYjI0ODdlODNmYzE0M2RlMmIxMTFmZiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF82M2Y4NzY5NDkyNWY0YTI1YjRhYzUwN2M1OWVmODZmZSA9ICQoJzxkaXYgaWQ9Imh0bWxfNjNmODc2OTQ5MjVmNGEyNWI0YWM1MDdjNTllZjg2ZmUiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPk1hcnl2YWxlLFdleGZvcmQsIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9mNDI2MjlkOTQwYjI0ODdlODNmYzE0M2RlMmIxMTFmZi5zZXRDb250ZW50KGh0bWxfNjNmODc2OTQ5MjVmNGEyNWI0YWM1MDdjNTllZjg2ZmUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNjdlZGNiZGI5ODc1NDI3ZDk5ZThlOTQyZGNkN2FkOTIuYmluZFBvcHVwKHBvcHVwX2Y0MjYyOWQ5NDBiMjQ4N2U4M2ZjMTQzZGUyYjExMWZmKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzVmNmE1NGIzMjFmODQwYzA5Zjc5YmJjNDRmYzc5OWJlID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzk0MjAwMywtNzkuMjYyMDI5NDAwMDAwMDJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNDE1MGEyZjQyZjdhNDk2MmFiNjI1MmNmNGEzMjJhNzcgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMTRhYzE2YmViNTYwNGQ5YTk1MzdjOGNlNzg1Y2E2MmQgPSAkKCc8ZGl2IGlkPSJodG1sXzE0YWMxNmJlYjU2MDRkOWE5NTM3YzhjZTc4NWNhNjJkIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5BZ2luY291cnQsIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF80MTUwYTJmNDJmN2E0OTYyYWI2MjUyY2Y0YTMyMmE3Ny5zZXRDb250ZW50KGh0bWxfMTRhYzE2YmViNTYwNGQ5YTk1MzdjOGNlNzg1Y2E2MmQpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNWY2YTU0YjMyMWY4NDBjMDlmNzliYmM0NGZjNzk5YmUuYmluZFBvcHVwKHBvcHVwXzQxNTBhMmY0MmY3YTQ5NjJhYjYyNTJjZjRhMzIyYTc3KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzY0MTM5NmU2ZmRhODQ1YTBiNzIyMzBkNWY0NTRhNWExID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzgxNjM3NSwtNzkuMzA0MzAyMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8zZWE0N2Q3NTY2ZGM0OTRjYTczNTA5OWVhYjI3NzgxNyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF80YjQ4ZjM2OGEwYzY0YTg5YTNlYmMxYzY1ZWQ3MWU5NSA9ICQoJzxkaXYgaWQ9Imh0bWxfNGI0OGYzNjhhMGM2NGE4OWEzZWJjMWM2NWVkNzFlOTUiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNsYXJrcyBDb3JuZXJzLFN1bGxpdmFuLFRhbSBPJiMzOTtTaGFudGVyLCBTY2FyYm9yb3VnaDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfM2VhNDdkNzU2NmRjNDk0Y2E3MzUwOTllYWIyNzc4MTcuc2V0Q29udGVudChodG1sXzRiNDhmMzY4YTBjNjRhODlhM2ViYzFjNjVlZDcxZTk1KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzY0MTM5NmU2ZmRhODQ1YTBiNzIyMzBkNWY0NTRhNWExLmJpbmRQb3B1cChwb3B1cF8zZWE0N2Q3NTY2ZGM0OTRjYTczNTA5OWVhYjI3NzgxNyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8yMGE3NTlkNmYzZTc0ZGYwODUzODNjMDY0YzYxYjQ5NiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjgxNTI1MjIsLTc5LjI4NDU3NzJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfOWUwN2RlN2NkMTFmNDFkYzlmYzhkMTEwNGUxNmVhYzEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYzMxYTk3NzJkZTkzNGU1OTg0MjY5OTU0MzBmOWNhYTUgPSAkKCc8ZGl2IGlkPSJodG1sX2MzMWE5NzcyZGU5MzRlNTk4NDI2OTk1NDMwZjljYWE1IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5BZ2luY291cnQgTm9ydGgsTCYjMzk7QW1vcmVhdXggRWFzdCxNaWxsaWtlbixTdGVlbGVzIEVhc3QsIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF85ZTA3ZGU3Y2QxMWY0MWRjOWZjOGQxMTA0ZTE2ZWFjMS5zZXRDb250ZW50KGh0bWxfYzMxYTk3NzJkZTkzNGU1OTg0MjY5OTU0MzBmOWNhYTUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMjBhNzU5ZDZmM2U3NGRmMDg1MzgzYzA2NGM2MWI0OTYuYmluZFBvcHVwKHBvcHVwXzllMDdkZTdjZDExZjQxZGM5ZmM4ZDExMDRlMTZlYWMxKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2U1ZDhhZTVkNjFkYjQxZDg5OTQ4MDg4Yjg3NmRjYTUzID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzk5NTI1MjAwMDAwMDA1LC03OS4zMTgzODg3XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzdjNWU2MDIxNmI5ZTRmMjU4M2RlYTA5ZmEyNjVjODYzID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzk3Mzk4YTNlY2M1NzRlNzI4ZjY5NjU4MDBjZDEzNWQ5ID0gJCgnPGRpdiBpZD0iaHRtbF85NzM5OGEzZWNjNTc0ZTcyOGY2OTY1ODAwY2QxMzVkOSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+TCYjMzk7QW1vcmVhdXggV2VzdCwgU2NhcmJvcm91Z2g8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzdjNWU2MDIxNmI5ZTRmMjU4M2RlYTA5ZmEyNjVjODYzLnNldENvbnRlbnQoaHRtbF85NzM5OGEzZWNjNTc0ZTcyOGY2OTY1ODAwY2QxMzVkOSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9lNWQ4YWU1ZDYxZGI0MWQ4OTk0ODA4OGI4NzZkY2E1My5iaW5kUG9wdXAocG9wdXBfN2M1ZTYwMjE2YjllNGYyNTgzZGVhMDlmYTI2NWM4NjMpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfZTZhY2Y5NTQwODZkNDQ0YWE0ZTJiOWNiMDlkYzNmOTQgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My44MzYxMjQ3MDAwMDAwMDYsLTc5LjIwNTYzNjA5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzg4ZTE2NjU1MDNlNjQwZjZhOTNlOGNhNDFlMjAyNDUwID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzk1NWUxY2JjNGY3OTQxZWZiYmNiZjBjMTcyNzk1ZGRhID0gJCgnPGRpdiBpZD0iaHRtbF85NTVlMWNiYzRmNzk0MWVmYmJjYmYwYzE3Mjc5NWRkYSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+VXBwZXIgUm91Z2UsIFNjYXJib3JvdWdoPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF84OGUxNjY1NTAzZTY0MGY2YTkzZThjYTQxZTIwMjQ1MC5zZXRDb250ZW50KGh0bWxfOTU1ZTFjYmM0Zjc5NDFlZmJiY2JmMGMxNzI3OTVkZGEpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfZTZhY2Y5NTQwODZkNDQ0YWE0ZTJiOWNiMDlkYzNmOTQuYmluZFBvcHVwKHBvcHVwXzg4ZTE2NjU1MDNlNjQwZjZhOTNlOGNhNDFlMjAyNDUwKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2JkOTU4ZjM2NDAxNTRmNGNhNjJiN2JlNDNlN2IzZWZhID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuODAzNzYyMiwtNzkuMzYzNDUxN10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9lM2JkMjJmZGU0YzA0MWZkOWM1N2I1NmY0YjQyOGNiMSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8yNThmYjA4OGM5NTA0MmE4OWIzNjdiN2MyY2ZlZTc4MiA9ICQoJzxkaXYgaWQ9Imh0bWxfMjU4ZmIwODhjOTUwNDJhODliMzY3YjdjMmNmZWU3ODIiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkhpbGxjcmVzdCBWaWxsYWdlLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9lM2JkMjJmZGU0YzA0MWZkOWM1N2I1NmY0YjQyOGNiMS5zZXRDb250ZW50KGh0bWxfMjU4ZmIwODhjOTUwNDJhODliMzY3YjdjMmNmZWU3ODIpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYmQ5NThmMzY0MDE1NGY0Y2E2MmI3YmU0M2U3YjNlZmEuYmluZFBvcHVwKHBvcHVwX2UzYmQyMmZkZTRjMDQxZmQ5YzU3YjU2ZjRiNDI4Y2IxKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzYzYzYyZjRhMjY3ZjRkZjliMWEwMTA3ZTViMTAwMDhhID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzc4NTE3NSwtNzkuMzQ2NTU1N10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9jMDE3MWUxOGEyNWE0MWIwOTdjZDY0NjAwYzExNDk5NyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8yMWNkN2U2ODcwMDI0ZmNmOWEzZGJlNmMyYzU5NGM1MSA9ICQoJzxkaXYgaWQ9Imh0bWxfMjFjZDdlNjg3MDAyNGZjZjlhM2RiZTZjMmM1OTRjNTEiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkZhaXJ2aWV3LEhlbnJ5IEZhcm0sT3Jpb2xlLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9jMDE3MWUxOGEyNWE0MWIwOTdjZDY0NjAwYzExNDk5Ny5zZXRDb250ZW50KGh0bWxfMjFjZDdlNjg3MDAyNGZjZjlhM2RiZTZjMmM1OTRjNTEpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNjNjNjJmNGEyNjdmNGRmOWIxYTAxMDdlNWIxMDAwOGEuYmluZFBvcHVwKHBvcHVwX2MwMTcxZTE4YTI1YTQxYjA5N2NkNjQ2MDBjMTE0OTk3KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzRlY2I2MWI1OWQ1YTQ0MzRiOWZhNmM3YTNhMDQ0OGMzID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzg2OTQ3MywtNzkuMzg1OTc1XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzZiNThkYWM1ZWQ3YzRkOWJhNzk1ZWM4MTQ2MGY2OTNhID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2UyYjNkMzAyYTY2MjQ5YmViMzRmYTE0NTlmNmU5Y2ZkID0gJCgnPGRpdiBpZD0iaHRtbF9lMmIzZDMwMmE2NjI0OWJlYjM0ZmExNDU5ZjZlOWNmZCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+QmF5dmlldyBWaWxsYWdlLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF82YjU4ZGFjNWVkN2M0ZDliYTc5NWVjODE0NjBmNjkzYS5zZXRDb250ZW50KGh0bWxfZTJiM2QzMDJhNjYyNDliZWIzNGZhMTQ1OWY2ZTljZmQpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNGVjYjYxYjU5ZDVhNDQzNGI5ZmE2YzdhM2EwNDQ4YzMuYmluZFBvcHVwKHBvcHVwXzZiNThkYWM1ZWQ3YzRkOWJhNzk1ZWM4MTQ2MGY2OTNhKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2Q2YTdlYTAzZWY1YzQxMjk5OGM0OGM4OTA0NmIwYTUzID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzU3NDkwMiwtNzkuMzc0NzE0MDk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfYjEzODZhNDljNGIxNDY0OTg4OWRkOTYxM2MyZDk3NGMgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNzg1OGY1NGRiNjdhNDFjZDg3YTg1MDNkYzhkMmUxZTcgPSAkKCc8ZGl2IGlkPSJodG1sXzc4NThmNTRkYjY3YTQxY2Q4N2E4NTAzZGM4ZDJlMWU3IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5TaWx2ZXIgSGlsbHMsWW9yayBNaWxscywgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfYjEzODZhNDljNGIxNDY0OTg4OWRkOTYxM2MyZDk3NGMuc2V0Q29udGVudChodG1sXzc4NThmNTRkYjY3YTQxY2Q4N2E4NTAzZGM4ZDJlMWU3KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2Q2YTdlYTAzZWY1YzQxMjk5OGM0OGM4OTA0NmIwYTUzLmJpbmRQb3B1cChwb3B1cF9iMTM4NmE0OWM0YjE0NjQ5ODg5ZGQ5NjEzYzJkOTc0Yyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8wZGZiMmRmMjMxNGI0YmZjYThkYmEyZmFkOWI0MTk4NiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc4OTA1MywtNzkuNDA4NDkyNzk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMjM4NGNkYTdjYTJiNGRiOTkwOTIxYjlkYzA0YzZkMzUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNTUzNzZmMjIzZDliNDUxNDk0YzY4YWUzMGQ3NDk5ZTMgPSAkKCc8ZGl2IGlkPSJodG1sXzU1Mzc2ZjIyM2Q5YjQ1MTQ5NGM2OGFlMzBkNzQ5OWUzIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5OZXd0b25icm9vayxXaWxsb3dkYWxlLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8yMzg0Y2RhN2NhMmI0ZGI5OTA5MjFiOWRjMDRjNmQzNS5zZXRDb250ZW50KGh0bWxfNTUzNzZmMjIzZDliNDUxNDk0YzY4YWUzMGQ3NDk5ZTMpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMGRmYjJkZjIzMTRiNGJmY2E4ZGJhMmZhZDliNDE5ODYuYmluZFBvcHVwKHBvcHVwXzIzODRjZGE3Y2EyYjRkYjk5MDkyMWI5ZGMwNGM2ZDM1KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2UwNGViYTFiNTMwMjQ1YTZiZTRkNzE1YjRlNWNmZTExID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzcwMTE5OSwtNzkuNDA4NDkyNzk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZWI4YjFlZjMzMDgwNDRjOTgyYjMwZTk4ZjFmYmI2MmQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZWIwZTEwMTMxN2E0NGI0OTg1OTA1MzVhZTA1OGNiZTQgPSAkKCc8ZGl2IGlkPSJodG1sX2ViMGUxMDEzMTdhNDRiNDk4NTkwNTM1YWUwNThjYmU0IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5XaWxsb3dkYWxlIFNvdXRoLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9lYjhiMWVmMzMwODA0NGM5ODJiMzBlOThmMWZiYjYyZC5zZXRDb250ZW50KGh0bWxfZWIwZTEwMTMxN2E0NGI0OTg1OTA1MzVhZTA1OGNiZTQpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfZTA0ZWJhMWI1MzAyNDVhNmJlNGQ3MTViNGU1Y2ZlMTEuYmluZFBvcHVwKHBvcHVwX2ViOGIxZWYzMzA4MDQ0Yzk4MmIzMGU5OGYxZmJiNjJkKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2JjZWEzY2U1OGVhZDQ5MGZiYWE4MzAzNGM5YzkzNThjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzUyNzU4Mjk5OTk5OTk2LC03OS40MDAwNDkzXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2M1N2VjNDY4ODIyMTQ5OTY4NmJmMzUwYjAwYTNiN2QxID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzc1MjE0OTE4NDgxMzQzZWE4ZTI1MjA5ODJjZDA0ZjY3ID0gJCgnPGRpdiBpZD0iaHRtbF83NTIxNDkxODQ4MTM0M2VhOGUyNTIwOTgyY2QwNGY2NyIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+WW9yayBNaWxscyBXZXN0LCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9jNTdlYzQ2ODgyMjE0OTk2ODZiZjM1MGIwMGEzYjdkMS5zZXRDb250ZW50KGh0bWxfNzUyMTQ5MTg0ODEzNDNlYThlMjUyMDk4MmNkMDRmNjcpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYmNlYTNjZTU4ZWFkNDkwZmJhYTgzMDM0YzljOTM1OGMuYmluZFBvcHVwKHBvcHVwX2M1N2VjNDY4ODIyMTQ5OTY4NmJmMzUwYjAwYTNiN2QxKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2IxODQ5OTg0N2I2ZDRhZTNhYTBkMzc4ZWNlMjgyYzI1ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzgyNzM2NCwtNzkuNDQyMjU5M10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8zMmY3ZjZmNGEzMzQ0MjZlOTNmYTllZjM0NDIxMWFkYiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9jY2E5YWFhYjcwZTA0NjI2OTcxZjEyNzRmMmY1MDFiYiA9ICQoJzxkaXYgaWQ9Imh0bWxfY2NhOWFhYWI3MGUwNDYyNjk3MWYxMjc0ZjJmNTAxYmIiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPldpbGxvd2RhbGUgV2VzdCwgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMzJmN2Y2ZjRhMzM0NDI2ZTkzZmE5ZWYzNDQyMTFhZGIuc2V0Q29udGVudChodG1sX2NjYTlhYWFiNzBlMDQ2MjY5NzFmMTI3NGYyZjUwMWJiKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2IxODQ5OTg0N2I2ZDRhZTNhYTBkMzc4ZWNlMjgyYzI1LmJpbmRQb3B1cChwb3B1cF8zMmY3ZjZmNGEzMzQ0MjZlOTNmYTllZjM0NDIxMWFkYik7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8zMTg0YTczYmI3NWY0YjVjYjk3NTUyYWJmMThmZTQ5NSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc1MzI1ODYsLTc5LjMyOTY1NjVdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfYTU2N2FiYmQ4M2IyNDRmN2FlZTQyYWMzYzM5MjRhZjAgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMDMyM2I1NTZjMzQyNDZkNmIwNDFhYzY3OGI0ZjIyOTQgPSAkKCc8ZGl2IGlkPSJodG1sXzAzMjNiNTU2YzM0MjQ2ZDZiMDQxYWM2NzhiNGYyMjk0IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5QYXJrd29vZHMsIE5vcnRoIFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2E1NjdhYmJkODNiMjQ0ZjdhZWU0MmFjM2MzOTI0YWYwLnNldENvbnRlbnQoaHRtbF8wMzIzYjU1NmMzNDI0NmQ2YjA0MWFjNjc4YjRmMjI5NCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8zMTg0YTczYmI3NWY0YjVjYjk3NTUyYWJmMThmZTQ5NS5iaW5kUG9wdXAocG9wdXBfYTU2N2FiYmQ4M2IyNDRmN2FlZTQyYWMzYzM5MjRhZjApOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfNWJlYzczNmY0ZDljNDg0YjgwMzY0NjlmNGZmYjdjOTYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43NDU5MDU3OTk5OTk5OTYsLTc5LjM1MjE4OF0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9mZGE1ZGMyMjdkMjc0NjM4YjNkMGY4ZmRlODU1MTYzMyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9mMDY4MjA3NDgzZmQ0ZWZhODQxYzM1YjhmOGJmYzc5NiA9ICQoJzxkaXYgaWQ9Imh0bWxfZjA2ODIwNzQ4M2ZkNGVmYTg0MWMzNWI4ZjhiZmM3OTYiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkRvbiBNaWxscyBOb3J0aCwgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZmRhNWRjMjI3ZDI3NDYzOGIzZDBmOGZkZTg1NTE2MzMuc2V0Q29udGVudChodG1sX2YwNjgyMDc0ODNmZDRlZmE4NDFjMzViOGY4YmZjNzk2KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzViZWM3MzZmNGQ5YzQ4NGI4MDM2NDY5ZjRmZmI3Yzk2LmJpbmRQb3B1cChwb3B1cF9mZGE1ZGMyMjdkMjc0NjM4YjNkMGY4ZmRlODU1MTYzMyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9mODU3MTA4N2JiYTU0NDM2OTVlN2YyODQyNDhhNjQ3NyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcyNTg5OTcwMDAwMDAxLC03OS4zNDA5MjNdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfYTQ4NmJjYzYzMDI4NGI0Njk1ODJlODliZDgyNDFlYWQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMjY4MzM1MTUzN2ViNDVjZmJlMTgwMTBmNGVkYmNmOGMgPSAkKCc8ZGl2IGlkPSJodG1sXzI2ODMzNTE1MzdlYjQ1Y2ZiZTE4MDEwZjRlZGJjZjhjIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5GbGVtaW5nZG9uIFBhcmssRG9uIE1pbGxzIFNvdXRoLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9hNDg2YmNjNjMwMjg0YjQ2OTU4MmU4OWJkODI0MWVhZC5zZXRDb250ZW50KGh0bWxfMjY4MzM1MTUzN2ViNDVjZmJlMTgwMTBmNGVkYmNmOGMpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfZjg1NzEwODdiYmE1NDQzNjk1ZTdmMjg0MjQ4YTY0NzcuYmluZFBvcHVwKHBvcHVwX2E0ODZiY2M2MzAyODRiNDY5NTgyZTg5YmQ4MjQxZWFkKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2YyNTkwMDE3ZjkwNzRlNWM4ZDM5ODUwYTQzMzk0MWM5ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzU0MzI4MywtNzkuNDQyMjU5M10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9iZDc5OWI2YjFiY2U0MjIwOThmN2ZmYTE3ODMyOGJlYSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF85NjRlNjNkYjMxMDI0NmU5YjIxMzk3ZTM0OTJhMWI5NyA9ICQoJzxkaXYgaWQ9Imh0bWxfOTY0ZTYzZGIzMTAyNDZlOWIyMTM5N2UzNDkyYTFiOTciIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkJhdGh1cnN0IE1hbm9yLERvd25zdmlldyBOb3J0aCxXaWxzb24gSGVpZ2h0cywgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfYmQ3OTliNmIxYmNlNDIyMDk4ZjdmZmExNzgzMjhiZWEuc2V0Q29udGVudChodG1sXzk2NGU2M2RiMzEwMjQ2ZTliMjEzOTdlMzQ5MmExYjk3KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2YyNTkwMDE3ZjkwNzRlNWM4ZDM5ODUwYTQzMzk0MWM5LmJpbmRQb3B1cChwb3B1cF9iZDc5OWI2YjFiY2U0MjIwOThmN2ZmYTE3ODMyOGJlYSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl85NTU2MGMwNzBmZTk0OWQ2ODZkYzdmZmU1OTgxNWYxNSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc2Nzk4MDMsLTc5LjQ4NzI2MTkwMDAwMDAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzY4ZDk1OTUyMTkxMTQxZGZhNzdkMTZmZWM1YjRlNzBiID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2EyNDdiMjhkNDkzOTRlZjViZWQ2ZDk0ODI4YTQwY2RlID0gJCgnPGRpdiBpZD0iaHRtbF9hMjQ3YjI4ZDQ5Mzk0ZWY1YmVkNmQ5NDgyOGE0MGNkZSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Tm9ydGh3b29kIFBhcmssWW9yayBVbml2ZXJzaXR5LCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF82OGQ5NTk1MjE5MTE0MWRmYTc3ZDE2ZmVjNWI0ZTcwYi5zZXRDb250ZW50KGh0bWxfYTI0N2IyOGQ0OTM5NGVmNWJlZDZkOTQ4MjhhNDBjZGUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfOTU1NjBjMDcwZmU5NDlkNjg2ZGM3ZmZlNTk4MTVmMTUuYmluZFBvcHVwKHBvcHVwXzY4ZDk1OTUyMTkxMTQxZGZhNzdkMTZmZWM1YjRlNzBiKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzYzODNkNjU0ODNjMDQyODQ5M2VhNWJmNzljYWUzN2ZmID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzM3NDczMjAwMDAwMDA0LC03OS40NjQ3NjMyOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9iOGQyYTU4MjQzMDA0ZWNjOGUzNDBkNTBkMGFkMmU0NCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF81YmNlOGVmZWM5NjA0NzdlODBlM2EwMzdjYjk4OWE2MiA9ICQoJzxkaXYgaWQ9Imh0bWxfNWJjZThlZmVjOTYwNDc3ZTgwZTNhMDM3Y2I5ODlhNjIiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNGQiBUb3JvbnRvLERvd25zdmlldyBFYXN0LCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9iOGQyYTU4MjQzMDA0ZWNjOGUzNDBkNTBkMGFkMmU0NC5zZXRDb250ZW50KGh0bWxfNWJjZThlZmVjOTYwNDc3ZTgwZTNhMDM3Y2I5ODlhNjIpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNjM4M2Q2NTQ4M2MwNDI4NDkzZWE1YmY3OWNhZTM3ZmYuYmluZFBvcHVwKHBvcHVwX2I4ZDJhNTgyNDMwMDRlY2M4ZTM0MGQ1MGQwYWQyZTQ0KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzAxM2YxNjJhOTdlNzQyNjg5ZmI4NzAyODAwZGY5YTY5ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzM5MDE0NiwtNzkuNTA2OTQzNl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9hODFhYTg2NGJkNWE0Nzk0ODViMjA4NDcyMzI5Yzc0YiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF80OWFlN2YzOGRjY2I0MGExYTQwYzhlMzJkNWM5ZmVkYyA9ICQoJzxkaXYgaWQ9Imh0bWxfNDlhZTdmMzhkY2NiNDBhMWE0MGM4ZTMyZDVjOWZlZGMiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkRvd25zdmlldyBXZXN0LCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9hODFhYTg2NGJkNWE0Nzk0ODViMjA4NDcyMzI5Yzc0Yi5zZXRDb250ZW50KGh0bWxfNDlhZTdmMzhkY2NiNDBhMWE0MGM4ZTMyZDVjOWZlZGMpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMDEzZjE2MmE5N2U3NDI2ODlmYjg3MDI4MDBkZjlhNjkuYmluZFBvcHVwKHBvcHVwX2E4MWFhODY0YmQ1YTQ3OTQ4NWIyMDg0NzIzMjljNzRiKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2Q2YzIzMWIzMjVkMjQ3OGY5YWJhZTczYTM3MWYwM2RiID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzI4NDk2NCwtNzkuNDk1Njk3NDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMDhlZGM2NDM0MTdhNDZjYzhjZGEzNWE3MDJhZTk0YjcgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNTZmYzRkMTViYjY1NDJmMWI2Y2YzZDNlZWEyOTUyZTAgPSAkKCc8ZGl2IGlkPSJodG1sXzU2ZmM0ZDE1YmI2NTQyZjFiNmNmM2QzZWVhMjk1MmUwIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Eb3duc3ZpZXcgQ2VudHJhbCwgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMDhlZGM2NDM0MTdhNDZjYzhjZGEzNWE3MDJhZTk0Yjcuc2V0Q29udGVudChodG1sXzU2ZmM0ZDE1YmI2NTQyZjFiNmNmM2QzZWVhMjk1MmUwKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2Q2YzIzMWIzMjVkMjQ3OGY5YWJhZTczYTM3MWYwM2RiLmJpbmRQb3B1cChwb3B1cF8wOGVkYzY0MzQxN2E0NmNjOGNkYTM1YTcwMmFlOTRiNyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl81NWNjMTk4NTNmNmI0ZWU1OWQ5YWExMGE1MzE1YjNiNSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc2MTYzMTMsLTc5LjUyMDk5OTQwMDAwMDAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzA0NzQ2ZDA4NDliZTQwMTZiZmU4M2FjYTkwM2VlYTY5ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzZlYzhkMDUzNWI4YTRlMDE4YTI3MmEzNTI2YmZkMzExID0gJCgnPGRpdiBpZD0iaHRtbF82ZWM4ZDA1MzViOGE0ZTAxOGEyNzJhMzUyNmJmZDMxMSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+RG93bnN2aWV3IE5vcnRod2VzdCwgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMDQ3NDZkMDg0OWJlNDAxNmJmZTgzYWNhOTAzZWVhNjkuc2V0Q29udGVudChodG1sXzZlYzhkMDUzNWI4YTRlMDE4YTI3MmEzNTI2YmZkMzExKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzU1Y2MxOTg1M2Y2YjRlZTU5ZDlhYTEwYTUzMTViM2I1LmJpbmRQb3B1cChwb3B1cF8wNDc0NmQwODQ5YmU0MDE2YmZlODNhY2E5MDNlZWE2OSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl82ZWE3NTBlZjM5YzY0NTY5YTU3Y2MzZDNlYjQ2YTk2YSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcyNTg4MjI5OTk5OTk5NSwtNzkuMzE1NTcxNTk5OTk5OThdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfY2FjNTE3ODAzMGIzNDA3Yjg5Njc5MDU5MzI5ODljNWIgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYzFhOTg2ODFmY2QyNDE5N2FhZjhmMzVhOGRhYmNjMDUgPSAkKCc8ZGl2IGlkPSJodG1sX2MxYTk4NjgxZmNkMjQxOTdhYWY4ZjM1YThkYWJjYzA1IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5WaWN0b3JpYSBWaWxsYWdlLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9jYWM1MTc4MDMwYjM0MDdiODk2NzkwNTkzMjk4OWM1Yi5zZXRDb250ZW50KGh0bWxfYzFhOTg2ODFmY2QyNDE5N2FhZjhmMzVhOGRhYmNjMDUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNmVhNzUwZWYzOWM2NDU2OWE1N2NjM2QzZWI0NmE5NmEuYmluZFBvcHVwKHBvcHVwX2NhYzUxNzgwMzBiMzQwN2I4OTY3OTA1OTMyOTg5YzViKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzhhODYzZjk5NDdlNzRiZGU4MDM3MjhmMjhjYWUwYzI5ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzA2Mzk3MiwtNzkuMzA5OTM3XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2JjOTMyZWE2NTY1MzQ3MmFhM2IxODVjZmY5MDJiMjNmID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzc3NjViNTFhOWZkZTRhYWJiODk0ZGQyOTY5NmQxNjM5ID0gJCgnPGRpdiBpZD0iaHRtbF83NzY1YjUxYTlmZGU0YWFiYjg5NGRkMjk2OTZkMTYzOSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+V29vZGJpbmUgR2FyZGVucyxQYXJrdmlldyBIaWxsLCBFYXN0IFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2JjOTMyZWE2NTY1MzQ3MmFhM2IxODVjZmY5MDJiMjNmLnNldENvbnRlbnQoaHRtbF83NzY1YjUxYTlmZGU0YWFiYjg5NGRkMjk2OTZkMTYzOSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl84YTg2M2Y5OTQ3ZTc0YmRlODAzNzI4ZjI4Y2FlMGMyOS5iaW5kUG9wdXAocG9wdXBfYmM5MzJlYTY1NjUzNDcyYWEzYjE4NWNmZjkwMmIyM2YpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfYjU4YTgxZDI0MDkwNGI3MTlhNTZhYWE1ZGE0MzcyM2UgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42OTUzNDM5MDAwMDAwMDUsLTc5LjMxODM4ODddLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfYjE1OTNmZGNlMTgwNDRkYTlkZTA4YzQ0NTI1MDMzN2YgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfOThlZjVmNmI1NzQzNDRiMWE1NmQ3MjQ1YTdmMzljMmIgPSAkKCc8ZGl2IGlkPSJodG1sXzk4ZWY1ZjZiNTc0MzQ0YjFhNTZkNzI0NWE3ZjM5YzJiIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Xb29kYmluZSBIZWlnaHRzLCBFYXN0IFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2IxNTkzZmRjZTE4MDQ0ZGE5ZGUwOGM0NDUyNTAzMzdmLnNldENvbnRlbnQoaHRtbF85OGVmNWY2YjU3NDM0NGIxYTU2ZDcyNDVhN2YzOWMyYik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9iNThhODFkMjQwOTA0YjcxOWE1NmFhYTVkYTQzNzIzZS5iaW5kUG9wdXAocG9wdXBfYjE1OTNmZGNlMTgwNDRkYTlkZTA4YzQ0NTI1MDMzN2YpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfNWE4YjMyM2Y1NDE3NDg0ZGExNGU1MGM2YTZhZDJjMDEgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NzYzNTczOTk5OTk5OSwtNzkuMjkzMDMxMl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF81ZDJiZDQ3NTM5NzQ0ZTg1ODY0ZTkzNWZkMjY0NjhlNCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF82NjJjZDgzOWRiMjQ0MjRjYmI5OGVmN2I0OTA5MTMwYyA9ICQoJzxkaXYgaWQ9Imh0bWxfNjYyY2Q4MzlkYjI0NDI0Y2JiOThlZjdiNDkwOTEzMGMiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlRoZSBCZWFjaGVzLCBFYXN0IFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzVkMmJkNDc1Mzk3NDRlODU4NjRlOTM1ZmQyNjQ2OGU0LnNldENvbnRlbnQoaHRtbF82NjJjZDgzOWRiMjQ0MjRjYmI5OGVmN2I0OTA5MTMwYyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl81YThiMzIzZjU0MTc0ODRkYTE0ZTUwYzZhNmFkMmMwMS5iaW5kUG9wdXAocG9wdXBfNWQyYmQ0NzUzOTc0NGU4NTg2NGU5MzVmZDI2NDY4ZTQpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfZGQ2MjkxODlkZGRlNGY2Mjk0NzE3NGYxYTkxMDNlOGYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43MDkwNjA0LC03OS4zNjM0NTE3XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzRmYzQwZjQ0OWIyODQxYmI4ZWJlZjYyNTNmYzllNTE1ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzRhNGIxZDZiN2E4NTQ0NDg4NTU1YjFkMjEyMzBmNDM3ID0gJCgnPGRpdiBpZD0iaHRtbF80YTRiMWQ2YjdhODU0NDQ4ODU1NWIxZDIxMjMwZjQzNyIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+TGVhc2lkZSwgRWFzdCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF80ZmM0MGY0NDliMjg0MWJiOGViZWY2MjUzZmM5ZTUxNS5zZXRDb250ZW50KGh0bWxfNGE0YjFkNmI3YTg1NDQ0ODg1NTViMWQyMTIzMGY0MzcpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfZGQ2MjkxODlkZGRlNGY2Mjk0NzE3NGYxYTkxMDNlOGYuYmluZFBvcHVwKHBvcHVwXzRmYzQwZjQ0OWIyODQxYmI4ZWJlZjYyNTNmYzllNTE1KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzYzNWUzY2RkM2RiMDRjNWViZmNjOTg5MTRlZTBhMDU4ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzA1MzY4OSwtNzkuMzQ5MzcxOTAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNTMzOTJkMjYzYjg2NDUwMmIyN2VhZDVhODVkMzAxNTUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMWJkMDE4NWZmZTAzNGZkNmJkMGRjOTNjMGQ1MGY5MTEgPSAkKCc8ZGl2IGlkPSJodG1sXzFiZDAxODVmZmUwMzRmZDZiZDBkYzkzYzBkNTBmOTExIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5UaG9ybmNsaWZmZSBQYXJrLCBFYXN0IFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzUzMzkyZDI2M2I4NjQ1MDJiMjdlYWQ1YTg1ZDMwMTU1LnNldENvbnRlbnQoaHRtbF8xYmQwMTg1ZmZlMDM0ZmQ2YmQwZGM5M2MwZDUwZjkxMSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl82MzVlM2NkZDNkYjA0YzVlYmZjYzk4OTE0ZWUwYTA1OC5iaW5kUG9wdXAocG9wdXBfNTMzOTJkMjYzYjg2NDUwMmIyN2VhZDVhODVkMzAxNTUpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfNjJkNjBkMjFhNjJmNDQ1OWFiODA1NWE1MThkZTA3MjkgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42ODUzNDcsLTc5LjMzODEwNjVdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZTI0ODdkYTQ0MjVkNDI5OWFhZjYzODBkOTMxNTEwZjkgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNTY2MWY0ODYyNzhjNGM4ZmE1YWE3ZTdlYzBiZTcxMGMgPSAkKCc8ZGl2IGlkPSJodG1sXzU2NjFmNDg2Mjc4YzRjOGZhNWFhN2U3ZWMwYmU3MTBjIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5FYXN0IFRvcm9udG8sIEVhc3QgWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZTI0ODdkYTQ0MjVkNDI5OWFhZjYzODBkOTMxNTEwZjkuc2V0Q29udGVudChodG1sXzU2NjFmNDg2Mjc4YzRjOGZhNWFhN2U3ZWMwYmU3MTBjKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzYyZDYwZDIxYTYyZjQ0NTlhYjgwNTVhNTE4ZGUwNzI5LmJpbmRQb3B1cChwb3B1cF9lMjQ4N2RhNDQyNWQ0Mjk5YWFmNjM4MGQ5MzE1MTBmOSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl81N2EzMTA0NzgyMTI0NzkyYmI1ODJlMTZkYmE0OGY1ZSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY3OTU1NzEsLTc5LjM1MjE4OF0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9jYTY0ZGE2NWIyOTQ0MWMxOTlhYzQ1ZmU5YjMxMWJhNyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8xN2Y4ODM3MzgwNDI0ZGQzOGI2ZDI4YzkyZjFiODUzNyA9ICQoJzxkaXYgaWQ9Imh0bWxfMTdmODgzNzM4MDQyNGRkMzhiNmQyOGM5MmYxYjg1MzciIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlRoZSBEYW5mb3J0aCBXZXN0LFJpdmVyZGFsZSwgRWFzdCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9jYTY0ZGE2NWIyOTQ0MWMxOTlhYzQ1ZmU5YjMxMWJhNy5zZXRDb250ZW50KGh0bWxfMTdmODgzNzM4MDQyNGRkMzhiNmQyOGM5MmYxYjg1MzcpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNTdhMzEwNDc4MjEyNDc5MmJiNTgyZTE2ZGJhNDhmNWUuYmluZFBvcHVwKHBvcHVwX2NhNjRkYTY1YjI5NDQxYzE5OWFjNDVmZTliMzExYmE3KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzIxYTRiM2Y2Yzk5ODQ3ZmZhNjY1OTY5NGJkZTA0NjhiID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjY4OTk4NSwtNzkuMzE1NTcxNTk5OTk5OThdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfOWU3YzViNDg0ZTFiNDY4MDg2Zjg4ZTI4ZjMwYjg3OTAgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNWEwOGNjYjc4YTA2NDM2MTgxOWQ0OGQxZjJhM2RhYWUgPSAkKCc8ZGl2IGlkPSJodG1sXzVhMDhjY2I3OGEwNjQzNjE4MTlkNDhkMWYyYTNkYWFlIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5UaGUgQmVhY2hlcyBXZXN0LEluZGlhIEJhemFhciwgRWFzdCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF85ZTdjNWI0ODRlMWI0NjgwODZmODhlMjhmMzBiODc5MC5zZXRDb250ZW50KGh0bWxfNWEwOGNjYjc4YTA2NDM2MTgxOWQ0OGQxZjJhM2RhYWUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMjFhNGIzZjZjOTk4NDdmZmE2NjU5Njk0YmRlMDQ2OGIuYmluZFBvcHVwKHBvcHVwXzllN2M1YjQ4NGUxYjQ2ODA4NmY4OGUyOGYzMGI4NzkwKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzk5MGI1NzU1YWM5YzQ5NGRhZGVmMDhhNDYxMTE1M2ZlID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjU5NTI1NSwtNzkuMzQwOTIzXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzE0OTQ2MDI2ZTMxMTRhZTg4ZTYwMDQzNDk5ZDgxZmNkID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzI3ZWVjYmFkZGRjMTQ2NTZiMWNmZTdiNjI2YjYyZWMyID0gJCgnPGRpdiBpZD0iaHRtbF8yN2VlY2JhZGRkYzE0NjU2YjFjZmU3YjYyNmI2MmVjMiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+U3R1ZGlvIERpc3RyaWN0LCBFYXN0IFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzE0OTQ2MDI2ZTMxMTRhZTg4ZTYwMDQzNDk5ZDgxZmNkLnNldENvbnRlbnQoaHRtbF8yN2VlY2JhZGRkYzE0NjU2YjFjZmU3YjYyNmI2MmVjMik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl85OTBiNTc1NWFjOWM0OTRkYWRlZjA4YTQ2MTExNTNmZS5iaW5kUG9wdXAocG9wdXBfMTQ5NDYwMjZlMzExNGFlODhlNjAwNDM0OTlkODFmY2QpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfY2EzMGJiMzhhMjQwNGZiZWJlMDlhMDY1N2NiOGU2OTUgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43MjgwMjA1LC03OS4zODg3OTAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2FhZjBmNjI4ZDM2YjRhZmE5ZjUxNDkxYzg5YjZiMjY2ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzc4ZmQzYzA5YjIyOTRiODA5Yjg4MzJkZjcwODRmODc0ID0gJCgnPGRpdiBpZD0iaHRtbF83OGZkM2MwOWIyMjk0YjgwOWI4ODMyZGY3MDg0Zjg3NCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+TGF3cmVuY2UgUGFyaywgQ2VudHJhbCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9hYWYwZjYyOGQzNmI0YWZhOWY1MTQ5MWM4OWI2YjI2Ni5zZXRDb250ZW50KGh0bWxfNzhmZDNjMDliMjI5NGI4MDliODgzMmRmNzA4NGY4NzQpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfY2EzMGJiMzhhMjQwNGZiZWJlMDlhMDY1N2NiOGU2OTUuYmluZFBvcHVwKHBvcHVwX2FhZjBmNjI4ZDM2YjRhZmE5ZjUxNDkxYzg5YjZiMjY2KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2I5NDNkMzQ5ZjY0MzQ3MTk5N2FlY2YwMmI1MTMzZmUyID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzEyNzUxMSwtNzkuMzkwMTk3NV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9jZWRmMDg0NzFlMWM0NDYwYmY4YzYyYTZkMzc5MzFmYSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8wYzAzZjY4ZjUwMWM0MjUzOTZmYTUyNTNhZTcwMzkzYiA9ICQoJzxkaXYgaWQ9Imh0bWxfMGMwM2Y2OGY1MDFjNDI1Mzk2ZmE1MjUzYWU3MDM5M2IiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkRhdmlzdmlsbGUgTm9ydGgsIENlbnRyYWwgVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfY2VkZjA4NDcxZTFjNDQ2MGJmOGM2MmE2ZDM3OTMxZmEuc2V0Q29udGVudChodG1sXzBjMDNmNjhmNTAxYzQyNTM5NmZhNTI1M2FlNzAzOTNiKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2I5NDNkMzQ5ZjY0MzQ3MTk5N2FlY2YwMmI1MTMzZmUyLmJpbmRQb3B1cChwb3B1cF9jZWRmMDg0NzFlMWM0NDYwYmY4YzYyYTZkMzc5MzFmYSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl85MzA4MzMzZDEwNmM0YzQ1YTFkNzFjMjgyMzVlZTc3NyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcxNTM4MzQsLTc5LjQwNTY3ODQwMDAwMDAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzYxOTJkYTQzNDc4NzQxOGM5ZmY3NjlmZjI1MjY1MTM1ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzUwODQyZjAzMmVhZTQxMjFhYmMzMmJhNzY4YzUzMTE4ID0gJCgnPGRpdiBpZD0iaHRtbF81MDg0MmYwMzJlYWU0MTIxYWJjMzJiYTc2OGM1MzExOCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Tm9ydGggVG9yb250byBXZXN0LCBDZW50cmFsIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzYxOTJkYTQzNDc4NzQxOGM5ZmY3NjlmZjI1MjY1MTM1LnNldENvbnRlbnQoaHRtbF81MDg0MmYwMzJlYWU0MTIxYWJjMzJiYTc2OGM1MzExOCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl85MzA4MzMzZDEwNmM0YzQ1YTFkNzFjMjgyMzVlZTc3Ny5iaW5kUG9wdXAocG9wdXBfNjE5MmRhNDM0Nzg3NDE4YzlmZjc2OWZmMjUyNjUxMzUpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfMzJjNjFlMDA3NzVmNDE5Mjg4MjQ4OTE1YmQyMzkzMTIgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43MDQzMjQ0LC03OS4zODg3OTAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2E0YTRkNWJmNzRlZjRkMmE5ZTYzZmJmNDI4MjVjYzdmID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2FhYjFmNTdiNThmNjQwZDdhNTRhM2RiM2I2NjU2MTA0ID0gJCgnPGRpdiBpZD0iaHRtbF9hYWIxZjU3YjU4ZjY0MGQ3YTU0YTNkYjNiNjY1NjEwNCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+RGF2aXN2aWxsZSwgQ2VudHJhbCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9hNGE0ZDViZjc0ZWY0ZDJhOWU2M2ZiZjQyODI1Y2M3Zi5zZXRDb250ZW50KGh0bWxfYWFiMWY1N2I1OGY2NDBkN2E1NGEzZGIzYjY2NTYxMDQpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMzJjNjFlMDA3NzVmNDE5Mjg4MjQ4OTE1YmQyMzkzMTIuYmluZFBvcHVwKHBvcHVwX2E0YTRkNWJmNzRlZjRkMmE5ZTYzZmJmNDI4MjVjYzdmKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzgwMjc1ZGJmYWI0ZTQzNThhYjY1NTBmMTI4N2M2MjMwID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjg5NTc0MywtNzkuMzgzMTU5OTAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZjFiZDEwOGMzM2FlNGQ2MDliMjEzN2E0NmJhNDFlOWYgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMDk4ZTFmYjU3NjE0NGVmMDg0MmU5M2JhNzQ1MjcxZGUgPSAkKCc8ZGl2IGlkPSJodG1sXzA5OGUxZmI1NzYxNDRlZjA4NDJlOTNiYTc0NTI3MWRlIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Nb29yZSBQYXJrLFN1bW1lcmhpbGwgRWFzdCwgQ2VudHJhbCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9mMWJkMTA4YzMzYWU0ZDYwOWIyMTM3YTQ2YmE0MWU5Zi5zZXRDb250ZW50KGh0bWxfMDk4ZTFmYjU3NjE0NGVmMDg0MmU5M2JhNzQ1MjcxZGUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfODAyNzVkYmZhYjRlNDM1OGFiNjU1MGYxMjg3YzYyMzAuYmluZFBvcHVwKHBvcHVwX2YxYmQxMDhjMzNhZTRkNjA5YjIxMzdhNDZiYTQxZTlmKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzEwNDJjNzExM2UzYzRjYTRiZDFjMGJjNDQwZjlhMDg2ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjg2NDEyMjk5OTk5OTksLTc5LjQwMDA0OTNdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNDAxMzQzZTVlMjY2NGYxMmI5NDU4NTQzYzkyNGNiN2MgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMzk0OGQ4MzdlZDg0NDFkYjlhMWNjN2NhMDY3MjkzMjMgPSAkKCc8ZGl2IGlkPSJodG1sXzM5NDhkODM3ZWQ4NDQxZGI5YTFjYzdjYTA2NzI5MzIzIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5EZWVyIFBhcmssRm9yZXN0IEhpbGwgU0UsUmF0aG5lbGx5LFNvdXRoIEhpbGwsU3VtbWVyaGlsbCBXZXN0LCBDZW50cmFsIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzQwMTM0M2U1ZTI2NjRmMTJiOTQ1ODU0M2M5MjRjYjdjLnNldENvbnRlbnQoaHRtbF8zOTQ4ZDgzN2VkODQ0MWRiOWExY2M3Y2EwNjcyOTMyMyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8xMDQyYzcxMTNlM2M0Y2E0YmQxYzBiYzQ0MGY5YTA4Ni5iaW5kUG9wdXAocG9wdXBfNDAxMzQzZTVlMjY2NGYxMmI5NDU4NTQzYzkyNGNiN2MpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfZTEzNDdiODhhN2ZjNDdhNGE1NmI5YTcwMTIzNjE0MzEgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42Nzk1NjI2LC03OS4zNzc1Mjk0MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8wZTRhM2ExNzRkOGI0ZjE1YjgxNDljMGUzMjcyMmY2NSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF83NDliZDdmMmFiNjE0YThjYmU3OTE5N2EyMzYxNmQzZCA9ICQoJzxkaXYgaWQ9Imh0bWxfNzQ5YmQ3ZjJhYjYxNGE4Y2JlNzkxOTdhMjM2MTZkM2QiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlJvc2VkYWxlLCBEb3dudG93biBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8wZTRhM2ExNzRkOGI0ZjE1YjgxNDljMGUzMjcyMmY2NS5zZXRDb250ZW50KGh0bWxfNzQ5YmQ3ZjJhYjYxNGE4Y2JlNzkxOTdhMjM2MTZkM2QpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfZTEzNDdiODhhN2ZjNDdhNGE1NmI5YTcwMTIzNjE0MzEuYmluZFBvcHVwKHBvcHVwXzBlNGEzYTE3NGQ4YjRmMTViODE0OWMwZTMyNzIyZjY1KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2M5NzE4ZWNiNTU2NjQyYjg5MjQ2YTdjZDhjYTkxYjczID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjY3OTY3LC03OS4zNjc2NzUzXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzlhYTllZWViMWIyOTRkZGNhMTU4ODljMmY3ZDQzOWEzID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2IxZjY1NDY0OWUwZjRjYWRhNDVjZjVmYWM5M2NhNTliID0gJCgnPGRpdiBpZD0iaHRtbF9iMWY2NTQ2NDllMGY0Y2FkYTQ1Y2Y1ZmFjOTNjYTU5YiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Q2FiYmFnZXRvd24sU3QuIEphbWVzIFRvd24sIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzlhYTllZWViMWIyOTRkZGNhMTU4ODljMmY3ZDQzOWEzLnNldENvbnRlbnQoaHRtbF9iMWY2NTQ2NDllMGY0Y2FkYTQ1Y2Y1ZmFjOTNjYTU5Yik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9jOTcxOGVjYjU1NjY0MmI4OTI0NmE3Y2Q4Y2E5MWI3My5iaW5kUG9wdXAocG9wdXBfOWFhOWVlZWIxYjI5NGRkY2ExNTg4OWMyZjdkNDM5YTMpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfMDM0Y2VhZTQyYzg2NGYwNDhhYWQ2MWI2ZWQ0YjUzZDYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NjU4NTk5LC03OS4zODMxNTk5MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF81ODI3NTk5NGRhMjI0NTM4OGQ1ZmNlM2VmYjY2NDhmMCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8xMDRmNWM2ZjdhNmM0NGZlYTgwMTliMmEyNDRkNjU3NSA9ICQoJzxkaXYgaWQ9Imh0bWxfMTA0ZjVjNmY3YTZjNDRmZWE4MDE5YjJhMjQ0ZDY1NzUiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNodXJjaCBhbmQgV2VsbGVzbGV5LCBEb3dudG93biBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF81ODI3NTk5NGRhMjI0NTM4OGQ1ZmNlM2VmYjY2NDhmMC5zZXRDb250ZW50KGh0bWxfMTA0ZjVjNmY3YTZjNDRmZWE4MDE5YjJhMjQ0ZDY1NzUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMDM0Y2VhZTQyYzg2NGYwNDhhYWQ2MWI2ZWQ0YjUzZDYuYmluZFBvcHVwKHBvcHVwXzU4Mjc1OTk0ZGEyMjQ1Mzg4ZDVmY2UzZWZiNjY0OGYwKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2UwNWU4MDVkYTE0NDRmN2M4MWM3ZDljOTI3ODQwNGEwID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjU0MjU5OSwtNzkuMzYwNjM1OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF80MDc4MGJlNjQ1ODQ0NTFiOGY5MjA0MzI5NDdjZGQ4NyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF82YWRjZmI4YjVlOWQ0N2I4OWViNmQzNzdiNzcyYzY5NiA9ICQoJzxkaXYgaWQ9Imh0bWxfNmFkY2ZiOGI1ZTlkNDdiODllYjZkMzc3Yjc3MmM2OTYiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkhhcmJvdXJmcm9udCwgRG93bnRvd24gVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfNDA3ODBiZTY0NTg0NDUxYjhmOTIwNDMyOTQ3Y2RkODcuc2V0Q29udGVudChodG1sXzZhZGNmYjhiNWU5ZDQ3Yjg5ZWI2ZDM3N2I3NzJjNjk2KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2UwNWU4MDVkYTE0NDRmN2M4MWM3ZDljOTI3ODQwNGEwLmJpbmRQb3B1cChwb3B1cF80MDc4MGJlNjQ1ODQ0NTFiOGY5MjA0MzI5NDdjZGQ4Nyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl81M2ZiMGY4OTA3YmI0ZjY2YmQ3ZjVlNGZmYWI4NDE3MyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY1NzE2MTgsLTc5LjM3ODkzNzA5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2EzZDY4OTRlODM4YTQ5NTFiMjQ4MmMwZDQxODczYTQyID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzkzMGVkMGRmNzYxMzQxOTRhY2Q1ZWFkZDU1N2FjMmI2ID0gJCgnPGRpdiBpZD0iaHRtbF85MzBlZDBkZjc2MTM0MTk0YWNkNWVhZGQ1NTdhYzJiNiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+UnllcnNvbixHYXJkZW4gRGlzdHJpY3QsIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2EzZDY4OTRlODM4YTQ5NTFiMjQ4MmMwZDQxODczYTQyLnNldENvbnRlbnQoaHRtbF85MzBlZDBkZjc2MTM0MTk0YWNkNWVhZGQ1NTdhYzJiNik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl81M2ZiMGY4OTA3YmI0ZjY2YmQ3ZjVlNGZmYWI4NDE3My5iaW5kUG9wdXAocG9wdXBfYTNkNjg5NGU4MzhhNDk1MWIyNDgyYzBkNDE4NzNhNDIpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfYjdhZjAwZGUwMWI4NGNlNjg5NDJiYzRiMTliMGFkNjAgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NTE0OTM5LC03OS4zNzU0MTc5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2NmYmViYjkyOGJkNDQ4MzliOTkxMTZmZTlhNzkxOTQyID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzFiM2IwYjE5YjZjYjQ1ZDZiNDRiYWIxNTk5MGYyYjRiID0gJCgnPGRpdiBpZD0iaHRtbF8xYjNiMGIxOWI2Y2I0NWQ2YjQ0YmFiMTU5OTBmMmI0YiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+U3QuIEphbWVzIFRvd24sIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2NmYmViYjkyOGJkNDQ4MzliOTkxMTZmZTlhNzkxOTQyLnNldENvbnRlbnQoaHRtbF8xYjNiMGIxOWI2Y2I0NWQ2YjQ0YmFiMTU5OTBmMmI0Yik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9iN2FmMDBkZTAxYjg0Y2U2ODk0MmJjNGIxOWIwYWQ2MC5iaW5kUG9wdXAocG9wdXBfY2ZiZWJiOTI4YmQ0NDgzOWI5OTExNmZlOWE3OTE5NDIpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfM2EwMTY1MTM4MmM4NDYwOWFjYWVkZjg2OTYzZTEyNGEgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NDQ3NzA3OTk5OTk5OTYsLTc5LjM3MzMwNjRdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfOGJjZDAzODllZWFjNDQ2OGE3YmJiMmQwNzZjNmU5MTQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfOWQ3OWYwMTFjNzBmNGEyNmExYmJiMmM0OTBmMzMzOGEgPSAkKCc8ZGl2IGlkPSJodG1sXzlkNzlmMDExYzcwZjRhMjZhMWJiYjJjNDkwZjMzMzhhIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5CZXJjenkgUGFyaywgRG93bnRvd24gVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfOGJjZDAzODllZWFjNDQ2OGE3YmJiMmQwNzZjNmU5MTQuc2V0Q29udGVudChodG1sXzlkNzlmMDExYzcwZjRhMjZhMWJiYjJjNDkwZjMzMzhhKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzNhMDE2NTEzODJjODQ2MDlhY2FlZGY4Njk2M2UxMjRhLmJpbmRQb3B1cChwb3B1cF84YmNkMDM4OWVlYWM0NDY4YTdiYmIyZDA3NmM2ZTkxNCk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9mY2FkMGU3YjM3N2Q0ZDcwODliZDZlMTNiZjVlYTJkMiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY1Nzk1MjQsLTc5LjM4NzM4MjZdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZDRjNjUzNWU1NmJhNGIzYWEzOTA4NWFjNWRjYzgzM2UgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYjFiMjkwYTExOWFkNDc2NWE1MTRlZjc4MWQ3Y2I1NTIgPSAkKCc8ZGl2IGlkPSJodG1sX2IxYjI5MGExMTlhZDQ3NjVhNTE0ZWY3ODFkN2NiNTUyIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5DZW50cmFsIEJheSBTdHJlZXQsIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2Q0YzY1MzVlNTZiYTRiM2FhMzkwODVhYzVkY2M4MzNlLnNldENvbnRlbnQoaHRtbF9iMWIyOTBhMTE5YWQ0NzY1YTUxNGVmNzgxZDdjYjU1Mik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9mY2FkMGU3YjM3N2Q0ZDcwODliZDZlMTNiZjVlYTJkMi5iaW5kUG9wdXAocG9wdXBfZDRjNjUzNWU1NmJhNGIzYWEzOTA4NWFjNWRjYzgzM2UpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfZWE4OWNiOWZlMDliNGU4ZTgwYmU0NDg5MWI3MTQ2MmYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NTA1NzEyMDAwMDAwMSwtNzkuMzg0NTY3NV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9iZjMyMmM3Nzk4OGI0ZDE3ODZmM2FlY2U0NTEzMWU0YSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF80YWRkMGVmNmJlNDI0ZjZhODVlNDM3ZDljZjc0MWJmNCA9ICQoJzxkaXYgaWQ9Imh0bWxfNGFkZDBlZjZiZTQyNGY2YTg1ZTQzN2Q5Y2Y3NDFiZjQiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkFkZWxhaWRlLEtpbmcsUmljaG1vbmQsIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2JmMzIyYzc3OTg4YjRkMTc4NmYzYWVjZTQ1MTMxZTRhLnNldENvbnRlbnQoaHRtbF80YWRkMGVmNmJlNDI0ZjZhODVlNDM3ZDljZjc0MWJmNCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9lYTg5Y2I5ZmUwOWI0ZThlODBiZTQ0ODkxYjcxNDYyZi5iaW5kUG9wdXAocG9wdXBfYmYzMjJjNzc5ODhiNGQxNzg2ZjNhZWNlNDUxMzFlNGEpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfOWQ3YTRkYTY3NDVjNDZlYTg2NDMyYTE2NWVkZmIyM2IgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NDA4MTU3LC03OS4zODE3NTIyOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF84ZGMxMzlmNGZjYjU0YjdlOGU4MDA0NDcwYWU1NDQwOCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF82N2E3ZjU3ODIzMWY0MTc5ODA1NzBiNzcyY2M5M2ZiYiA9ICQoJzxkaXYgaWQ9Imh0bWxfNjdhN2Y1NzgyMzFmNDE3OTgwNTcwYjc3MmNjOTNmYmIiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkhhcmJvdXJmcm9udCBFYXN0LFRvcm9udG8gSXNsYW5kcyxVbmlvbiBTdGF0aW9uLCBEb3dudG93biBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF84ZGMxMzlmNGZjYjU0YjdlOGU4MDA0NDcwYWU1NDQwOC5zZXRDb250ZW50KGh0bWxfNjdhN2Y1NzgyMzFmNDE3OTgwNTcwYjc3MmNjOTNmYmIpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfOWQ3YTRkYTY3NDVjNDZlYTg2NDMyYTE2NWVkZmIyM2IuYmluZFBvcHVwKHBvcHVwXzhkYzEzOWY0ZmNiNTRiN2U4ZTgwMDQ0NzBhZTU0NDA4KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2U1ZTFmM2Q3YzBmYTQ5MjA4OGVlYTc1YzI5NmVmY2ZmID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjQ3MTc2OCwtNzkuMzgxNTc2NDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNTExMTlhZDkxMDE5NDZmM2ExMzk5MWM0ODc2MzhiOGUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNmVlNWZhNWI0YTg5NDJjZjgyOWEwZjVmMGE5MDNjYTQgPSAkKCc8ZGl2IGlkPSJodG1sXzZlZTVmYTViNGE4OTQyY2Y4MjlhMGY1ZjBhOTAzY2E0IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5EZXNpZ24gRXhjaGFuZ2UsVG9yb250byBEb21pbmlvbiBDZW50cmUsIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzUxMTE5YWQ5MTAxOTQ2ZjNhMTM5OTFjNDg3NjM4YjhlLnNldENvbnRlbnQoaHRtbF82ZWU1ZmE1YjRhODk0MmNmODI5YTBmNWYwYTkwM2NhNCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9lNWUxZjNkN2MwZmE0OTIwODhlZWE3NWMyOTZlZmNmZi5iaW5kUG9wdXAocG9wdXBfNTExMTlhZDkxMDE5NDZmM2ExMzk5MWM0ODc2MzhiOGUpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfYmMxMTczMmI4YTM3NDhkY2I2OTNmODk4MTE3ZWUzZGEgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NDgxOTg1LC03OS4zNzk4MTY5MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8wNTQ1NDY0NTVlODk0NzRmYWI1YmE2ZjNhNzcxZTQ5NSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF82YzQ1OWNlNjE0MTA0ZWRlOGY1Y2U1ZjAyMDRkMzhjOCA9ICQoJzxkaXYgaWQ9Imh0bWxfNmM0NTljZTYxNDEwNGVkZThmNWNlNWYwMjA0ZDM4YzgiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNvbW1lcmNlIENvdXJ0LFZpY3RvcmlhIEhvdGVsLCBEb3dudG93biBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8wNTQ1NDY0NTVlODk0NzRmYWI1YmE2ZjNhNzcxZTQ5NS5zZXRDb250ZW50KGh0bWxfNmM0NTljZTYxNDEwNGVkZThmNWNlNWYwMjA0ZDM4YzgpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYmMxMTczMmI4YTM3NDhkY2I2OTNmODk4MTE3ZWUzZGEuYmluZFBvcHVwKHBvcHVwXzA1NDU0NjQ1NWU4OTQ3NGZhYjViYTZmM2E3NzFlNDk1KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzAxYTY5ODJiMWUwMjRmZDhiNDY4ZWI5Y2Y3YzY4MmVjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzMzMjgyNSwtNzkuNDE5NzQ5N10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF85MzU1NWU2NDk1Mjg0MjFkODkwNzU3YTJkY2VhN2Y1NSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9kYjFjOTU0MDJmNjg0ZGFmOGNjYWNlMDM4OGI4NGY1OSA9ICQoJzxkaXYgaWQ9Imh0bWxfZGIxYzk1NDAyZjY4NGRhZjhjY2FjZTAzODhiODRmNTkiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkJlZGZvcmQgUGFyayxMYXdyZW5jZSBNYW5vciBFYXN0LCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF85MzU1NWU2NDk1Mjg0MjFkODkwNzU3YTJkY2VhN2Y1NS5zZXRDb250ZW50KGh0bWxfZGIxYzk1NDAyZjY4NGRhZjhjY2FjZTAzODhiODRmNTkpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMDFhNjk4MmIxZTAyNGZkOGI0NjhlYjljZjdjNjgyZWMuYmluZFBvcHVwKHBvcHVwXzkzNTU1ZTY0OTUyODQyMWQ4OTA3NTdhMmRjZWE3ZjU1KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2NiNmFhZDg2NzgyZTQyNjU4NWU4YzEwNTg5ZmIyNzQxID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzExNjk0OCwtNzkuNDE2OTM1NTk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNWNkMDYxYzRjNDQyNDJiZmFmMDU0ZDZjYzc3ZmY2MDMgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNzNkYzlkZDI5NjJhNGJmMWEzMTU2ZmQzYzc4YTExMDIgPSAkKCc8ZGl2IGlkPSJodG1sXzczZGM5ZGQyOTYyYTRiZjFhMzE1NmZkM2M3OGExMTAyIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Sb3NlbGF3biwgQ2VudHJhbCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF81Y2QwNjFjNGM0NDI0MmJmYWYwNTRkNmNjNzdmZjYwMy5zZXRDb250ZW50KGh0bWxfNzNkYzlkZDI5NjJhNGJmMWEzMTU2ZmQzYzc4YTExMDIpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfY2I2YWFkODY3ODJlNDI2NTg1ZThjMTA1ODlmYjI3NDEuYmluZFBvcHVwKHBvcHVwXzVjZDA2MWM0YzQ0MjQyYmZhZjA1NGQ2Y2M3N2ZmNjAzKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzdkMzJmZDlmYzQzNzRiMTc4OThmZTg3ZDg3MmNiZWZjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjk2OTQ3NiwtNzkuNDExMzA3MjAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfYzE4Nzc4Zjg1MWRiNGEwOGFmNmQwODg0NDI4OGI4YmEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNGFlNzYwMjQ4MTRkNGM5ZmEzYmNiNDUwNmM3NWEzMDIgPSAkKCc8ZGl2IGlkPSJodG1sXzRhZTc2MDI0ODE0ZDRjOWZhM2JjYjQ1MDZjNzVhMzAyIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Gb3Jlc3QgSGlsbCBOb3J0aCxGb3Jlc3QgSGlsbCBXZXN0LCBDZW50cmFsIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2MxODc3OGY4NTFkYjRhMDhhZjZkMDg4NDQyODhiOGJhLnNldENvbnRlbnQoaHRtbF80YWU3NjAyNDgxNGQ0YzlmYTNiY2I0NTA2Yzc1YTMwMik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl83ZDMyZmQ5ZmM0Mzc0YjE3ODk4ZmU4N2Q4NzJjYmVmYy5iaW5kUG9wdXAocG9wdXBfYzE4Nzc4Zjg1MWRiNGEwOGFmNmQwODg0NDI4OGI4YmEpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfYjEzMmZmZWZhMGQ4NGJmYWI0ZmRlMDlmNTc3MGZkZGUgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NzI3MDk3LC03OS40MDU2Nzg0MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9jMzI4YzZhMWI4YjY0Yjk3YWUyZTI5ZTRlNDU1N2RmNCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF82ZTM4YzY5NmZlYTg0NGIzYmVlYmVmNjkwOGJiMTc4ZSA9ICQoJzxkaXYgaWQ9Imh0bWxfNmUzOGM2OTZmZWE4NDRiM2JlZWJlZjY5MDhiYjE3OGUiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlRoZSBBbm5leCxOb3J0aCBNaWR0b3duLFlvcmt2aWxsZSwgQ2VudHJhbCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9jMzI4YzZhMWI4YjY0Yjk3YWUyZTI5ZTRlNDU1N2RmNC5zZXRDb250ZW50KGh0bWxfNmUzOGM2OTZmZWE4NDRiM2JlZWJlZjY5MDhiYjE3OGUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYjEzMmZmZWZhMGQ4NGJmYWI0ZmRlMDlmNTc3MGZkZGUuYmluZFBvcHVwKHBvcHVwX2MzMjhjNmExYjhiNjRiOTdhZTJlMjllNGU0NTU3ZGY0KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzQ0NjQ5ZWI4YjU5NzQ5ZjA4ZDJmZDA5ZTBiNTEyMmUwID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjYyNjk1NiwtNzkuNDAwMDQ5M10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9mY2JhZDM4YWY2MDg0ZGM3YTA5ZGNkNTlkODQ5ODg1NCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8yMDA0Y2NkMTE0ZDQ0NzE2YTdhM2ZiMjkwMmVlYWE0MSA9ICQoJzxkaXYgaWQ9Imh0bWxfMjAwNGNjZDExNGQ0NDcxNmE3YTNmYjI5MDJlZWFhNDEiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkhhcmJvcmQsVW5pdmVyc2l0eSBvZiBUb3JvbnRvLCBEb3dudG93biBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9mY2JhZDM4YWY2MDg0ZGM3YTA5ZGNkNTlkODQ5ODg1NC5zZXRDb250ZW50KGh0bWxfMjAwNGNjZDExNGQ0NDcxNmE3YTNmYjI5MDJlZWFhNDEpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNDQ2NDllYjhiNTk3NDlmMDhkMmZkMDllMGI1MTIyZTAuYmluZFBvcHVwKHBvcHVwX2ZjYmFkMzhhZjYwODRkYzdhMDlkY2Q1OWQ4NDk4ODU0KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzVkZTI2MWI0M2NmMzQ5NGE4NDY1YmFjZDAzMTUxOGRiID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjUzMjA1NywtNzkuNDAwMDQ5M10sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9jZjQ0NDA0YjliYjE0MDcyOGNmNjZjNTcyZDUxYmI0MyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8yNjM5ZjVkYWYyOGI0YTQyYTgyMzM2NjA4YTk0Yzg1ZCA9ICQoJzxkaXYgaWQ9Imh0bWxfMjYzOWY1ZGFmMjhiNGE0MmE4MjMzNjYwOGE5NGM4NWQiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNoaW5hdG93bixHcmFuZ2UgUGFyayxLZW5zaW5ndG9uIE1hcmtldCwgRG93bnRvd24gVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfY2Y0NDQwNGI5YmIxNDA3MjhjZjY2YzU3MmQ1MWJiNDMuc2V0Q29udGVudChodG1sXzI2MzlmNWRhZjI4YjRhNDJhODIzMzY2MDhhOTRjODVkKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzVkZTI2MWI0M2NmMzQ5NGE4NDY1YmFjZDAzMTUxOGRiLmJpbmRQb3B1cChwb3B1cF9jZjQ0NDA0YjliYjE0MDcyOGNmNjZjNTcyZDUxYmI0Myk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8yYTY2M2E0MDFiMmM0ZDEwYmViN2IwYmFhNmQ0MTI5NiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjYyODk0NjcsLTc5LjM5NDQxOTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNDVjMjVhOTNmYWFjNDZjYmIxNWYzOGZhODc2MzEzZDQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZDQwMjhjYTc5YjA1NDkyZTg2YWE0NmJhMTVmNTBiMzUgPSAkKCc8ZGl2IGlkPSJodG1sX2Q0MDI4Y2E3OWIwNTQ5MmU4NmFhNDZiYTE1ZjUwYjM1IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5DTiBUb3dlcixCYXRodXJzdCBRdWF5LElzbGFuZCBhaXJwb3J0LEhhcmJvdXJmcm9udCBXZXN0LEtpbmcgYW5kIFNwYWRpbmEsUmFpbHdheSBMYW5kcyxTb3V0aCBOaWFnYXJhLCBEb3dudG93biBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF80NWMyNWE5M2ZhYWM0NmNiYjE1ZjM4ZmE4NzYzMTNkNC5zZXRDb250ZW50KGh0bWxfZDQwMjhjYTc5YjA1NDkyZTg2YWE0NmJhMTVmNTBiMzUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMmE2NjNhNDAxYjJjNGQxMGJlYjdiMGJhYTZkNDEyOTYuYmluZFBvcHVwKHBvcHVwXzQ1YzI1YTkzZmFhYzQ2Y2JiMTVmMzhmYTg3NjMxM2Q0KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2IwMmM1NjQyNjc1YTRhZjdhOGMwMzk1MTYwNjIyZWNlID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjQ2NDM1MiwtNzkuMzc0ODQ1OTk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNDA0NWEyOTFhY2JlNDgyMTg3ZTEzMGRiZDA3OTUzYzkgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZjBhYjM1MDVlNmFlNGY5MWI5NmM4N2RlNDRiOWE2YmMgPSAkKCc8ZGl2IGlkPSJodG1sX2YwYWIzNTA1ZTZhZTRmOTFiOTZjODdkZTQ0YjlhNmJjIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5TdG4gQSBQTyBCb3hlcyAyNSBUaGUgRXNwbGFuYWRlLCBEb3dudG93biBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF80MDQ1YTI5MWFjYmU0ODIxODdlMTMwZGJkMDc5NTNjOS5zZXRDb250ZW50KGh0bWxfZjBhYjM1MDVlNmFlNGY5MWI5NmM4N2RlNDRiOWE2YmMpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYjAyYzU2NDI2NzVhNGFmN2E4YzAzOTUxNjA2MjJlY2UuYmluZFBvcHVwKHBvcHVwXzQwNDVhMjkxYWNiZTQ4MjE4N2UxMzBkYmQwNzk1M2M5KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzg0ZDQ2ZjYwOTZiNTQ1MGI5NGRhMzBhMmU1NjE1YmY2ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjQ4NDI5MiwtNzkuMzgyMjgwMl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF80NmFiMGI4ZjNlMTA0NWE0YTYzMGYyMjdhMzQ0NGZiOCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9iZWUxYTk1YzJjNWU0NDFmOTBlNzk3ZGU4NTRiZDM0MyA9ICQoJzxkaXYgaWQ9Imh0bWxfYmVlMWE5NWMyYzVlNDQxZjkwZTc5N2RlODU0YmQzNDMiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkZpcnN0IENhbmFkaWFuIFBsYWNlLFVuZGVyZ3JvdW5kIGNpdHksIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzQ2YWIwYjhmM2UxMDQ1YTRhNjMwZjIyN2EzNDQ0ZmI4LnNldENvbnRlbnQoaHRtbF9iZWUxYTk1YzJjNWU0NDFmOTBlNzk3ZGU4NTRiZDM0Myk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl84NGQ0NmY2MDk2YjU0NTBiOTRkYTMwYTJlNTYxNWJmNi5iaW5kUG9wdXAocG9wdXBfNDZhYjBiOGYzZTEwNDVhNGE2MzBmMjI3YTM0NDRmYjgpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfZjY2MzRmMWE5NmIzNGU0YTg4YzRlYzA3YTdmNDM1YzQgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43MTg1MTc5OTk5OTk5OTYsLTc5LjQ2NDc2MzI5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzExNGFhMWRhMDMyOTRlZDBhNTdmNWU3ODE5MGY3ZmU0ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2UwMDMyYzQ1NzQ2YzQ4OTZhNWEwNWYwN2MyMzhhNTA3ID0gJCgnPGRpdiBpZD0iaHRtbF9lMDAzMmM0NTc0NmM0ODk2YTVhMDVmMDdjMjM4YTUwNyIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+TGF3cmVuY2UgSGVpZ2h0cyxMYXdyZW5jZSBNYW5vciwgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMTE0YWExZGEwMzI5NGVkMGE1N2Y1ZTc4MTkwZjdmZTQuc2V0Q29udGVudChodG1sX2UwMDMyYzQ1NzQ2YzQ4OTZhNWEwNWYwN2MyMzhhNTA3KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2Y2NjM0ZjFhOTZiMzRlNGE4OGM0ZWMwN2E3ZjQzNWM0LmJpbmRQb3B1cChwb3B1cF8xMTRhYTFkYTAzMjk0ZWQwYTU3ZjVlNzgxOTBmN2ZlNCk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8zZjNlMjc0ZWU1OTg0MmZlYTQ3YTBlNmQ2NGQ0OTUzYiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcwOTU3NywtNzkuNDQ1MDcyNTk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMmQzYjc5NDg4NTY5NGFiNDk1MGI2YmRmMmI4MmFhYjQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZDFmMGZlZjYxZDRhNGViMDkwMTAzMWQ0ZmJhNzQ4N2MgPSAkKCc8ZGl2IGlkPSJodG1sX2QxZjBmZWY2MWQ0YTRlYjA5MDEwMzFkNGZiYTc0ODdjIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5HbGVuY2Fpcm4sIE5vcnRoIFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzJkM2I3OTQ4ODU2OTRhYjQ5NTBiNmJkZjJiODJhYWI0LnNldENvbnRlbnQoaHRtbF9kMWYwZmVmNjFkNGE0ZWIwOTAxMDMxZDRmYmE3NDg3Yyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8zZjNlMjc0ZWU1OTg0MmZlYTQ3YTBlNmQ2NGQ0OTUzYi5iaW5kUG9wdXAocG9wdXBfMmQzYjc5NDg4NTY5NGFiNDk1MGI2YmRmMmI4MmFhYjQpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfOGQwMDQ5ODNkZDMzNGM1Nzg5M2Y4NmI3NGQxZTI5MDkgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42OTM3ODEzLC03OS40MjgxOTE0MDAwMDAwMl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8wYTJlMDFkNTM0NDU0ZWM0OThhZjAyNGE2NzcyZDFiOSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8zMmNkZGYyODAxOGE0ZDEzYmMxZDJiYTIwOGQ3YTBkNyA9ICQoJzxkaXYgaWQ9Imh0bWxfMzJjZGRmMjgwMThhNGQxM2JjMWQyYmEyMDhkN2EwZDciIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkh1bWV3b29kLUNlZGFydmFsZSwgWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMGEyZTAxZDUzNDQ1NGVjNDk4YWYwMjRhNjc3MmQxYjkuc2V0Q29udGVudChodG1sXzMyY2RkZjI4MDE4YTRkMTNiYzFkMmJhMjA4ZDdhMGQ3KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzhkMDA0OTgzZGQzMzRjNTc4OTNmODZiNzRkMWUyOTA5LmJpbmRQb3B1cChwb3B1cF8wYTJlMDFkNTM0NDU0ZWM0OThhZjAyNGE2NzcyZDFiOSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9iMjI0ZDU5MmFiYzM0ZGU3YjJjMzhjNDllOThhZWY3YSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY4OTAyNTYsLTc5LjQ1MzUxMl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8wY2IyMDgwYTI5OTc0N2MyOGQzN2RlODVjNjhhNmIyZCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9jZGM2MDYwMDU4NTI0ZjEyYWQzMWNhZWM3MDJhNjQ5MyA9ICQoJzxkaXYgaWQ9Imh0bWxfY2RjNjA2MDA1ODUyNGYxMmFkMzFjYWVjNzAyYTY0OTMiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNhbGVkb25pYS1GYWlyYmFua3MsIFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzBjYjIwODBhMjk5NzQ3YzI4ZDM3ZGU4NWM2OGE2YjJkLnNldENvbnRlbnQoaHRtbF9jZGM2MDYwMDU4NTI0ZjEyYWQzMWNhZWM3MDJhNjQ5Myk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9iMjI0ZDU5MmFiYzM0ZGU3YjJjMzhjNDllOThhZWY3YS5iaW5kUG9wdXAocG9wdXBfMGNiMjA4MGEyOTk3NDdjMjhkMzdkZTg1YzY4YTZiMmQpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfOWMzOTU2YjMxZDZlNDE2MTg2M2U5NTUyMTc5OGZlNmEgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42Njk1NDIsLTc5LjQyMjU2MzddLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNmIwMzg0MDVkZGVjNGU4YWIzNzIyN2U1NTJiN2YwN2QgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZGUwZjNiMTZiYjZiNGI1MzlmYzNiMDkzNjhhZjNlNjIgPSAkKCc8ZGl2IGlkPSJodG1sX2RlMGYzYjE2YmI2YjRiNTM5ZmMzYjA5MzY4YWYzZTYyIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5DaHJpc3RpZSwgRG93bnRvd24gVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfNmIwMzg0MDVkZGVjNGU4YWIzNzIyN2U1NTJiN2YwN2Quc2V0Q29udGVudChodG1sX2RlMGYzYjE2YmI2YjRiNTM5ZmMzYjA5MzY4YWYzZTYyKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzljMzk1NmIzMWQ2ZTQxNjE4NjNlOTU1MjE3OThmZTZhLmJpbmRQb3B1cChwb3B1cF82YjAzODQwNWRkZWM0ZThhYjM3MjI3ZTU1MmI3ZjA3ZCk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8yZjZiZjNkMjQyNjQ0ZjllOGQwOGM0NWY3MzIxMmE0MyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY2OTAwNTEwMDAwMDAxLC03OS40NDIyNTkzXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2NkZTcyNDg2MTUwYzQ0NjNiOWY3MDgzZDdmYWI5NDM4ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzUzNzA1YjZlNzNiNzRiOTg4Zjk2NTA3MGE1ZjVhYjhiID0gJCgnPGRpdiBpZD0iaHRtbF81MzcwNWI2ZTczYjc0Yjk4OGY5NjUwNzBhNWY1YWI4YiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+RG92ZXJjb3VydCBWaWxsYWdlLER1ZmZlcmluLCBXZXN0IFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2NkZTcyNDg2MTUwYzQ0NjNiOWY3MDgzZDdmYWI5NDM4LnNldENvbnRlbnQoaHRtbF81MzcwNWI2ZTczYjc0Yjk4OGY5NjUwNzBhNWY1YWI4Yik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8yZjZiZjNkMjQyNjQ0ZjllOGQwOGM0NWY3MzIxMmE0My5iaW5kUG9wdXAocG9wdXBfY2RlNzI0ODYxNTBjNDQ2M2I5ZjcwODNkN2ZhYjk0MzgpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfMzViMGQwNTY5MGQxNDI4NWJjMDc1Nzk0MjlmZjE5ZGMgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NDc5MjY3MDAwMDAwMDYsLTc5LjQxOTc0OTddLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNTNiYWJmNmUxNDkyNGZkZDg0ZTkyNTVjMmEzZjBlNWQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfODcwZTUyMWMxYjRmNGRjODk5ZTBjOGVlNzQzOTM0N2QgPSAkKCc8ZGl2IGlkPSJodG1sXzg3MGU1MjFjMWI0ZjRkYzg5OWUwYzhlZTc0MzkzNDdkIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5MaXR0bGUgUG9ydHVnYWwsVHJpbml0eSwgV2VzdCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF81M2JhYmY2ZTE0OTI0ZmRkODRlOTI1NWMyYTNmMGU1ZC5zZXRDb250ZW50KGh0bWxfODcwZTUyMWMxYjRmNGRjODk5ZTBjOGVlNzQzOTM0N2QpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMzViMGQwNTY5MGQxNDI4NWJjMDc1Nzk0MjlmZjE5ZGMuYmluZFBvcHVwKHBvcHVwXzUzYmFiZjZlMTQ5MjRmZGQ4NGU5MjU1YzJhM2YwZTVkKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzFhMmY5YzVmM2Y2NzQ1YzhiMzM2NDUxYTMwNDUxMzBiID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjM2ODQ3MiwtNzkuNDI4MTkxNDAwMDAwMDJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfY2ZkMWIwMWQ3ZTkwNGI0Y2FjZjE0MTJhNTg3ZWZjNWQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNmE4YjJjYTEyMDI0NDgxY2JkMDdiODg5N2JlOTMzNDUgPSAkKCc8ZGl2IGlkPSJodG1sXzZhOGIyY2ExMjAyNDQ4MWNiZDA3Yjg4OTdiZTkzMzQ1IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Ccm9ja3RvbixFeGhpYml0aW9uIFBsYWNlLFBhcmtkYWxlIFZpbGxhZ2UsIFdlc3QgVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfY2ZkMWIwMWQ3ZTkwNGI0Y2FjZjE0MTJhNTg3ZWZjNWQuc2V0Q29udGVudChodG1sXzZhOGIyY2ExMjAyNDQ4MWNiZDA3Yjg4OTdiZTkzMzQ1KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzFhMmY5YzVmM2Y2NzQ1YzhiMzM2NDUxYTMwNDUxMzBiLmJpbmRQb3B1cChwb3B1cF9jZmQxYjAxZDdlOTA0YjRjYWNmMTQxMmE1ODdlZmM1ZCk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8wMThmODA2NTJmYzY0OWY1OTJjNmZjNDFmMjAxMjkxNyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcxMzc1NjIwMDAwMDAwNiwtNzkuNDkwMDczOF0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9lODljZDE1NmQ1N2I0OWY5OTZiOTFjYmUyNmMzMTJiYiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8xMDRjZThiNjQyNmQ0OTA4YWExM2EzNGE5ZmI3MzYyZSA9ICQoJzxkaXYgaWQ9Imh0bWxfMTA0Y2U4YjY0MjZkNDkwOGFhMTNhMzRhOWZiNzM2MmUiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkRvd25zdmlldyxOb3J0aCBQYXJrLFVwd29vZCBQYXJrLCBOb3J0aCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9lODljZDE1NmQ1N2I0OWY5OTZiOTFjYmUyNmMzMTJiYi5zZXRDb250ZW50KGh0bWxfMTA0Y2U4YjY0MjZkNDkwOGFhMTNhMzRhOWZiNzM2MmUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMDE4ZjgwNjUyZmM2NDlmNTkyYzZmYzQxZjIwMTI5MTcuYmluZFBvcHVwKHBvcHVwX2U4OWNkMTU2ZDU3YjQ5Zjk5NmI5MWNiZTI2YzMxMmJiKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzVjYzk1ZjMxY2Q3OTRiNGFiM2VjNWNkYjMwMDcxOGNjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjkxMTE1OCwtNzkuNDc2MDEzMjk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMmE1YTBlMzA1NmU5NDgyMmFhYTcxMzI3ZjIwZjlmZmUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfOWI4Yjk1YTM1YzY3NGRjMjhhNDFhMjA2ZDJmYTIxMWEgPSAkKCc8ZGl2IGlkPSJodG1sXzliOGI5NWEzNWM2NzRkYzI4YTQxYTIwNmQyZmEyMTFhIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5EZWwgUmF5LEtlZWxlc2RhbGUsTW91bnQgRGVubmlzLFNpbHZlcnRob3JuLCBZb3JrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8yYTVhMGUzMDU2ZTk0ODIyYWFhNzEzMjdmMjBmOWZmZS5zZXRDb250ZW50KGh0bWxfOWI4Yjk1YTM1YzY3NGRjMjhhNDFhMjA2ZDJmYTIxMWEpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNWNjOTVmMzFjZDc5NGI0YWIzZWM1Y2RiMzAwNzE4Y2MuYmluZFBvcHVwKHBvcHVwXzJhNWEwZTMwNTZlOTQ4MjJhYWE3MTMyN2YyMGY5ZmZlKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzIwNmI5NTE3ZjkxYzQ1MDM4ZThmZmZiMDA2MjQ5MzMyID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjczMTg1Mjk5OTk5OTksLTc5LjQ4NzI2MTkwMDAwMDAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2ZmODZkMjdhNDM4ZDQzMTQ5OGM4YzAyZjIzNzdhZjFmID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzg0ZjVmNjYzZTI1YzQ1MGQ4ZDFjMGVjMjMzZjEyNjgyID0gJCgnPGRpdiBpZD0iaHRtbF84NGY1ZjY2M2UyNWM0NTBkOGQxYzBlYzIzM2YxMjY4MiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+VGhlIEp1bmN0aW9uIE5vcnRoLFJ1bm55bWVkZSwgWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZmY4NmQyN2E0MzhkNDMxNDk4YzhjMDJmMjM3N2FmMWYuc2V0Q29udGVudChodG1sXzg0ZjVmNjYzZTI1YzQ1MGQ4ZDFjMGVjMjMzZjEyNjgyKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzIwNmI5NTE3ZjkxYzQ1MDM4ZThmZmZiMDA2MjQ5MzMyLmJpbmRQb3B1cChwb3B1cF9mZjg2ZDI3YTQzOGQ0MzE0OThjOGMwMmYyMzc3YWYxZik7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl82NTg0OTZiZWZlNjE0ODI5OWE1ZDE0ZjU3NmMzYTUwNCA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY2MTYwODMsLTc5LjQ2NDc2MzI5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzE1YmRjMWRjZGM1YzRkNzFhMmRjNGEwMWMwMzI4NTQ4ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzk2ZDA3NWVhNzZkMDQyM2JiOTg5YjUyZjBkYzQ3MzdlID0gJCgnPGRpdiBpZD0iaHRtbF85NmQwNzVlYTc2ZDA0MjNiYjk4OWI1MmYwZGM0NzM3ZSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+SGlnaCBQYXJrLFRoZSBKdW5jdGlvbiBTb3V0aCwgV2VzdCBUb3JvbnRvPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8xNWJkYzFkY2RjNWM0ZDcxYTJkYzRhMDFjMDMyODU0OC5zZXRDb250ZW50KGh0bWxfOTZkMDc1ZWE3NmQwNDIzYmI5ODliNTJmMGRjNDczN2UpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNjU4NDk2YmVmZTYxNDgyOTlhNWQxNGY1NzZjM2E1MDQuYmluZFBvcHVwKHBvcHVwXzE1YmRjMWRjZGM1YzRkNzFhMmRjNGEwMWMwMzI4NTQ4KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzc1MzViNTNkNmVmOTQ2NWY5YTM2M2I1ZjVlNDBjOGYwID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjQ4OTU5NywtNzkuNDU2MzI1XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzQ3ZjgzNzRkMGQ2NzRhNzY4MjM0ZjIxMjc0Yzg1NjM1ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzFhNjg0Y2U2YTFjOTRmODI4ODgzOGM5NGE2NDY2MWQ4ID0gJCgnPGRpdiBpZD0iaHRtbF8xYTY4NGNlNmExYzk0ZjgyODg4MzhjOTRhNjQ2NjFkOCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+UGFya2RhbGUsUm9uY2VzdmFsbGVzLCBXZXN0IFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzQ3ZjgzNzRkMGQ2NzRhNzY4MjM0ZjIxMjc0Yzg1NjM1LnNldENvbnRlbnQoaHRtbF8xYTY4NGNlNmExYzk0ZjgyODg4MzhjOTRhNjQ2NjFkOCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl83NTM1YjUzZDZlZjk0NjVmOWEzNjNiNWY1ZTQwYzhmMC5iaW5kUG9wdXAocG9wdXBfNDdmODM3NGQwZDY3NGE3NjgyMzRmMjEyNzRjODU2MzUpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfMTk4MTc0N2UzY2I4NGU3ZmE0ZGMyODNkMmY5MDcwMGUgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NTE1NzA2LC03OS40ODQ0NDk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzViZThiYzgxZjdmNzRlOTI5NDE0NWEzZDU3YmFkODJiID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzNjMDcwZmE4MDRiNjRlMjlhMjRlMTFhZTY1ZGFjOTc1ID0gJCgnPGRpdiBpZD0iaHRtbF8zYzA3MGZhODA0YjY0ZTI5YTI0ZTExYWU2NWRhYzk3NSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+UnVubnltZWRlLFN3YW5zZWEsIFdlc3QgVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfNWJlOGJjODFmN2Y3NGU5Mjk0MTQ1YTNkNTdiYWQ4MmIuc2V0Q29udGVudChodG1sXzNjMDcwZmE4MDRiNjRlMjlhMjRlMTFhZTY1ZGFjOTc1KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzE5ODE3NDdlM2NiODRlN2ZhNGRjMjgzZDJmOTA3MDBlLmJpbmRQb3B1cChwb3B1cF81YmU4YmM4MWY3Zjc0ZTkyOTQxNDVhM2Q1N2JhZDgyYik7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8wZWNhOTdjNTZhNzk0YjllOGQ1MjM4ZGEyZTM3NzkzZiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY2MjMwMTUsLTc5LjM4OTQ5MzhdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZTNlN2IwMTRkMjdhNDE3YThkYzcxNzA4NWNjMGY5OWYgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMjliZjdiZGJiMjE5NGM4ZWI4YTQ2Y2RhOTI2ODE5OTggPSAkKCc8ZGl2IGlkPSJodG1sXzI5YmY3YmRiYjIxOTRjOGViOGE0NmNkYTkyNjgxOTk4IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5RdWVlbiYjMzk7cyBQYXJrLCBRdWVlbiYjMzk7cyBQYXJrPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9lM2U3YjAxNGQyN2E0MTdhOGRjNzE3MDg1Y2MwZjk5Zi5zZXRDb250ZW50KGh0bWxfMjliZjdiZGJiMjE5NGM4ZWI4YTQ2Y2RhOTI2ODE5OTgpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMGVjYTk3YzU2YTc5NGI5ZThkNTIzOGRhMmUzNzc5M2YuYmluZFBvcHVwKHBvcHVwX2UzZTdiMDE0ZDI3YTQxN2E4ZGM3MTcwODVjYzBmOTlmKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2Y0MzBiMjNkZTY1YTQzM2M4YzBkYWI1ZmU2MzU4MDkwID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjM2OTY1NiwtNzkuNjE1ODE4OTk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMzAwZTQ0MjYxZmViNDIxN2JkMmVhN2I2ZDY4ZDAwMDUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfOTM1YWVkNTJmYzkzNGU4YzhjMWI1YTMyNDZmMzk5NjAgPSAkKCc8ZGl2IGlkPSJodG1sXzkzNWFlZDUyZmM5MzRlOGM4YzFiNWEzMjQ2ZjM5OTYwIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5DYW5hZGEgUG9zdCBHYXRld2F5IFByb2Nlc3NpbmcgQ2VudHJlLCBNaXNzaXNzYXVnYTwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMzAwZTQ0MjYxZmViNDIxN2JkMmVhN2I2ZDY4ZDAwMDUuc2V0Q29udGVudChodG1sXzkzNWFlZDUyZmM5MzRlOGM4YzFiNWEzMjQ2ZjM5OTYwKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2Y0MzBiMjNkZTY1YTQzM2M4YzBkYWI1ZmU2MzU4MDkwLmJpbmRQb3B1cChwb3B1cF8zMDBlNDQyNjFmZWI0MjE3YmQyZWE3YjZkNjhkMDAwNSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8yMmZmMWNjNzc0ZjY0ZTdjYThiMzdjMmJhNTcxNTQxMSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY2Mjc0MzksLTc5LjMyMTU1OF0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF85MzViYzM2NTBmY2U0YzQzOWIyYzk0MDI2YjBkMWRhMyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9iYzY4YTY1YmFlODc0ZDQxOThjZGVmMDYxZTEwY2ZmNCA9ICQoJzxkaXYgaWQ9Imh0bWxfYmM2OGE2NWJhZTg3NGQ0MTk4Y2RlZjA2MWUxMGNmZjQiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkJ1c2luZXNzIFJlcGx5IE1haWwgUHJvY2Vzc2luZyBDZW50cmUgOTY5IEVhc3Rlcm4sIEVhc3QgVG9yb250bzwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfOTM1YmMzNjUwZmNlNGM0MzliMmM5NDAyNmIwZDFkYTMuc2V0Q29udGVudChodG1sX2JjNjhhNjViYWU4NzRkNDE5OGNkZWYwNjFlMTBjZmY0KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzIyZmYxY2M3NzRmNjRlN2NhOGIzN2MyYmE1NzE1NDExLmJpbmRQb3B1cChwb3B1cF85MzViYzM2NTBmY2U0YzQzOWIyYzk0MDI2YjBkMWRhMyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl82MWYyNGUxODMxMWI0MGUyOWFmM2RhNDY4YjZlMmRjYiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjYwNTY0NjYsLTc5LjUwMTMyMDcwMDAwMDAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2E1MWQyOTQ4YWMyZjRkMmFhZjE0ZmUxNDcwNTk3NTQxID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2YxYTNiOTE4ODM1ODQwMWVhYWVmYjQyYTIzM2Y3ZTUzID0gJCgnPGRpdiBpZD0iaHRtbF9mMWEzYjkxODgzNTg0MDFlYWFlZmI0MmEyMzNmN2U1MyIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+SHVtYmVyIEJheSBTaG9yZXMsTWltaWNvIFNvdXRoLE5ldyBUb3JvbnRvLCBFdG9iaWNva2U8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2E1MWQyOTQ4YWMyZjRkMmFhZjE0ZmUxNDcwNTk3NTQxLnNldENvbnRlbnQoaHRtbF9mMWEzYjkxODgzNTg0MDFlYWFlZmI0MmEyMzNmN2U1Myk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl82MWYyNGUxODMxMWI0MGUyOWFmM2RhNDY4YjZlMmRjYi5iaW5kUG9wdXAocG9wdXBfYTUxZDI5NDhhYzJmNGQyYWFmMTRmZTE0NzA1OTc1NDEpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfODIyZjc3YmNmYjBhNDViY2IzYWI3MGI0M2NlNDE5OTYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42MDI0MTM3MDAwMDAwMSwtNzkuNTQzNDg0MDk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZWRkMDUwM2E4MzBiNDkyYjk5NTM2YmNlZjYyNzJhMjUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMDA5ZWYyMjZjODRjNGZmZThmMTYxZjZiZDJhNTM0MWYgPSAkKCc8ZGl2IGlkPSJodG1sXzAwOWVmMjI2Yzg0YzRmZmU4ZjE2MWY2YmQyYTUzNDFmIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5BbGRlcndvb2QsTG9uZyBCcmFuY2gsIEV0b2JpY29rZTwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZWRkMDUwM2E4MzBiNDkyYjk5NTM2YmNlZjYyNzJhMjUuc2V0Q29udGVudChodG1sXzAwOWVmMjI2Yzg0YzRmZmU4ZjE2MWY2YmQyYTUzNDFmKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzgyMmY3N2JjZmIwYTQ1YmNiM2FiNzBiNDNjZTQxOTk2LmJpbmRQb3B1cChwb3B1cF9lZGQwNTAzYTgzMGI0OTJiOTk1MzZiY2VmNjI3MmEyNSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl81NDU1NTFmNmJlMjI0YTgzYmI3NjdhMDdmMWY0NGFjMSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY1MzY1MzYwMDAwMDAwNSwtNzkuNTA2OTQzNl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9hZWQ2NTJiOTlhYjA0MGUxOGQ1NjdhZThjYjc5MTE5MCA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF80YWJkYTM3NmJmYTE0YzFlOWZlZjM1Njc3OTFhMjc0OSA9ICQoJzxkaXYgaWQ9Imh0bWxfNGFiZGEzNzZiZmExNGMxZTlmZWYzNTY3NzkxYTI3NDkiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlRoZSBLaW5nc3dheSxNb250Z29tZXJ5IFJvYWQsT2xkIE1pbGwgTm9ydGgsIEV0b2JpY29rZTwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfYWVkNjUyYjk5YWIwNDBlMThkNTY3YWU4Y2I3OTExOTAuc2V0Q29udGVudChodG1sXzRhYmRhMzc2YmZhMTRjMWU5ZmVmMzU2Nzc5MWEyNzQ5KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzU0NTU1MWY2YmUyMjRhODNiYjc2N2EwN2YxZjQ0YWMxLmJpbmRQb3B1cChwb3B1cF9hZWQ2NTJiOTlhYjA0MGUxOGQ1NjdhZThjYjc5MTE5MCk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9lMjdiZjFkY2FlY2U0NTg5Yjk3ZTE2ZjM0MWU1MWU5ZiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjYzNjI1NzksLTc5LjQ5ODUwOTA5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzQxZjUzNjc4Zjg4MzQ1ODZhOWI5OWU5ZGI4Y2I2MTI1ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzM5NWU3Y2YzYTY0MjRkZjE5MTdmNDNkYzMxZjliYjkwID0gJCgnPGRpdiBpZD0iaHRtbF8zOTVlN2NmM2E2NDI0ZGYxOTE3ZjQzZGMzMWY5YmI5MCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+SHVtYmVyIEJheSxLaW5nJiMzOTtzIE1pbGwgUGFyayxLaW5nc3dheSBQYXJrIFNvdXRoIEVhc3QsTWltaWNvIE5FLE9sZCBNaWxsIFNvdXRoLFRoZSBRdWVlbnN3YXkgRWFzdCxSb3lhbCBZb3JrIFNvdXRoIEVhc3QsU3VubnlsZWEsIEV0b2JpY29rZTwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfNDFmNTM2NzhmODgzNDU4NmE5Yjk5ZTlkYjhjYjYxMjUuc2V0Q29udGVudChodG1sXzM5NWU3Y2YzYTY0MjRkZjE5MTdmNDNkYzMxZjliYjkwKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2UyN2JmMWRjYWVjZTQ1ODliOTdlMTZmMzQxZTUxZTlmLmJpbmRQb3B1cChwb3B1cF80MWY1MzY3OGY4ODM0NTg2YTliOTllOWRiOGNiNjEyNSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8xYjUxMjBmMDM3ZWQ0ODc3OTZhYjcxNDMyMmRjYmEwMyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjYyODg0MDgsLTc5LjUyMDk5OTQwMDAwMDAxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2FiOWY3OWQ1MzFlYTRiYTk4MDk1M2IwYzk3YTliMTUzID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2VmOWVkMjY1NDI0NTRjYTI5NDc5ZjAzYzNkZmQwNjEyID0gJCgnPGRpdiBpZD0iaHRtbF9lZjllZDI2NTQyNDU0Y2EyOTQ3OWYwM2MzZGZkMDYxMiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+S2luZ3N3YXkgUGFyayBTb3V0aCBXZXN0LE1pbWljbyBOVyxUaGUgUXVlZW5zd2F5IFdlc3QsUm95YWwgWW9yayBTb3V0aCBXZXN0LFNvdXRoIG9mIEJsb29yLCBFdG9iaWNva2U8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2FiOWY3OWQ1MzFlYTRiYTk4MDk1M2IwYzk3YTliMTUzLnNldENvbnRlbnQoaHRtbF9lZjllZDI2NTQyNDU0Y2EyOTQ3OWYwM2MzZGZkMDYxMik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8xYjUxMjBmMDM3ZWQ0ODc3OTZhYjcxNDMyMmRjYmEwMy5iaW5kUG9wdXAocG9wdXBfYWI5Zjc5ZDUzMWVhNGJhOTgwOTUzYjBjOTdhOWIxNTMpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfN2JiNDZjNGExZmJhNDAyZjg1NWYwOTNjYzhkYTkwNDcgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42Njc4NTU2LC03OS41MzIyNDI0MDAwMDAwMl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9lYzc5Mzk1YzVkOTU0ZDIxOWM0NzJjMDRlMGMwMzFmMyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF80N2NiNzBhMGVmNjU0MTQ3OWFkYTJiZTBmYmRjMWU2MyA9ICQoJzxkaXYgaWQ9Imh0bWxfNDdjYjcwYTBlZjY1NDE0NzlhZGEyYmUwZmJkYzFlNjMiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlF1ZWVuJiMzOTtzIFBhcmssIERvd250b3duIFRvcm9udG88L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2VjNzkzOTVjNWQ5NTRkMjE5YzQ3MmMwNGUwYzAzMWYzLnNldENvbnRlbnQoaHRtbF80N2NiNzBhMGVmNjU0MTQ3OWFkYTJiZTBmYmRjMWU2Myk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl83YmI0NmM0YTFmYmE0MDJmODU1ZjA5M2NjOGRhOTA0Ny5iaW5kUG9wdXAocG9wdXBfZWM3OTM5NWM1ZDk1NGQyMTljNDcyYzA0ZTBjMDMxZjMpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfOGJiOWUyYmU4ZTUwNGZhYzk2NTU3NTE1NGU5MGU0ZDEgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42NTA5NDMyLC03OS41NTQ3MjQ0MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF81MGY0NWFmZjVhOGE0NDJhODNhNWZiZDgxOWIwZDVkYiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8yMDYyNDU0NjU2YWE0YWJlOTAyOTRmOGE5OWNhMzg5MiA9ICQoJzxkaXYgaWQ9Imh0bWxfMjA2MjQ1NDY1NmFhNGFiZTkwMjk0ZjhhOTljYTM4OTIiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNsb3ZlcmRhbGUsSXNsaW5ndG9uLE1hcnRpbiBHcm92ZSxQcmluY2VzcyBHYXJkZW5zLFdlc3QgRGVhbmUgUGFyaywgRXRvYmljb2tlPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF81MGY0NWFmZjVhOGE0NDJhODNhNWZiZDgxOWIwZDVkYi5zZXRDb250ZW50KGh0bWxfMjA2MjQ1NDY1NmFhNGFiZTkwMjk0ZjhhOTljYTM4OTIpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfOGJiOWUyYmU4ZTUwNGZhYzk2NTU3NTE1NGU5MGU0ZDEuYmluZFBvcHVwKHBvcHVwXzUwZjQ1YWZmNWE4YTQ0MmE4M2E1ZmJkODE5YjBkNWRiKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2QzMzM3NWVmOWQwYzRiYTE4NGU2NzgyMTJjNTE3ZjNlID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNjQzNTE1MiwtNzkuNTc3MjAwNzk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNTNlYjViZTQ1ZTc2NGIxN2E2ZjUxN2VmMTgxZTQ0YTYgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZDVkMGFkZjAyODczNDhkMWI0Yjk5YWEzZWZmY2EwN2IgPSAkKCc8ZGl2IGlkPSJodG1sX2Q1ZDBhZGYwMjg3MzQ4ZDFiNGI5OWFhM2VmZmNhMDdiIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5CbG9vcmRhbGUgR2FyZGVucyxFcmluZ2F0ZSxNYXJrbGFuZCBXb29kLE9sZCBCdXJuaGFtdGhvcnBlLCBFdG9iaWNva2U8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzUzZWI1YmU0NWU3NjRiMTdhNmY1MTdlZjE4MWU0NGE2LnNldENvbnRlbnQoaHRtbF9kNWQwYWRmMDI4NzM0OGQxYjRiOTlhYTNlZmZjYTA3Yik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9kMzMzNzVlZjlkMGM0YmExODRlNjc4MjEyYzUxN2YzZS5iaW5kUG9wdXAocG9wdXBfNTNlYjViZTQ1ZTc2NGIxN2E2ZjUxN2VmMTgxZTQ0YTYpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfYWFiOTJkMmI5YWNkNDk4ODg0NWRmY2EzZjI1ZDFmYTggPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43NTYzMDMzLC03OS41NjU5NjMyOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9mZjZmOTEyN2IzYjM0YTYwOWM3ZTRhMzcyMTNiYzgyMyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8wMjNmNzhjYWZkZDE0NDRmYjgxNGY2YWE0MTE2NGZhYyA9ICQoJzxkaXYgaWQ9Imh0bWxfMDIzZjc4Y2FmZGQxNDQ0ZmI4MTRmNmFhNDExNjRmYWMiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkh1bWJlciBTdW1taXQsIE5vcnRoIFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2ZmNmY5MTI3YjNiMzRhNjA5YzdlNGEzNzIxM2JjODIzLnNldENvbnRlbnQoaHRtbF8wMjNmNzhjYWZkZDE0NDRmYjgxNGY2YWE0MTE2NGZhYyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9hYWI5MmQyYjlhY2Q0OTg4ODQ1ZGZjYTNmMjVkMWZhOC5iaW5kUG9wdXAocG9wdXBfZmY2ZjkxMjdiM2IzNGE2MDljN2U0YTM3MjEzYmM4MjMpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfNjliODU3YzYwMWI5NDhlZGIwMTJkMjM2NzA2MjdmYmIgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43MjQ3NjU5LC03OS41MzIyNDI0MDAwMDAwMl0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF84MDM2OGE4YWIxMWQ0ZmUyOTg0NjdjNTU4ZWZiMTk1ZiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9mMjUxMWFhMGIwMWQ0ZmY0YWI1NzNlYWUzMjM5NGU4MCA9ICQoJzxkaXYgaWQ9Imh0bWxfZjI1MTFhYTBiMDFkNGZmNGFiNTczZWFlMzIzOTRlODAiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkVtZXJ5LEh1bWJlcmxlYSwgTm9ydGggWW9yazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfODAzNjhhOGFiMTFkNGZlMjk4NDY3YzU1OGVmYjE5NWYuc2V0Q29udGVudChodG1sX2YyNTExYWEwYjAxZDRmZjRhYjU3M2VhZTMyMzk0ZTgwKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzY5Yjg1N2M2MDFiOTQ4ZWRiMDEyZDIzNjcwNjI3ZmJiLmJpbmRQb3B1cChwb3B1cF84MDM2OGE4YWIxMWQ0ZmUyOTg0NjdjNTU4ZWZiMTk1Zik7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl81NzgyYjU4NmNiZWU0MTIxODNhNTBjNjljNGE4NDk4MyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcwNjg3NiwtNzkuNTE4MTg4NDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMDc0ZTBjYzc5MDhhNDBjM2IxNWY3YmM0YjI0ZTYxZTUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMDczODU0ZDlkZWZmNDlmOWJlMjY0NTkxOGJmOTlhZjkgPSAkKCc8ZGl2IGlkPSJodG1sXzA3Mzg1NGQ5ZGVmZjQ5ZjliZTI2NDU5MThiZjk5YWY5IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5XZXN0b24sIFlvcms8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzA3NGUwY2M3OTA4YTQwYzNiMTVmN2JjNGIyNGU2MWU1LnNldENvbnRlbnQoaHRtbF8wNzM4NTRkOWRlZmY0OWY5YmUyNjQ1OTE4YmY5OWFmOSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl81NzgyYjU4NmNiZWU0MTIxODNhNTBjNjljNGE4NDk4My5iaW5kUG9wdXAocG9wdXBfMDc0ZTBjYzc5MDhhNDBjM2IxNWY3YmM0YjI0ZTYxZTUpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfMTUyNWVjZTIyNTJmNDliM2FhNDg0MmQxOGRlMDQ0MTYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42OTYzMTksLTc5LjUzMjI0MjQwMDAwMDAyXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwX2MzMDdmYjdlYmM1MjRlMWRhNjZiZjUxMjQzNWM1ZjI1KTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzhlN2NkNDQ0OWY5MjQ2MGJhNDk1NWU1ZGU3NDg2ZjE5ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzQ0NTk0Y2ZhZjdjMDQ0ZWQ4MWMwNTM4NDYxYjQ0M2Q5ID0gJCgnPGRpdiBpZD0iaHRtbF80NDU5NGNmYWY3YzA0NGVkODFjMDUzODQ2MWI0NDNkOSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+V2VzdG1vdW50LCBFdG9iaWNva2U8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzhlN2NkNDQ0OWY5MjQ2MGJhNDk1NWU1ZGU3NDg2ZjE5LnNldENvbnRlbnQoaHRtbF80NDU5NGNmYWY3YzA0NGVkODFjMDUzODQ2MWI0NDNkOSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8xNTI1ZWNlMjI1MmY0OWIzYWE0ODQyZDE4ZGUwNDQxNi5iaW5kUG9wdXAocG9wdXBfOGU3Y2Q0NDQ5ZjkyNDYwYmE0OTU1ZTVkZTc0ODZmMTkpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfOWFlMDU2OTNkMDc4NGFjZmJmNmI4N2FiNjY1ZGJjMTAgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My42ODg5MDU0LC03OS41NTQ3MjQ0MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9jOWE0NDcxOTBhZDQ0MjIyOTFjOWQ5OTcxZjM0ZWQ0MSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF81MDFlMGY4NmY0Yjg0ZjUyOWQ3NjVjOWZlNGFkZTNjOSA9ICQoJzxkaXYgaWQ9Imh0bWxfNTAxZTBmODZmNGI4NGY1MjlkNzY1YzlmZTRhZGUzYzkiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPktpbmdzdmlldyBWaWxsYWdlLE1hcnRpbiBHcm92ZSBHYXJkZW5zLFJpY2h2aWV3IEdhcmRlbnMsU3QuIFBoaWxsaXBzLCBFdG9iaWNva2U8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2M5YTQ0NzE5MGFkNDQyMjI5MWM5ZDk5NzFmMzRlZDQxLnNldENvbnRlbnQoaHRtbF81MDFlMGY4NmY0Yjg0ZjUyOWQ3NjVjOWZlNGFkZTNjOSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl85YWUwNTY5M2QwNzg0YWNmYmY2Yjg3YWI2NjVkYmMxMC5iaW5kUG9wdXAocG9wdXBfYzlhNDQ3MTkwYWQ0NDIyMjkxYzlkOTk3MWYzNGVkNDEpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfY2NhZTM2ZTc3ZTAwNDg1MjgzYWFjOWE2ODI1ZGY4YTYgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43Mzk0MTYzOTk5OTk5OTYsLTc5LjU4ODQzNjldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfYzMwN2ZiN2ViYzUyNGUxZGE2NmJmNTEyNDM1YzVmMjUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZmU3MWE5NzNmZmM0NDk1NThkNTNhMjIyNTA3ZWU5NTAgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMDdjMDM1NGJhODllNDA3Njk4MzVhZWQ4YTc5YWEzOTIgPSAkKCc8ZGl2IGlkPSJodG1sXzA3YzAzNTRiYTg5ZTQwNzY5ODM1YWVkOGE3OWFhMzkyIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5BbGJpb24gR2FyZGVucyxCZWF1bW9uZCBIZWlnaHRzLEh1bWJlcmdhdGUsSmFtZXN0b3duLE1vdW50IE9saXZlLFNpbHZlcnN0b25lLFNvdXRoIFN0ZWVsZXMsVGhpc3RsZXRvd24sIEV0b2JpY29rZTwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZmU3MWE5NzNmZmM0NDk1NThkNTNhMjIyNTA3ZWU5NTAuc2V0Q29udGVudChodG1sXzA3YzAzNTRiYTg5ZTQwNzY5ODM1YWVkOGE3OWFhMzkyKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2NjYWUzNmU3N2UwMDQ4NTI4M2FhYzlhNjgyNWRmOGE2LmJpbmRQb3B1cChwb3B1cF9mZTcxYTk3M2ZmYzQ0OTU1OGQ1M2EyMjI1MDdlZTk1MCk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl81Y2ZlY2VhNDRkMjY0MDM5ODRhODEwZTAwN2ZmNjM4YiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcwNjc0ODI5OTk5OTk5NCwtNzkuNTk0MDU0NF0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF9jMzA3ZmI3ZWJjNTI0ZTFkYTY2YmY1MTI0MzVjNWYyNSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9lMGJiMmM4OTdjNzA0ZTQ0YjU3ZjY3YTNjNDdhMWY5MiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF85ZGMwN2JhZmE4MTM0ZjQ5OWJjZGY5OTIyYjUxYWY3MCA9ICQoJzxkaXYgaWQ9Imh0bWxfOWRjMDdiYWZhODEzNGY0OTliY2RmOTkyMmI1MWFmNzAiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPk5vcnRod2VzdCwgRXRvYmljb2tlPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9lMGJiMmM4OTdjNzA0ZTQ0YjU3ZjY3YTNjNDdhMWY5Mi5zZXRDb250ZW50KGh0bWxfOWRjMDdiYWZhODEzNGY0OTliY2RmOTkyMmI1MWFmNzApOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNWNmZWNlYTQ0ZDI2NDAzOTg0YTgxMGUwMDdmZjYzOGIuYmluZFBvcHVwKHBvcHVwX2UwYmIyYzg5N2M3MDRlNDRiNTdmNjdhM2M0N2ExZjkyKTsKCiAgICAgICAgICAgIAogICAgICAgIAo8L3NjcmlwdD4=" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>




```python
# deep analysis of Scarborough borough
df_sc = df_new[df_new['Borough'] == 'Scarborough'].reset_index(drop=True)
df_sc.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Rouge,Malvern</td>
      <td>43.806686</td>
      <td>-79.194353</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>Scarborough</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>43.784535</td>
      <td>-79.160497</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>Scarborough</td>
      <td>Guildwood,Morningside,West Hill</td>
      <td>43.763573</td>
      <td>-79.188711</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>Scarborough</td>
      <td>Woburn</td>
      <td>43.770992</td>
      <td>-79.216917</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
      <td>43.773136</td>
      <td>-79.239476</td>
    </tr>
  </tbody>
</table>
</div>




```python
#latitude and longitude of Scarborough
latitude = 43.7764
longitude = -79.2318

map_Scarborough = folium.Map(location=[latitude, longitude], zoom_start=11)

# add markers to map
for lat, lng, label in zip(df_sc['Latitude'], df_sc['Longitude'], df_sc['Neighbourhood']):
    label = folium.Popup(label, parse_html=True)
    folium.CircleMarker(
        [lat, lng],
        radius=5,
        popup=label,
        color='blue',
        fill=True,
        fill_color='#3186cc',
        fill_opacity=0.7,
        parse_html=False).add_to(map_Scarborough)  
    
map_Scarborough
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><iframe src="data:text/html;charset=utf-8;base64,PCFET0NUWVBFIGh0bWw+CjxoZWFkPiAgICAKICAgIDxtZXRhIGh0dHAtZXF1aXY9ImNvbnRlbnQtdHlwZSIgY29udGVudD0idGV4dC9odG1sOyBjaGFyc2V0PVVURi04IiAvPgogICAgPHNjcmlwdD5MX1BSRUZFUl9DQU5WQVMgPSBmYWxzZTsgTF9OT19UT1VDSCA9IGZhbHNlOyBMX0RJU0FCTEVfM0QgPSBmYWxzZTs8L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmpzIj48L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2FqYXguZ29vZ2xlYXBpcy5jb20vYWpheC9saWJzL2pxdWVyeS8xLjExLjEvanF1ZXJ5Lm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvanMvYm9vdHN0cmFwLm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9jZG5qcy5jbG91ZGZsYXJlLmNvbS9hamF4L2xpYnMvTGVhZmxldC5hd2Vzb21lLW1hcmtlcnMvMi4wLjIvbGVhZmxldC5hd2Vzb21lLW1hcmtlcnMuanMiPjwvc2NyaXB0PgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL21heGNkbi5ib290c3RyYXBjZG4uY29tL2Jvb3RzdHJhcC8zLjIuMC9jc3MvYm9vdHN0cmFwLm1pbi5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvY3NzL2Jvb3RzdHJhcC10aGVtZS5taW4uY3NzIi8+CiAgICA8bGluayByZWw9InN0eWxlc2hlZXQiIGhyZWY9Imh0dHBzOi8vbWF4Y2RuLmJvb3RzdHJhcGNkbi5jb20vZm9udC1hd2Vzb21lLzQuNi4zL2Nzcy9mb250LWF3ZXNvbWUubWluLmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2NkbmpzLmNsb3VkZmxhcmUuY29tL2FqYXgvbGlicy9MZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy8yLjAuMi9sZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9yYXdnaXQuY29tL3B5dGhvbi12aXN1YWxpemF0aW9uL2ZvbGl1bS9tYXN0ZXIvZm9saXVtL3RlbXBsYXRlcy9sZWFmbGV0LmF3ZXNvbWUucm90YXRlLmNzcyIvPgogICAgPHN0eWxlPmh0bWwsIGJvZHkge3dpZHRoOiAxMDAlO2hlaWdodDogMTAwJTttYXJnaW46IDA7cGFkZGluZzogMDt9PC9zdHlsZT4KICAgIDxzdHlsZT4jbWFwIHtwb3NpdGlvbjphYnNvbHV0ZTt0b3A6MDtib3R0b206MDtyaWdodDowO2xlZnQ6MDt9PC9zdHlsZT4KICAgIAogICAgICAgICAgICA8c3R5bGU+ICNtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMgewogICAgICAgICAgICAgICAgcG9zaXRpb24gOiByZWxhdGl2ZTsKICAgICAgICAgICAgICAgIHdpZHRoIDogMTAwLjAlOwogICAgICAgICAgICAgICAgaGVpZ2h0OiAxMDAuMCU7CiAgICAgICAgICAgICAgICBsZWZ0OiAwLjAlOwogICAgICAgICAgICAgICAgdG9wOiAwLjAlOwogICAgICAgICAgICAgICAgfQogICAgICAgICAgICA8L3N0eWxlPgogICAgICAgIAo8L2hlYWQ+Cjxib2R5PiAgICAKICAgIAogICAgICAgICAgICA8ZGl2IGNsYXNzPSJmb2xpdW0tbWFwIiBpZD0ibWFwXzk1ZjA2NDU5ZTM1NzRmNGI5ZjE4ZTY0MTg5N2NiNjkzIiA+PC9kaXY+CiAgICAgICAgCjwvYm9keT4KPHNjcmlwdD4gICAgCiAgICAKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGJvdW5kcyA9IG51bGw7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgdmFyIG1hcF85NWYwNjQ1OWUzNTc0ZjRiOWYxOGU2NDE4OTdjYjY5MyA9IEwubWFwKAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJ21hcF85NWYwNjQ1OWUzNTc0ZjRiOWYxOGU2NDE4OTdjYjY5MycsCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7Y2VudGVyOiBbNDMuNzc2NCwtNzkuMjMxOF0sCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB6b29tOiAxMSwKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIG1heEJvdW5kczogYm91bmRzLAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgbGF5ZXJzOiBbXSwKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHdvcmxkQ29weUp1bXA6IGZhbHNlLAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgY3JzOiBMLkNSUy5FUFNHMzg1NwogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9KTsKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHRpbGVfbGF5ZXJfNDY1N2JlNmY0YWQ3NDI1NWE5YjQwNzNiNjI5OTZhODMgPSBMLnRpbGVMYXllcigKICAgICAgICAgICAgICAgICdodHRwczovL3tzfS50aWxlLm9wZW5zdHJlZXRtYXAub3JnL3t6fS97eH0ve3l9LnBuZycsCiAgICAgICAgICAgICAgICB7CiAgImF0dHJpYnV0aW9uIjogbnVsbCwKICAiZGV0ZWN0UmV0aW5hIjogZmFsc2UsCiAgIm1heFpvb20iOiAxOCwKICAibWluWm9vbSI6IDEsCiAgIm5vV3JhcCI6IGZhbHNlLAogICJzdWJkb21haW5zIjogImFiYyIKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2M0ZTZmM2ZjZTBlOTQ1ZjdiZWEwNjgzZDU5N2UyZWFmID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuODA2Njg2Mjk5OTk5OTk2LC03OS4xOTQzNTM0MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF85NWYwNjQ1OWUzNTc0ZjRiOWYxOGU2NDE4OTdjYjY5Myk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9lYmMyNTI2ZDc1MmU0YTY3YTVmNTJiM2E0ODQ5OTRhOSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8zMTdmNzA2YWNlMTU0NmY2ODcyNDQ3YzQzM2ZkYzE0MSA9ICQoJzxkaXYgaWQ9Imh0bWxfMzE3ZjcwNmFjZTE1NDZmNjg3MjQ0N2M0MzNmZGMxNDEiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlJvdWdlLE1hbHZlcm48L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2ViYzI1MjZkNzUyZTRhNjdhNWY1MmIzYTQ4NDk5NGE5LnNldENvbnRlbnQoaHRtbF8zMTdmNzA2YWNlMTU0NmY2ODcyNDQ3YzQzM2ZkYzE0MSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl9jNGU2ZjNmY2UwZTk0NWY3YmVhMDY4M2Q1OTdlMmVhZi5iaW5kUG9wdXAocG9wdXBfZWJjMjUyNmQ3NTJlNGE2N2E1ZjUyYjNhNDg0OTk0YTkpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfYjI0YTVmMTI0YjEwNGQ3YjllYzY4NWVjMzc0NjQxMTAgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43ODQ1MzUxLC03OS4xNjA0OTcwOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF85NWYwNjQ1OWUzNTc0ZjRiOWYxOGU2NDE4OTdjYjY5Myk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF82MGRjNmFlMmJmM2E0MzU1YjM2MDMzZmVhODIyNmI5OSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9kNTllNmQ4ZWMwNWU0YWQyYmMwN2NlNTk3ODJhMjQ1MCA9ICQoJzxkaXYgaWQ9Imh0bWxfZDU5ZTZkOGVjMDVlNGFkMmJjMDdjZTU5NzgyYTI0NTAiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkhpZ2hsYW5kIENyZWVrLFJvdWdlIEhpbGwsUG9ydCBVbmlvbjwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfNjBkYzZhZTJiZjNhNDM1NWIzNjAzM2ZlYTgyMjZiOTkuc2V0Q29udGVudChodG1sX2Q1OWU2ZDhlYzA1ZTRhZDJiYzA3Y2U1OTc4MmEyNDUwKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2IyNGE1ZjEyNGIxMDRkN2I5ZWM2ODVlYzM3NDY0MTEwLmJpbmRQb3B1cChwb3B1cF82MGRjNmFlMmJmM2E0MzU1YjM2MDMzZmVhODIyNmI5OSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl83NjM5ODgzMjljOWU0M2FhODViOGNkODhjNTViMGFjMyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc2MzU3MjYsLTc5LjE4ODcxMTVdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMDU2MDMzNjgzNTY5NDY5NzliNDRmODkwM2ZlMjcyODEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMzhlNTRhOTNlMmU0NGZhZjhiZTVkMDEyOTFmZjMzOWQgPSAkKCc8ZGl2IGlkPSJodG1sXzM4ZTU0YTkzZTJlNDRmYWY4YmU1ZDAxMjkxZmYzMzlkIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5HdWlsZHdvb2QsTW9ybmluZ3NpZGUsV2VzdCBIaWxsPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8wNTYwMzM2ODM1Njk0Njk3OWI0NGY4OTAzZmUyNzI4MS5zZXRDb250ZW50KGh0bWxfMzhlNTRhOTNlMmU0NGZhZjhiZTVkMDEyOTFmZjMzOWQpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNzYzOTg4MzI5YzllNDNhYTg1YjhjZDg4YzU1YjBhYzMuYmluZFBvcHVwKHBvcHVwXzA1NjAzMzY4MzU2OTQ2OTc5YjQ0Zjg5MDNmZTI3MjgxKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzk0ZjE3ZjZiYzIyNjRmN2ViMjc5ZmE1NzJiNGZjNTBhID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzcwOTkyMSwtNzkuMjE2OTE3NDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNGU3MDk0YWY3NTEwNGVjMGIyZDgyNjIyNTM0NzhjZWMgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNmU3NjEzNjExMTUwNDkxMzgyMTM5MzRiYjBkMDkwYjMgPSAkKCc8ZGl2IGlkPSJodG1sXzZlNzYxMzYxMTE1MDQ5MTM4MjEzOTM0YmIwZDA5MGIzIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Xb2J1cm48L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzRlNzA5NGFmNzUxMDRlYzBiMmQ4MjYyMjUzNDc4Y2VjLnNldENvbnRlbnQoaHRtbF82ZTc2MTM2MTExNTA0OTEzODIxMzkzNGJiMGQwOTBiMyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl85NGYxN2Y2YmMyMjY0ZjdlYjI3OWZhNTcyYjRmYzUwYS5iaW5kUG9wdXAocG9wdXBfNGU3MDk0YWY3NTEwNGVjMGIyZDgyNjIyNTM0NzhjZWMpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfM2U3NzI4NzAzOTJmNDBhMjhjZTVkNjU3MmYwYTkwZDkgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43NzMxMzYsLTc5LjIzOTQ3NjA5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzk1ZjA2NDU5ZTM1NzRmNGI5ZjE4ZTY0MTg5N2NiNjkzKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzgzMjk3YmJhN2UzZDQ1NDk4MDBiMTk3NGM4MzFiNTQwID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzQwODkwNjJmZWZjOTRhOTZhNWZjNjY2M2U0NmE5YjMxID0gJCgnPGRpdiBpZD0iaHRtbF80MDg5MDYyZmVmYzk0YTk2YTVmYzY2NjNlNDZhOWIzMSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Q2VkYXJicmFlPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF84MzI5N2JiYTdlM2Q0NTQ5ODAwYjE5NzRjODMxYjU0MC5zZXRDb250ZW50KGh0bWxfNDA4OTA2MmZlZmM5NGE5NmE1ZmM2NjYzZTQ2YTliMzEpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfM2U3NzI4NzAzOTJmNDBhMjhjZTVkNjU3MmYwYTkwZDkuYmluZFBvcHVwKHBvcHVwXzgzMjk3YmJhN2UzZDQ1NDk4MDBiMTk3NGM4MzFiNTQwKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzZlZjNmZWYxNjUxOTRjNWFiYjJiZGNjYjIyYmVhODJjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzQ0NzM0MiwtNzkuMjM5NDc2MDk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfODMwMGYxN2RmZGQwNDY1ZmE5NGFiYWViYWMwNWExYzAgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYTkyOWEwMTI0OTg3NGU1OWI3NzYzMTQxYTcwZjhmYTUgPSAkKCc8ZGl2IGlkPSJodG1sX2E5MjlhMDEyNDk4NzRlNTliNzc2MzE0MWE3MGY4ZmE1IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5TY2FyYm9yb3VnaCBWaWxsYWdlPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF84MzAwZjE3ZGZkZDA0NjVmYTk0YWJhZWJhYzA1YTFjMC5zZXRDb250ZW50KGh0bWxfYTkyOWEwMTI0OTg3NGU1OWI3NzYzMTQxYTcwZjhmYTUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNmVmM2ZlZjE2NTE5NGM1YWJiMmJkY2NiMjJiZWE4MmMuYmluZFBvcHVwKHBvcHVwXzgzMDBmMTdkZmRkMDQ2NWZhOTRhYmFlYmFjMDVhMWMwKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2VjZTM4ZDk1NzVlNTQ5NTk4MDExODFlZWEyYzNhN2RmID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzI3OTI5MiwtNzkuMjYyMDI5NDAwMDAwMDJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZGFkZDE5M2Y0OWJmNDBjM2EwNjBmM2VmNzU4Y2E5ZmEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNmFmMzJlMDI1NGQzNDdlMGIwYjI0ODYzZjhkYTJhNTAgPSAkKCc8ZGl2IGlkPSJodG1sXzZhZjMyZTAyNTRkMzQ3ZTBiMGIyNDg2M2Y4ZGEyYTUwIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5FYXN0IEJpcmNobW91bnQgUGFyayxJb252aWV3LEtlbm5lZHkgUGFyazwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZGFkZDE5M2Y0OWJmNDBjM2EwNjBmM2VmNzU4Y2E5ZmEuc2V0Q29udGVudChodG1sXzZhZjMyZTAyNTRkMzQ3ZTBiMGIyNDg2M2Y4ZGEyYTUwKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2VjZTM4ZDk1NzVlNTQ5NTk4MDExODFlZWEyYzNhN2RmLmJpbmRQb3B1cChwb3B1cF9kYWRkMTkzZjQ5YmY0MGMzYTA2MGYzZWY3NThjYTlmYSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl83ZGU4MTlmMTAwZDk0MWI2OTU2NjE1MzBiNzMyMTQ2NyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcxMTExMTcwMDAwMDAwNCwtNzkuMjg0NTc3Ml0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF85NWYwNjQ1OWUzNTc0ZjRiOWYxOGU2NDE4OTdjYjY5Myk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9jZWYyYjY1ZGY5YWI0ZmM4OWRkZGE5Y2I5MjE2ODU5YyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF84Mjc3MDhhMTk3NTI0Njk5OTNmZmNkYmJiZWM1NDdiZiA9ICQoJzxkaXYgaWQ9Imh0bWxfODI3NzA4YTE5NzUyNDY5OTkzZmZjZGJiYmVjNTQ3YmYiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNsYWlybGVhLEdvbGRlbiBNaWxlLE9ha3JpZGdlPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9jZWYyYjY1ZGY5YWI0ZmM4OWRkZGE5Y2I5MjE2ODU5Yy5zZXRDb250ZW50KGh0bWxfODI3NzA4YTE5NzUyNDY5OTkzZmZjZGJiYmVjNTQ3YmYpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfN2RlODE5ZjEwMGQ5NDFiNjk1NjYxNTMwYjczMjE0NjcuYmluZFBvcHVwKHBvcHVwX2NlZjJiNjVkZjlhYjRmYzg5ZGRkYTljYjkyMTY4NTljKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2I4NGFkMTExMzc3ZjQ4YzhiZTdiMzY1NmVhZmMxZGQ5ID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzE2MzE2LC03OS4yMzk0NzYwOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF85NWYwNjQ1OWUzNTc0ZjRiOWYxOGU2NDE4OTdjYjY5Myk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8xNjNlNTZhNmE1MmE0NzhhYjhjYTIzZTljOTkyN2MzNiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF85MWYyMWEzODQwMjA0NTZhYTQxYTM4ZTI3NDYzOGU3NCA9ICQoJzxkaXYgaWQ9Imh0bWxfOTFmMjFhMzg0MDIwNDU2YWE0MWEzOGUyNzQ2MzhlNzQiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNsaWZmY3Jlc3QsQ2xpZmZzaWRlLFNjYXJib3JvdWdoIFZpbGxhZ2UgV2VzdDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMTYzZTU2YTZhNTJhNDc4YWI4Y2EyM2U5Yzk5MjdjMzYuc2V0Q29udGVudChodG1sXzkxZjIxYTM4NDAyMDQ1NmFhNDFhMzhlMjc0NjM4ZTc0KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2I4NGFkMTExMzc3ZjQ4YzhiZTdiMzY1NmVhZmMxZGQ5LmJpbmRQb3B1cChwb3B1cF8xNjNlNTZhNmE1MmE0NzhhYjhjYTIzZTljOTkyN2MzNik7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8xYmY1MGNmMjRkZDQ0YmU2YjVkZmZiMDNiNGEwNTVlMSA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY5MjY1NzAwMDAwMDAwNCwtNzkuMjY0ODQ4MV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICJibHVlIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMxODZjYyIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF85NWYwNjQ1OWUzNTc0ZjRiOWYxOGU2NDE4OTdjYjY5Myk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF85YWNjNDA1N2E1OWU0NGYwYjAxMmRlZWE1ZGZmZDMyZSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9jYzk3YTAyNzU5OGU0MzBlOTY0OTc0YTNjYTY1MGQyNiA9ICQoJzxkaXYgaWQ9Imh0bWxfY2M5N2EwMjc1OThlNDMwZTk2NDk3NGEzY2E2NTBkMjYiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkJpcmNoIENsaWZmLENsaWZmc2lkZSBXZXN0PC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF85YWNjNDA1N2E1OWU0NGYwYjAxMmRlZWE1ZGZmZDMyZS5zZXRDb250ZW50KGh0bWxfY2M5N2EwMjc1OThlNDMwZTk2NDk3NGEzY2E2NTBkMjYpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMWJmNTBjZjI0ZGQ0NGJlNmI1ZGZmYjAzYjRhMDU1ZTEuYmluZFBvcHVwKHBvcHVwXzlhY2M0MDU3YTU5ZTQ0ZjBiMDEyZGVlYTVkZmZkMzJlKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzAxNjFjNmY5MGIyMzQ3NGE5Yjg5YzQ4ZDQ4NTA0MDNjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzU3NDA5NiwtNzkuMjczMzA0MDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfOTg2YjQwOTBlOTY3NGU0Y2I2MGEzYTZlNGRmZDA3ZWEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfN2ExMGMyNTQ0YzNkNGFiZDhjNGMxMzFiNDliOGM1NjYgPSAkKCc8ZGl2IGlkPSJodG1sXzdhMTBjMjU0NGMzZDRhYmQ4YzRjMTMxYjQ5YjhjNTY2IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Eb3JzZXQgUGFyayxTY2FyYm9yb3VnaCBUb3duIENlbnRyZSxXZXhmb3JkIEhlaWdodHM8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzk4NmI0MDkwZTk2NzRlNGNiNjBhM2E2ZTRkZmQwN2VhLnNldENvbnRlbnQoaHRtbF83YTEwYzI1NDRjM2Q0YWJkOGM0YzEzMWI0OWI4YzU2Nik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8wMTYxYzZmOTBiMjM0NzRhOWI4OWM0OGQ0ODUwNDAzYy5iaW5kUG9wdXAocG9wdXBfOTg2YjQwOTBlOTY3NGU0Y2I2MGEzYTZlNGRmZDA3ZWEpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfM2E1NTg4ZTcxYzI1NGE4MzhjNWRiNzQzZjBlNWNkMTAgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43NTAwNzE1MDAwMDAwMDQsLTc5LjI5NTg0OTFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMjhlZjc3ZDM4YmFjNGQzZGJiNmU2ZWU4MDY4YmQ5MzAgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZmQzYTY2YzlhYjEyNDg2ZTkyODJlZWZkNGZjZmMzYzcgPSAkKCc8ZGl2IGlkPSJodG1sX2ZkM2E2NmM5YWIxMjQ4NmU5MjgyZWVmZDRmY2ZjM2M3IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5NYXJ5dmFsZSxXZXhmb3JkPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8yOGVmNzdkMzhiYWM0ZDNkYmI2ZTZlZTgwNjhiZDkzMC5zZXRDb250ZW50KGh0bWxfZmQzYTY2YzlhYjEyNDg2ZTkyODJlZWZkNGZjZmMzYzcpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfM2E1NTg4ZTcxYzI1NGE4MzhjNWRiNzQzZjBlNWNkMTAuYmluZFBvcHVwKHBvcHVwXzI4ZWY3N2QzOGJhYzRkM2RiYjZlNmVlODA2OGJkOTMwKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzljMjFkMDJkNjE5ODQyNmNhYTQ1YWJlMzFiYjY5ODFkID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzk0MjAwMywtNzkuMjYyMDI5NDAwMDAwMDJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfYWUzNzdjMzg2MjM2NDg5YmJhYzUwODNhZThjNjc4ODkgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNWNjNDhlMTY1NGNmNDEzM2FhYjA4NjIxOGZhNzc2Y2IgPSAkKCc8ZGl2IGlkPSJodG1sXzVjYzQ4ZTE2NTRjZjQxMzNhYWIwODYyMThmYTc3NmNiIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5BZ2luY291cnQ8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2FlMzc3YzM4NjIzNjQ4OWJiYWM1MDgzYWU4YzY3ODg5LnNldENvbnRlbnQoaHRtbF81Y2M0OGUxNjU0Y2Y0MTMzYWFiMDg2MjE4ZmE3NzZjYik7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl85YzIxZDAyZDYxOTg0MjZjYWE0NWFiZTMxYmI2OTgxZC5iaW5kUG9wdXAocG9wdXBfYWUzNzdjMzg2MjM2NDg5YmJhYzUwODNhZThjNjc4ODkpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfN2UxNjhiZWFiZDEwNGU2Zjk0MjU1MGQ3NmMzYWJlMDcgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43ODE2Mzc1LC03OS4zMDQzMDIxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzk1ZjA2NDU5ZTM1NzRmNGI5ZjE4ZTY0MTg5N2NiNjkzKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzEyYzM2MmJlMDliMjRhZmViZTI5YmY1Y2Q5ZTk3ZDRjID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzg0YmM2MDlmZTQ0NzQzZmRiYWE5NzhhOWFkZGI1OGJjID0gJCgnPGRpdiBpZD0iaHRtbF84NGJjNjA5ZmU0NDc0M2ZkYmFhOTc4YTlhZGRiNThiYyIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Q2xhcmtzIENvcm5lcnMsU3VsbGl2YW4sVGFtIE8mIzM5O1NoYW50ZXI8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzEyYzM2MmJlMDliMjRhZmViZTI5YmY1Y2Q5ZTk3ZDRjLnNldENvbnRlbnQoaHRtbF84NGJjNjA5ZmU0NDc0M2ZkYmFhOTc4YTlhZGRiNThiYyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl83ZTE2OGJlYWJkMTA0ZTZmOTQyNTUwZDc2YzNhYmUwNy5iaW5kUG9wdXAocG9wdXBfMTJjMzYyYmUwOWIyNGFmZWJlMjliZjVjZDllOTdkNGMpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfNTE3YzU0Mzg3NWQzNDQyMDgzOTNiZjBkNmJhMTk5YzIgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My44MTUyNTIyLC03OS4yODQ1NzcyXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzk1ZjA2NDU5ZTM1NzRmNGI5ZjE4ZTY0MTg5N2NiNjkzKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2Q5MTdkMzlkYjUxZDQ2M2Y5NzBiMThjOWJjZmFmNWFjID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzRlMjdkY2MzMmRmZDQyNjg4MDI1YTE1ZmNkZWUyOTM4ID0gJCgnPGRpdiBpZD0iaHRtbF80ZTI3ZGNjMzJkZmQ0MjY4ODAyNWExNWZjZGVlMjkzOCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+QWdpbmNvdXJ0IE5vcnRoLEwmIzM5O0Ftb3JlYXV4IEVhc3QsTWlsbGlrZW4sU3RlZWxlcyBFYXN0PC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9kOTE3ZDM5ZGI1MWQ0NjNmOTcwYjE4YzliY2ZhZjVhYy5zZXRDb250ZW50KGh0bWxfNGUyN2RjYzMyZGZkNDI2ODgwMjVhMTVmY2RlZTI5MzgpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNTE3YzU0Mzg3NWQzNDQyMDgzOTNiZjBkNmJhMTk5YzIuYmluZFBvcHVwKHBvcHVwX2Q5MTdkMzlkYjUxZDQ2M2Y5NzBiMThjOWJjZmFmNWFjKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2ZkMzdkZTZmYjEzMTQ5NzRiZmJiMTc5MmRmZDhiN2RmID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzk5NTI1MjAwMDAwMDA1LC03OS4zMTgzODg3XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogImJsdWUiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzE4NmNjIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzk1ZjA2NDU5ZTM1NzRmNGI5ZjE4ZTY0MTg5N2NiNjkzKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzQ2ZjMxNzRhYzhmMzQ5YjM5Nzc4OWM3MmQ1N2E5YTMzID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2U3MmEzYTkyMzY2MjQ5NDhhZjFkMGZmZTRlMGYzOGY2ID0gJCgnPGRpdiBpZD0iaHRtbF9lNzJhM2E5MjM2NjI0OTQ4YWYxZDBmZmU0ZTBmMzhmNiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+TCYjMzk7QW1vcmVhdXggV2VzdDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfNDZmMzE3NGFjOGYzNDliMzk3Nzg5YzcyZDU3YTlhMzMuc2V0Q29udGVudChodG1sX2U3MmEzYTkyMzY2MjQ5NDhhZjFkMGZmZTRlMGYzOGY2KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2ZkMzdkZTZmYjEzMTQ5NzRiZmJiMTc5MmRmZDhiN2RmLmJpbmRQb3B1cChwb3B1cF80NmYzMTc0YWM4ZjM0OWIzOTc3ODljNzJkNTdhOWEzMyk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8yNTlkMjE0M2E2NGI0MzdmOGYyZDY1ZTFhYTI1MjdjMiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjgzNjEyNDcwMDAwMDAwNiwtNzkuMjA1NjM2MDk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiYmx1ZSIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMTg2Y2MiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfOTVmMDY0NTllMzU3NGY0YjlmMThlNjQxODk3Y2I2OTMpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZWI0ZTA5MjY4OWIyNDdmZGI2YjRmNGYyNmY2ZjBhYTQgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMGRhMmRhZmYzNjA0NGQ4MWEyMjE4YjRiMDEwNWM3NDAgPSAkKCc8ZGl2IGlkPSJodG1sXzBkYTJkYWZmMzYwNDRkODFhMjIxOGI0YjAxMDVjNzQwIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5VcHBlciBSb3VnZTwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfZWI0ZTA5MjY4OWIyNDdmZGI2YjRmNGYyNmY2ZjBhYTQuc2V0Q29udGVudChodG1sXzBkYTJkYWZmMzYwNDRkODFhMjIxOGI0YjAxMDVjNzQwKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzI1OWQyMTQzYTY0YjQzN2Y4ZjJkNjVlMWFhMjUyN2MyLmJpbmRQb3B1cChwb3B1cF9lYjRlMDkyNjg5YjI0N2ZkYjZiNGY0ZjI2ZjZmMGFhNCk7CgogICAgICAgICAgICAKICAgICAgICAKPC9zY3JpcHQ+" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



## Analysing venues using four square api


```python
CLIENT_ID = 'UBIHL11MMQA3KOOEVUEMNVQKXX15P3Y0NBNYEH0B15AKDM33' # your Foursquare ID
CLIENT_SECRET = 'CMC1HQKZVYZ5O3JRURIADE4LGMH4IMMEULQXWL31JB1XPRMV' # your Foursquare Secret
VERSION = '20180605' # Foursquare API version

```

### Exploring first neighborhood


```python
df_sc.loc[10,'Neighbourhood']
```




    'Dorset Park,Scarborough Town Centre,Wexford Heights'




```python
neighborhood_latitude = df_sc.loc[0, 'Latitude'] # neighborhood latitude value
neighborhood_longitude = df_sc.loc[0, 'Longitude'] # neighborhood longitude value

neighborhood_name = df_sc.loc[0, 'Neighbourhood'] # neighborhood name

print('Latitude and longitude values of {} are {}, {}.'.format(neighborhood_name, 
                                                               neighborhood_latitude, 
                                                                neighborhood_longitude))
```

    Latitude and longitude values of Rouge,Malvern are 43.806686299999996, -79.19435340000001.
    

## top 100 venues that are in Rouge,Malvern within a radius of 500 meters.


```python
# type your answer here

LIMIT = 100 # limit of number of venues returned by Foursquare API

radius = 5000 # define radius


 # create URL
url = 'https://api.foursquare.com/v2/venues/explore?&client_id={}&client_secret={}&v={}&ll={},{}&radius={}&limit={}'.format(
    CLIENT_ID, 
    CLIENT_SECRET, 
    VERSION, 
    neighborhood_latitude, 
    neighborhood_longitude, 
    radius, 
    LIMIT)
url
```




    'https://api.foursquare.com/v2/venues/explore?&client_id=UBIHL11MMQA3KOOEVUEMNVQKXX15P3Y0NBNYEH0B15AKDM33&client_secret=CMC1HQKZVYZ5O3JRURIADE4LGMH4IMMEULQXWL31JB1XPRMV&v=20180605&ll=43.806686299999996,-79.19435340000001&radius=5000&limit=100'




```python
results = requests.get(url).json()
results
```




    {'meta': {'code': 200, 'requestId': '5df0fb577828ae001b517e01'},
     'response': {'suggestedFilters': {'header': 'Tap to show:',
       'filters': [{'name': 'Open now', 'key': 'openNow'}]},
      'headerLocation': 'Toronto',
      'headerFullLocation': 'Toronto',
      'headerLocationGranularity': 'city',
      'totalResults': 146,
      'suggestedBounds': {'ne': {'lat': 43.85168634500004,
        'lng': -79.13211520730404},
       'sw': {'lat': 43.76168625499995, 'lng': -79.25659159269598}},
      'groups': [{'type': 'Recommended Places',
        'name': 'recommended',
        'items': [{'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4cd854fd3ec4b1f71900be3f',
           'name': 'African Rainforest Pavilion',
           'location': {'lat': 43.81772505914066,
            'lng': -79.18343284457424,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81772505914066,
              'lng': -79.18343284457424}],
            'distance': 1509,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON', 'Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4cd854fd3ec4b1f71900be3f-0'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '542858a0498e22b7cfa91070',
           'name': 'Toronto Pan Am Sports Centre',
           'location': {'address': '875 Morningside Ave',
            'lat': 43.79062336247366,
            'lng': -79.19386919338744,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79062336247366,
              'lng': -79.19386919338744}],
            'distance': 1788,
            'postalCode': 'M1C 0C7',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['875 Morningside Ave',
             'Toronto ON M1C 0C7',
             'Canada']},
           'categories': [{'id': '4f4528bc4b90abdf24c9de85',
             'name': 'Athletics & Sports',
             'pluralName': 'Athletics & Sports',
             'shortName': 'Athletics & Sports',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/sports_outdoors_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-542858a0498e22b7cfa91070-1'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4ad4c05ef964a52093f620e3',
           'name': 'Toronto Zoo',
           'location': {'address': '361 Old Finch Av',
            'crossStreet': 'at Meadowvale & Toronto Zoo Rds',
            'lat': 43.82058189639563,
            'lng': -79.18155125697548,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.82058189639563,
              'lng': -79.18155125697548}],
            'distance': 1857,
            'postalCode': 'M1B 5K7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['361 Old Finch Av (at Meadowvale & Toronto Zoo Rds)',
             'Scarborough ON M1B 5K7',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d17b941735',
             'name': 'Zoo',
             'pluralName': 'Zoos',
             'shortName': 'Zoo',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4ad4c05ef964a52093f620e3-2'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bf590095e800f47b1b8e5d4',
           'name': 'Polar Bear Exhibit',
           'location': {'lat': 43.82337194085348,
            'lng': -79.18514523861421,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.82337194085348,
              'lng': -79.18514523861421}],
            'distance': 1999,
            'postalCode': 'M1X 1L3',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON M1X 1L3', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d17b941735',
             'name': 'Zoo',
             'pluralName': 'Zoos',
             'shortName': 'Zoo',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bf590095e800f47b1b8e5d4-3'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bf596d25efe2d7fbd936534',
           'name': 'Australasia Pavillion',
           'location': {'lat': 43.82256309108205,
            'lng': -79.18328629000764,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.82256309108205,
              'lng': -79.18328629000764}],
            'distance': 1978,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bf596d25efe2d7fbd936534-4'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c97975582b56dcb8320ebaa',
           'name': 'Canadiana exhibit',
           'location': {'lat': 43.81796218928876,
            'lng': -79.19337359666939,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81796218928876,
              'lng': -79.19337359666939}],
            'distance': 1257,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON', 'Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c97975582b56dcb8320ebaa-5'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c000fde92a6c928b09443e2',
           'name': "Lamanna's Bakery, Cafe & Fine Foods",
           'location': {'address': '6758 Kingston Rd.',
            'crossStreet': 'at Sheppard Ave. E',
            'lat': 43.7979714045181,
            'lng': -79.14843228726039,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7979714045181,
              'lng': -79.14843228726039}],
            'distance': 3814,
            'postalCode': 'M1B 1G8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['6758 Kingston Rd. (at Sheppard Ave. E)',
             'Scarborough ON M1B 1G8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16a941735',
             'name': 'Bakery',
             'pluralName': 'Bakeries',
             'shortName': 'Bakery',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/bakery_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []},
           'venuePage': {'id': '48681119'}},
          'referralId': 'e-0-4c000fde92a6c928b09443e2-6'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bb62c786edc76b08482301c',
           'name': 'Morningside Park',
           'location': {'crossStreet': 'Ellesmere Road & Morningside Avenue',
            'lat': 43.786545739068686,
            'lng': -79.20532166956865,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.786545739068686,
              'lng': -79.20532166956865}],
            'distance': 2409,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d163941735',
             'name': 'Park',
             'pluralName': 'Parks',
             'shortName': 'Park',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/parks_outdoors/park_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bb62c786edc76b08482301c-7'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4d669cba83865481c948fa53',
           'name': 'Images Salon & Spa',
           'location': {'address': '8130 Sheppard Ave E',
            'crossStreet': 'Morningside Ave',
            'lat': 43.80228301948931,
            'lng': -79.19856472801668,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80228301948931,
              'lng': -79.19856472801668}],
            'distance': 595,
            'postalCode': 'M1B 3W3',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['8130 Sheppard Ave E (Morningside Ave)',
             'Toronto ON M1B 3W3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1ed941735',
             'name': 'Spa',
             'pluralName': 'Spas',
             'shortName': 'Spa',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/spa_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4d669cba83865481c948fa53-8'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '50730879e4b00022a2a53d29',
           'name': 'Orangutan Exhibit',
           'location': {'lat': 43.81841270807629,
            'lng': -79.18254791524345,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81841270807629,
              'lng': -79.18254791524345}],
            'distance': 1613,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-50730879e4b00022a2a53d29-9'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4f538e74e4b0ef9672a71ac9',
           'name': 'penguin exhibit',
           'location': {'lat': 43.81943486516662,
            'lng': -79.18595932419524,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81943486516662,
              'lng': -79.18595932419524}],
            'distance': 1571,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4f538e74e4b0ef9672a71ac9-10'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c546bef1b46c9b689e291ce',
           'name': 'BeaverTails',
           'location': {'address': 'Meadowvale Road',
            'crossStreet': 'in Toronto Zoo',
            'lat': 43.823376,
            'lng': -79.184616,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.823376,
              'lng': -79.184616}],
            'distance': 2015,
            'postalCode': 'M1B 5K7',
            'cc': 'CA',
            'neighborhood': 'Rouge River',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Meadowvale Road (in Toronto Zoo)',
             'Toronto ON M1B 5K7',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1d0941735',
             'name': 'Dessert Shop',
             'pluralName': 'Dessert Shops',
             'shortName': 'Desserts',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/dessert_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c546bef1b46c9b689e291ce-11'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c8296f4d34ca14342a22d80',
           'name': 'Gorilla Exhibit',
           'location': {'lat': 43.81908012233776,
            'lng': -79.18423469237776,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81908012233776,
              'lng': -79.18423469237776}],
            'distance': 1601,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c8296f4d34ca14342a22d80-12'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c97ac2782b56dcb0fceebaa',
           'name': 'Americas Pavillon',
           'location': {'lat': 43.82208270116038,
            'lng': -79.18566515327035,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.82208270116038,
              'lng': -79.18566515327035}],
            'distance': 1850,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c97ac2782b56dcb0fceebaa-13'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bccf9bf511f9521ce0eb4c7',
           'name': 'Fratelli Village Pizzeria',
           'location': {'address': '384 Old Kingston Road',
            'crossStreet': 'McMorrish Rd',
            'lat': 43.784008053246104,
            'lng': -79.16978707527669,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.784008053246104,
              'lng': -79.16978707527669}],
            'distance': 3204,
            'postalCode': 'M1C 1B6',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['384 Old Kingston Road (McMorrish Rd)',
             'Toronto ON M1C 1B6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d110941735',
             'name': 'Italian Restaurant',
             'pluralName': 'Italian Restaurants',
             'shortName': 'Italian',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/italian_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bccf9bf511f9521ce0eb4c7-14'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c829dded92ea093eb7f4c72',
           'name': 'Lion Exhibit',
           'location': {'lat': 43.81922816181858,
            'lng': -79.18697728292929,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81922816181858,
              'lng': -79.18697728292929}],
            'distance': 1516,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c829dded92ea093eb7f4c72-15'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c77d56293faa093bbfcf1fb',
           'name': 'Glen Rouge Campground',
           'location': {'address': '7450 Kingston Rd.',
            'lat': 43.80316668151155,
            'lng': -79.15518309247824,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80316668151155,
              'lng': -79.15518309247824}],
            'distance': 3171,
            'postalCode': 'M1B',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['7450 Kingston Rd.', 'Toronto ON M1B', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e4941735',
             'name': 'Campground',
             'pluralName': 'Campgrounds',
             'shortName': 'Campground',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/parks_outdoors/campground_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c77d56293faa093bbfcf1fb-16'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4e78df9862e1b76aa3e399f4',
           'name': 'Giraffe Exhibit',
           'location': {'lat': 43.81985111905179,
            'lng': -79.18669214543897,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81985111905179,
              'lng': -79.18669214543897}],
            'distance': 1589,
            'cc': 'CA',
            'state': 'Ontario',
            'country': 'Canada',
            'formattedAddress': ['Ontario', 'Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4e78df9862e1b76aa3e399f4-17'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c5ca3d1d25320a102dcc37a',
           'name': "Mona's Roti",
           'location': {'address': '4810 Sheppard ave. East unit 209',
            'crossStreet': 'Mccowan',
            'lat': 43.79161325329546,
            'lng': -79.25101515799338,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79161325329546,
              'lng': -79.25101515799338}],
            'distance': 4851,
            'postalCode': 'M1s4n6',
            'cc': 'CA',
            'neighborhood': 'Agincourt',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4810 Sheppard ave. East unit 209 (Mccowan)',
             'Toronto ON M1s4n6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d144941735',
             'name': 'Caribbean Restaurant',
             'pluralName': 'Caribbean Restaurants',
             'shortName': 'Caribbean',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/caribbean_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c5ca3d1d25320a102dcc37a-18'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bf470256a31d13a9ec7952e',
           'name': 'The Real McCoy Burgers And Pizza',
           'location': {'address': '1021 Markham Road',
            'crossStreet': 'Brimorton',
            'lat': 43.77408136872742,
            'lng': -79.23049585681272,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77408136872742,
              'lng': -79.23049585681272}],
            'distance': 4648,
            'postalCode': 'M1K 2Y5',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['1021 Markham Road (Brimorton)',
             'Toronto ON M1K 2Y5',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16c941735',
             'name': 'Burger Joint',
             'pluralName': 'Burger Joints',
             'shortName': 'Burgers',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/burger_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bf470256a31d13a9ec7952e-19'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c8d05a3ed3ab60cb1b76c21',
           'name': 'Honey B Hives Restaurant',
           'location': {'address': '2816 Markham Road',
            'crossStreet': 'Markham and McNicoll',
            'lat': 43.822721521694945,
            'lng': -79.24825866190741,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.822721521694945,
              'lng': -79.24825866190741}],
            'distance': 4683,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2816 Markham Road (Markham and McNicoll)',
             'Toronto ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16c941735',
             'name': 'Burger Joint',
             'pluralName': 'Burger Joints',
             'shortName': 'Burgers',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/burger_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c8d05a3ed3ab60cb1b76c21-20'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4ba164fdf964a52039b337e3',
           'name': 'Bulk Barn',
           'location': {'address': '4525 Kingston Rd',
            'crossStreet': 'Morningside Crossing',
            'lat': 43.77134173380578,
            'lng': -79.1843408346176,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77134173380578,
              'lng': -79.1843408346176}],
            'distance': 4015,
            'cc': 'CA',
            'city': 'West Hill',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4525 Kingston Rd (Morningside Crossing)',
             'West Hill ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1f9941735',
             'name': 'Food & Drink Shop',
             'pluralName': 'Food & Drink Shops',
             'shortName': 'Food & Drink',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/foodanddrink_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4ba164fdf964a52039b337e3-21'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b3a9504f964a520646a25e3',
           'name': 'LCBO',
           'location': {'address': '4525 Kingston Rd.',
            'crossStreet': 'at Lawrence Ave. E',
            'lat': 43.77146181777272,
            'lng': -79.18438374996185,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77146181777272,
              'lng': -79.18438374996185}],
            'distance': 4002,
            'postalCode': 'M1E 2P1',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4525 Kingston Rd. (at Lawrence Ave. E)',
             'Toronto ON M1E 2P1',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d186941735',
             'name': 'Liquor Store',
             'pluralName': 'Liquor Stores',
             'shortName': 'Liquor Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/food_liquor_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b3a9504f964a520646a25e3-22'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c4b8f0e9c8d2d7f5955196b',
           'name': 'Tim Hortons',
           'location': {'address': '1150 Markham Rd',
            'crossStreet': 'at Ellesmere Rd.',
            'lat': 43.77599190613985,
            'lng': -79.23213511705399,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77599190613985,
              'lng': -79.23213511705399}],
            'distance': 4570,
            'postalCode': 'M1H 2Y6',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['1150 Markham Rd (at Ellesmere Rd.)',
             'Scarborough ON M1H 2Y6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c4b8f0e9c8d2d7f5955196b-23'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b96e31cf964a5207deb34e3',
           'name': 'Shamrock Burgers',
           'location': {'address': '6070 Old Kingston Rd.',
            'lat': 43.78382252268771,
            'lng': -79.16840631604676,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.78382252268771,
              'lng': -79.16840631604676}],
            'distance': 3290,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['6070 Old Kingston Rd.',
             'Scarborough ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16c941735',
             'name': 'Burger Joint',
             'pluralName': 'Burger Joints',
             'shortName': 'Burgers',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/burger_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b96e31cf964a5207deb34e3-24'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bacd8e3f964a52080113be3',
           'name': 'Babu Catering & Take Out',
           'location': {'address': '4800 Sheppard Ave. E',
            'crossStreet': 'btwn McCowan & Shorting Rd.',
            'lat': 43.791720827884255,
            'lng': -79.25113186858357,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.791720827884255,
              'lng': -79.25113186858357}],
            'distance': 4856,
            'postalCode': 'M1S 4N5',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4800 Sheppard Ave. E (btwn McCowan & Shorting Rd.)',
             'Toronto ON M1S 4N5',
             'Canada']},
           'categories': [{'id': '5413605de4b0ae91d18581a9',
             'name': 'Sri Lankan Restaurant',
             'pluralName': 'Sri Lankan Restaurants',
             'shortName': 'Sri Lankan',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/default_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bacd8e3f964a52080113be3-25'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '545ecf75498ec51130da75e0',
           'name': 'Shoppers Drug Mart',
           'location': {'address': '1400 Neilson Rd',
            'lat': 43.80961,
            'lng': -79.222729,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80961,
              'lng': -79.222729}],
            'distance': 2302,
            'postalCode': 'M1B 0C2',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['1400 Neilson Rd',
             'Scarborough ON M1B 0C2',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f951735',
             'name': 'Pharmacy',
             'pluralName': 'Pharmacies',
             'shortName': 'Pharmacy',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/pharmacy_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-545ecf75498ec51130da75e0-26'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4da09a5758c2224ba2a95679',
           'name': 'Rouge National Urban Park',
           'location': {'address': 'Scarborough',
            'lat': 43.818747220221184,
            'lng': -79.17041446182765,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.818747220221184,
              'lng': -79.17041446182765}],
            'distance': 2345,
            'cc': 'CA',
            'neighborhood': 'Rouge',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Scarborough', 'Scarborough ON', 'Canada']},
           'categories': [{'id': '52e81612bcbc57f1066b7a21',
             'name': 'National Park',
             'pluralName': 'National Parks',
             'shortName': 'National Park',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/parks_outdoors/hikingtrail_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4da09a5758c2224ba2a95679-27'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bc366dab492d13a51b2a860',
           'name': 'Chick-N-Joy',
           'location': {'address': '4449 Kingston Road',
            'crossStreet': 'at Lawrence and Morningside',
            'lat': 43.76875171771289,
            'lng': -79.18798174616069,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.76875171771289,
              'lng': -79.18798174616069}],
            'distance': 4253,
            'postalCode': 'M1E 2N7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4449 Kingston Road (at Lawrence and Morningside)',
             'Scarborough ON M1E 2N7',
             'Canada']},
           'categories': [{'id': '4d4ae6fc7a7b7dea34424761',
             'name': 'Fried Chicken Joint',
             'pluralName': 'Fried Chicken Joints',
             'shortName': 'Fried Chicken',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/friedchicken_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bc366dab492d13a51b2a860-28'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4be6c179d4f7c9b665042720',
           'name': "Ted's Restaurant",
           'location': {'address': '404 Old Kingston Rd.',
            'lat': 43.78446796744621,
            'lng': -79.1692004571639,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.78446796744621,
              'lng': -79.1692004571639}],
            'distance': 3194,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['404 Old Kingston Rd.',
             'Scarborough ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d143941735',
             'name': 'Breakfast Spot',
             'pluralName': 'Breakfast Spots',
             'shortName': 'Breakfast',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/breakfast_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4be6c179d4f7c9b665042720-29'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4d8f78f6d4ec8cfa37728c89',
           'name': 'Tundra Trek',
           'location': {'lat': 43.8225339429127,
            'lng': -79.18455758101858,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.8225339429127,
              'lng': -79.18455758101858}],
            'distance': 1931,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4d8f78f6d4ec8cfa37728c89-30'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b340050f964a520b42325e3',
           'name': 'The Keg Steakhouse + Bar',
           'location': {'address': '60 Estate Drive',
            'lat': 43.782645987776526,
            'lng': -79.23484210051811,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.782645987776526,
              'lng': -79.23484210051811}],
            'distance': 4212,
            'postalCode': 'M1H 2Z1',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['60 Estate Drive',
             'Scarborough ON M1H 2Z1',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1cc941735',
             'name': 'Steakhouse',
             'pluralName': 'Steakhouses',
             'shortName': 'Steakhouse',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/steakhouse_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b340050f964a520b42325e3-31'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4afdfbeef964a520b52c22e3',
           'name': 'Black Dog Pub',
           'location': {'address': '87 Island Rd',
            'crossStreet': 'at East Ave',
            'lat': 43.79767416844248,
            'lng': -79.13933809219287,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79767416844248,
              'lng': -79.13933809219287}],
            'distance': 4532,
            'postalCode': 'M1C 2P6',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['87 Island Rd (at East Ave)',
             'Toronto ON M1C 2P6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d11b941735',
             'name': 'Pub',
             'pluralName': 'Pubs',
             'shortName': 'Pub',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/nightlife/pub_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4afdfbeef964a520b52c22e3-32'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bb50f8aef159c74a83574f7',
           'name': 'Shoppers Drug Mart',
           'location': {'address': '91 Rylander Blvd,Unit 1022',
            'lat': 43.797641,
            'lng': -79.150208,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.797641,
              'lng': -79.150208}],
            'distance': 3686,
            'postalCode': 'M1B 4X3',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['91 Rylander Blvd,Unit 1022',
             'Scarborough ON M1B 4X3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f951735',
             'name': 'Pharmacy',
             'pluralName': 'Pharmacies',
             'shortName': 'Pharmacy',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/pharmacy_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bb50f8aef159c74a83574f7-33'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b914562f964a520d4ae33e3',
           'name': 'Caribbean Wave',
           'location': {'address': '875 Milner Ave',
            'crossStreet': 'Milner and Morningside',
            'lat': 43.798557859976256,
            'lng': -79.19577725412623,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.798557859976256,
              'lng': -79.19577725412623}],
            'distance': 912,
            'postalCode': 'M1B',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['875 Milner Ave (Milner and Morningside)',
             'Toronto ON M1B',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d144941735',
             'name': 'Caribbean Restaurant',
             'pluralName': 'Caribbean Restaurants',
             'shortName': 'Caribbean',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/caribbean_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b914562f964a520d4ae33e3-34'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c5a19e22091a59356bc5ed0',
           'name': 'Best Western Plus Executive Inn',
           'location': {'address': '38 Estate Dr',
            'lat': 43.7836566,
            'lng': -79.2375119,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7836566,
              'lng': -79.2375119}],
            'distance': 4312,
            'postalCode': 'M1H 2Z1',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['38 Estate Dr', 'Toronto ON M1H 2Z1', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1fa931735',
             'name': 'Hotel',
             'pluralName': 'Hotels',
             'shortName': 'Hotel',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/travel/hotel_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c5a19e22091a59356bc5ed0-35'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bb37b1b4019a593c9f937b8',
           'name': 'LCBO',
           'location': {'address': '785 Milner Ave.',
            'crossStreet': 'at Cinemart Dr.',
            'lat': 43.796671124927286,
            'lng': -79.20458602673877,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.796671124927286,
              'lng': -79.20458602673877}],
            'distance': 1385,
            'postalCode': 'M1B 3C3',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['785 Milner Ave. (at Cinemart Dr.)',
             'Toronto ON M1B 3C3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d186941735',
             'name': 'Liquor Store',
             'pluralName': 'Liquor Stores',
             'shortName': 'Liquor Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/food_liquor_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bb37b1b4019a593c9f937b8-36'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4d570727fb65236a7f600db4',
           'name': 'Silver Spoon Pak-Indian Restaurant',
           'location': {'lat': 43.79192991300102,
            'lng': -79.25125257024139,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79192991300102,
              'lng': -79.25125257024139}],
            'distance': 4857,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f941735',
             'name': 'Indian Restaurant',
             'pluralName': 'Indian Restaurants',
             'shortName': 'Indian',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/indian_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4d570727fb65236a7f600db4-37'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4db32160a86e8d2707697afd',
           'name': 'Lindt Outlet Boutique',
           'location': {'address': '2250 Markham Road',
            'crossStreet': 'Just South of Finch Avenue East',
            'lat': 43.81098123769522,
            'lng': -79.2441752718326,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81098123769522,
              'lng': -79.2441752718326}],
            'distance': 4030,
            'postalCode': 'M1B 2W4',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2250 Markham Road (Just South of Finch Avenue East)',
             'Scarborough ON M1B 2W4',
             'Canada']},
           'categories': [{'id': '52f2ab2ebcbc57f1066b8b31',
             'name': 'Chocolate Shop',
             'pluralName': 'Chocolate Shops',
             'shortName': 'Chocolate Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/candystore_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4db32160a86e8d2707697afd-38'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4fcba458754a63325ee554c4',
           'name': 'Highland Creek',
           'location': {'lat': 43.790281030437924,
            'lng': -79.17370319366455,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.790281030437924,
              'lng': -79.17370319366455}],
            'distance': 2467,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Scarborough ON', 'Canada']},
           'categories': [{'id': '4f2a25ac4b909258e854f55f',
             'name': 'Neighborhood',
             'pluralName': 'Neighborhoods',
             'shortName': 'Neighborhood',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/parks_outdoors/neighborhood_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4fcba458754a63325ee554c4-39'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c347d5566e40f47f88fc98b',
           'name': 'Petro-Canada',
           'location': {'address': '3100 Ellesmere Rd',
            'crossStreet': 'at Morningside Ave.',
            'lat': 43.784984,
            'lng': -79.194923,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.784984,
              'lng': -79.194923}],
            'distance': 2416,
            'postalCode': 'M1E 4C2',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['3100 Ellesmere Rd (at Morningside Ave.)',
             'Scarborough ON M1E 4C2',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d113951735',
             'name': 'Gas Station',
             'pluralName': 'Gas Stations',
             'shortName': 'Gas Station',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/gas_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c347d5566e40f47f88fc98b-40'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bab7deef964a5209fad3ae3',
           'name': 'Long & McQuade',
           'location': {'address': '1133 Markham Rd.',
            'lat': 43.77590298228139,
            'lng': -79.23096539347517,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77590298228139,
              'lng': -79.23096539347517}],
            'distance': 4516,
            'postalCode': 'M1H 2Y5',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['1133 Markham Rd.',
             'Scarborough ON M1H 2Y5',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1fe941735',
             'name': 'Music Store',
             'pluralName': 'Music Stores',
             'shortName': 'Music Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/music_instruments_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bab7deef964a5209fad3ae3-41'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b59bb58f964a5201a9528e3',
           'name': 'No Frills',
           'location': {'address': '70 Island Rd',
            'crossStreet': 'Port Union Rd.',
            'lat': 43.798476,
            'lng': -79.141303,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.798476,
              'lng': -79.141303}],
            'distance': 4359,
            'postalCode': 'M1C 2P5',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['70 Island Rd (Port Union Rd.)',
             'Scarborough ON M1C 2P5',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d118951735',
             'name': 'Grocery Store',
             'pluralName': 'Grocery Stores',
             'shortName': 'Grocery Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/food_grocery_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b59bb58f964a5201a9528e3-42'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4af7835cf964a520a90922e3',
           'name': 'Beauty Boutique by Shoppers Drug Mart',
           'location': {'address': '265 Port Union Rd',
            'lat': 43.78909,
            'lng': -79.139695,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.78909,
              'lng': -79.139695}],
            'distance': 4808,
            'postalCode': 'M1C 2L3',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['265 Port Union Rd',
             'Scarborough ON M1C 2L3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10c951735',
             'name': 'Cosmetics Shop',
             'pluralName': 'Cosmetics Shops',
             'shortName': 'Cosmetics',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/beauty_cosmetic_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4af7835cf964a520a90922e3-43'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '540880cb498eb86517fc02ee',
           'name': 'Starbucks',
           'location': {'address': '1265 Military Trl',
            'lat': 43.783821,
            'lng': -79.18749,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.783821,
              'lng': -79.18749}],
            'distance': 2604,
            'postalCode': 'M1C 1A4',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['1265 Military Trl',
             'Toronto ON M1C 1A4',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-540880cb498eb86517fc02ee-44'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c9fdb04542b224bca4201a0',
           'name': 'Little Caesars Pizza',
           'location': {'address': '4218 Lawrence Avenue East',
            'lat': 43.76904597684398,
            'lng': -79.18438601716002,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.76904597684398,
              'lng': -79.18438601716002}],
            'distance': 4265,
            'postalCode': 'M1E 4X9',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4218 Lawrence Avenue East',
             'Scarborough ON M1E 4X9',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1ca941735',
             'name': 'Pizza Place',
             'pluralName': 'Pizza Places',
             'shortName': 'Pizza',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/pizza_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c9fdb04542b224bca4201a0-45'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b46755ff964a520ac2126e3',
           'name': "Coppa's Fresh Market",
           'location': {'address': '148 Bennett Rd',
            'crossStreet': 'Lawrence Ave East',
            'lat': 43.772094259953064,
            'lng': -79.16634033015073,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.772094259953064,
              'lng': -79.16634033015073}],
            'distance': 4460,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['148 Bennett Rd (Lawrence Ave East)',
             'Scarborough ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d118951735',
             'name': 'Grocery Store',
             'pluralName': 'Grocery Stores',
             'shortName': 'Grocery Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/food_grocery_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b46755ff964a520ac2126e3-46'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bc0bfdeabf49521a0c9bf93',
           'name': 'Popeyes Louisiana Kitchen',
           'location': {'address': '790 Military Trail',
            'crossStreet': 'at Morningside Ave.',
            'lat': 43.79004934105916,
            'lng': -79.19524795280122,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79004934105916,
              'lng': -79.19524795280122}],
            'distance': 1853,
            'postalCode': 'M1E 4P7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['790 Military Trail (at Morningside Ave.)',
             'Scarborough ON M1E 4P7',
             'Canada']},
           'categories': [{'id': '4d4ae6fc7a7b7dea34424761',
             'name': 'Fried Chicken Joint',
             'pluralName': 'Fried Chicken Joints',
             'shortName': 'Fried Chicken',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/friedchicken_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bc0bfdeabf49521a0c9bf93-47'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4cbb2e2fa33bb1f70bbb92fd',
           'name': 'Petro-Canada',
           'location': {'address': '9501 Sheppard Ave E',
            'lat': 43.807831,
            'lng': -79.171431,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.807831,
              'lng': -79.171431}],
            'distance': 1845,
            'postalCode': 'M1B 5R9',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['9501 Sheppard Ave E',
             'Scarborough ON M1B 5R9',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d113951735',
             'name': 'Gas Station',
             'pluralName': 'Gas Stations',
             'shortName': 'Gas Station',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/gas_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4cbb2e2fa33bb1f70bbb92fd-48'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4dda6bc7fa76ad96d16b05c8',
           'name': 'African Penguins',
           'location': {'lat': 43.81949188404824,
            'lng': -79.18596866560624,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81949188404824,
              'lng': -79.18596866560624}],
            'distance': 1576,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON', 'Canada']},
           'categories': [{'id': '58daa1558bbb0b01f18ec1fd',
             'name': 'Zoo Exhibit',
             'pluralName': 'Zoo Exhibits',
             'shortName': 'Zoo Exhibit',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/arts_entertainment/zoo_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4dda6bc7fa76ad96d16b05c8-49'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4beca2f9d6e676b0538764d4',
           'name': 'Booster Juice',
           'location': {'address': '4525 Kingston Road, Unit #H8',
            'crossStreet': 'at Collinsgrove Rd.',
            'lat': 43.77066813,
            'lng': -79.18415042,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77066813,
              'lng': -79.18415042}],
            'distance': 4092,
            'postalCode': 'M1E 2P1',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4525 Kingston Road, Unit #H8 (at Collinsgrove Rd.)',
             'Scarborough ON M1E 2P1',
             'Canada']},
           'categories': [{'id': '52f2ab2ebcbc57f1066b8b41',
             'name': 'Smoothie Shop',
             'pluralName': 'Smoothie Shops',
             'shortName': 'Smoothie Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/juicebar_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4beca2f9d6e676b0538764d4-50'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '51955209498ef3356d12adcc',
           'name': 'Menchies',
           'location': {'lat': 43.797870210197416,
            'lng': -79.14950945831252,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.797870210197416,
              'lng': -79.14950945831252}],
            'distance': 3734,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '4bf58dd8d48988d1c9941735',
             'name': 'Ice Cream Shop',
             'pluralName': 'Ice Cream Shops',
             'shortName': 'Ice Cream',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/icecream_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-51955209498ef3356d12adcc-51'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4cbdc9f8f50e224b03a106fc',
           'name': 'TD Canada Trust',
           'location': {'address': '49 Lapsley Rd',
            'crossStreet': 'Sheppard Ave E',
            'lat': 43.7960168,
            'lng': -79.2261009,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7960168,
              'lng': -79.2261009}],
            'distance': 2813,
            'postalCode': 'M1B 1K1',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['49 Lapsley Rd (Sheppard Ave E)',
             'Scarborough ON M1B 1K1',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10a951735',
             'name': 'Bank',
             'pluralName': 'Banks',
             'shortName': 'Bank',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/financial_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4cbdc9f8f50e224b03a106fc-52'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '510bd6f1e4b0256d6cc14409',
           'name': 'Sunset Grill',
           'location': {'address': '4551 Kingston Rd.',
            'crossStreet': 'Lawrence',
            'lat': 43.77231854994461,
            'lng': -79.18490011736371,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77231854994461,
              'lng': -79.18490011736371}],
            'distance': 3900,
            'postalCode': '4551 Kingsto',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4551 Kingston Rd. (Lawrence)',
             'Toronto ON 4551 Kingsto',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d143941735',
             'name': 'Breakfast Spot',
             'pluralName': 'Breakfast Spots',
             'shortName': 'Breakfast',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/breakfast_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-510bd6f1e4b0256d6cc14409-53'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '579a91b3498e9bd833afa78a',
           'name': "Wendy's",
           'location': {'address': '8129 Sheppard Avenue',
            'lat': 43.8020084,
            'lng': -79.1980797,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.8020084,
              'lng': -79.1980797}],
            'distance': 600,
            'postalCode': 'M1B 6A3',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['8129 Sheppard Avenue',
             'Scarborough ON M1B 6A3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16e941735',
             'name': 'Fast Food Restaurant',
             'pluralName': 'Fast Food Restaurants',
             'shortName': 'Fast Food',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/fastfood_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-579a91b3498e9bd833afa78a-54'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c68119de1da1b8d45179fc3',
           'name': 'Subway',
           'location': {'address': '31 Tapscott Rd',
            'crossStreet': 'Neilson Rd',
            'lat': 43.80680496572125,
            'lng': -79.2225154816595,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80680496572125,
              'lng': -79.2225154816595}],
            'distance': 2262,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['31 Tapscott Rd (Neilson Rd)',
             'Toronto ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1c5941735',
             'name': 'Sandwich Place',
             'pluralName': 'Sandwich Places',
             'shortName': 'Sandwiches',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/deli_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c68119de1da1b8d45179fc3-55'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4ba6f126f964a520ee7839e3',
           'name': 'Pizza Pizza',
           'location': {'address': '9390 SHEPPARD AVENUE EAST',
            'lat': 43.80661280665733,
            'lng': -79.17844533920288,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80661280665733,
              'lng': -79.17844533920288}],
            'distance': 1278,
            'postalCode': 'M1B 2Y7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['9390 SHEPPARD AVENUE EAST',
             'Scarborough ON M1B 2Y7',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1ca941735',
             'name': 'Pizza Place',
             'pluralName': 'Pizza Places',
             'shortName': 'Pizza',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/pizza_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4ba6f126f964a520ee7839e3-56'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '54a6ea76498ebc906c8c3652',
           'name': 'Hakka Legend',
           'location': {'address': '2058 Ellesmere Road',
            'lat': 43.77630936532644,
            'lng': -79.23493865172834,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77630936532644,
              'lng': -79.23493865172834}],
            'distance': 4697,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2058 Ellesmere Road',
             'Scarborough ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d145941735',
             'name': 'Chinese Restaurant',
             'pluralName': 'Chinese Restaurants',
             'shortName': 'Chinese',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/asian_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-54a6ea76498ebc906c8c3652-57'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c3cb1c7b169c9b6ab0f4668',
           'name': 'Food Basics',
           'location': {'address': '2900 Ellesmere Road',
            'crossStreet': 'Neilson Rd.',
            'lat': 43.786553933465264,
            'lng': -79.20534287670463,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.786553933465264,
              'lng': -79.20534287670463}],
            'distance': 2408,
            'postalCode': 'M1E 4B8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2900 Ellesmere Road (Neilson Rd.)',
             'Scarborough ON M1E 4B8',
             'Canada']},
           'categories': [{'id': '52f2ab2ebcbc57f1066b8b46',
             'name': 'Supermarket',
             'pluralName': 'Supermarkets',
             'shortName': 'Supermarket',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/food_grocery_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c3cb1c7b169c9b6ab0f4668-58'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bd3741777b29c743ee89082',
           'name': "McDonald's",
           'location': {'address': '7431 Kingston Road',
            'lat': 43.80027187464014,
            'lng': -79.14340995469388,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80027187464014,
              'lng': -79.14340995469388}],
            'distance': 4154,
            'postalCode': 'M1B 5S3',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['7431 Kingston Road',
             'Scarborough ON M1B 5S3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16e941735',
             'name': 'Fast Food Restaurant',
             'pluralName': 'Fast Food Restaurants',
             'shortName': 'Fast Food',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/fastfood_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bd3741777b29c743ee89082-59'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b6718c2f964a5203f3a2be3',
           'name': "Harvey's",
           'location': {'address': '853 Milner Ave',
            'crossStreet': 'at Morningside Ave',
            'lat': 43.80010575211872,
            'lng': -79.19825833589329,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80010575211872,
              'lng': -79.19825833589329}],
            'distance': 796,
            'postalCode': 'M1B 5N6',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['853 Milner Ave (at Morningside Ave)',
             'Scarborough ON M1B 5N6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16e941735',
             'name': 'Fast Food Restaurant',
             'pluralName': 'Fast Food Restaurants',
             'shortName': 'Fast Food',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/fastfood_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b6718c2f964a5203f3a2be3-60'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c880ad1da5da1cd70f030e9',
           'name': 'Dollarama',
           'location': {'address': '2900 Ellesmere Rd,Centenary Plaza',
            'crossStreet': 'Neilson Road',
            'lat': 43.783187,
            'lng': -79.202538,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.783187,
              'lng': -79.202538}],
            'distance': 2697,
            'postalCode': 'M1E 4B8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2900 Ellesmere Rd,Centenary Plaza (Neilson Road)',
             'Scarborough ON M1E 4B8',
             'Canada']},
           'categories': [{'id': '52dea92d3cf9994f4e043dbb',
             'name': 'Discount Store',
             'pluralName': 'Discount Stores',
             'shortName': 'Discount Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/discountstore_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c880ad1da5da1cd70f030e9-61'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b993333f964a5203c6935e3',
           'name': 'Malvern Arena',
           'location': {'lat': 43.808593521938036,
            'lng': -79.21663377206129,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.808593521938036,
              'lng': -79.21663377206129}],
            'distance': 1802,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d168941735',
             'name': 'Skating Rink',
             'pluralName': 'Skating Rinks',
             'shortName': 'Skating Rink',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/parks_outdoors/skatingrink_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b993333f964a5203c6935e3-62'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bcb612d3740b713f0606265',
           'name': 'Staples Morningside',
           'location': {'address': '850 Milner Avenue',
            'lat': 43.80028467632823,
            'lng': -79.19660657644272,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80028467632823,
              'lng': -79.19660657644272}],
            'distance': 735,
            'postalCode': 'M1B 5N7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['850 Milner Avenue',
             'Scarborough ON M1B 5N7',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d121951735',
             'name': 'Paper / Office Supplies Store',
             'pluralName': 'Paper / Office Supplies Stores',
             'shortName': 'Office Supplies',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/papergoods_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bcb612d3740b713f0606265-63'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4afd8b76f964a520762822e3',
           'name': 'Markham Station Restaurant',
           'location': {'address': '5117 Sheppard Ave. E',
            'crossStreet': 'at Markham Rd.',
            'lat': 43.79264410001942,
            'lng': -79.23847252989981,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79264410001942,
              'lng': -79.23847252989981}],
            'distance': 3874,
            'postalCode': 'M1S 4N8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['5117 Sheppard Ave. E (at Markham Rd.)',
             'Scarborough ON M1S 4N8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d147941735',
             'name': 'Diner',
             'pluralName': 'Diners',
             'shortName': 'Diner',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/diner_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4afd8b76f964a520762822e3-64'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4cc1d28c06c254815ac18547',
           'name': 'Starbucks',
           'location': {'address': '300 Borough Dr',
            'crossStreet': 'Scarborough Town Centre',
            'lat': 43.770037201625215,
            'lng': -79.22115586641958,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.770037201625215,
              'lng': -79.22115586641958}],
            'distance': 4613,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['300 Borough Dr (Scarborough Town Centre)',
             'Scarborough ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4cc1d28c06c254815ac18547-65'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4de678298877a085f8ca16fe',
           'name': 'Booster Juice',
           'location': {'address': '4525 Kingston Rd',
            'crossStreet': 'Morningside Ave',
            'lat': 43.76615937955718,
            'lng': -79.20582062504174,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.76615937955718,
              'lng': -79.20582062504174}],
            'distance': 4604,
            'postalCode': 'M1E 2P1',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4525 Kingston Rd (Morningside Ave)',
             'Toronto ON M1E 2P1',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d112941735',
             'name': 'Juice Bar',
             'pluralName': 'Juice Bars',
             'shortName': 'Juice Bar',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/juicebar_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4de678298877a085f8ca16fe-66'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4cefd55828abb60c05c8c409',
           'name': 'Food Basics Pharmacy',
           'location': {'address': '5085 Sheppard Avenue East',
            'crossStreet': 'Markham Rd',
            'lat': 43.79299402531743,
            'lng': -79.24032869404621,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79299402531743,
              'lng': -79.24032869404621}],
            'distance': 3996,
            'postalCode': 'M1S 4N8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['5085 Sheppard Avenue East (Markham Rd)',
             'Scarborough ON M1S 4N8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f951735',
             'name': 'Pharmacy',
             'pluralName': 'Pharmacies',
             'shortName': 'Pharmacy',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/pharmacy_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4cefd55828abb60c05c8c409-67'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4f1daec5e4b0c74ef42b43e6',
           'name': 'Subway',
           'location': {'address': '2872 Ellesmere Rd.',
            'crossStreet': 'at Neilson Rd.',
            'lat': 43.783551620751005,
            'lng': -79.20459596922957,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.783551620751005,
              'lng': -79.20459596922957}],
            'distance': 2703,
            'postalCode': 'M1E 4B8',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2872 Ellesmere Rd. (at Neilson Rd.)',
             'Toronto ON M1E 4B8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1c5941735',
             'name': 'Sandwich Place',
             'pluralName': 'Sandwich Places',
             'shortName': 'Sandwiches',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/deli_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4f1daec5e4b0c74ef42b43e6-68'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bd33a1a77b29c74c8449082',
           'name': 'The Beer Store',
           'location': {'address': '2866 Ellesmere Rd',
            'lat': 43.7839039,
            'lng': -79.2048998,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7839039,
              'lng': -79.2048998}],
            'distance': 2673,
            'postalCode': 'M1E 4B8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2866 Ellesmere Rd',
             'Scarborough ON M1E 4B8',
             'Canada']},
           'categories': [{'id': '5370f356bcbc57f1066c94c2',
             'name': 'Beer Store',
             'pluralName': 'Beer Stores',
             'shortName': 'Beer Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/nightlife/beergarden_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bd33a1a77b29c74c8449082-69'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c3a2c23ae2da5934dcf03c6',
           'name': 'Dean Park',
           'location': {'crossStreet': 'Dean Park Road and Meadowvale',
            'lat': 43.80436379110694,
            'lng': -79.16915938899648,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80436379110694,
              'lng': -79.16915938899648}],
            'distance': 2040,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Scarborough ON', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d163941735',
             'name': 'Park',
             'pluralName': 'Parks',
             'shortName': 'Park',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/parks_outdoors/park_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c3a2c23ae2da5934dcf03c6-70'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bb6b9446edc76b0d771311c',
           'name': "Wendy's",
           'location': {'crossStreet': 'Morningside & Sheppard',
            'lat': 43.80744841934756,
            'lng': -79.19905558052072,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80744841934756,
              'lng': -79.19905558052072}],
            'distance': 387,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto ON', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16e941735',
             'name': 'Fast Food Restaurant',
             'pluralName': 'Fast Food Restaurants',
             'shortName': 'Fast Food',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/fastfood_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bb6b9446edc76b0d771311c-71'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4cb9e2d84495721e640c4d7a',
           'name': 'Pizza Hut',
           'location': {'address': '31 Tapscott Road, Unit #B8A',
            'lat': 43.80832603333603,
            'lng': -79.2206160906872,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80832603333603,
              'lng': -79.2206160906872}],
            'distance': 2117,
            'postalCode': 'M1B 4Y7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['31 Tapscott Road, Unit #B8A',
             'Scarborough ON M1B 4Y7',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1ca941735',
             'name': 'Pizza Place',
             'pluralName': 'Pizza Places',
             'shortName': 'Pizza',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/pizza_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4cb9e2d84495721e640c4d7a-72'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '519f9fc9498ea72866bcb1fd',
           'name': 'Eggsmart',
           'location': {'address': '6 Rylander Blvd.',
            'lat': 43.797979,
            'lng': -79.149207,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.797979,
              'lng': -79.149207}],
            'distance': 3754,
            'postalCode': 'M1B 0B6',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['6 Rylander Blvd.',
             'Toronto ON M1B 0B6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d143941735',
             'name': 'Breakfast Spot',
             'pluralName': 'Breakfast Spots',
             'shortName': 'Breakfast',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/breakfast_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-519f9fc9498ea72866bcb1fd-73'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4ddb992bd4c009d3c58b7857',
           'name': 'Petro-Canada',
           'location': {'address': '5110 Sheppard Ave E',
            'crossStreet': 'at Markham Rd',
            'lat': 43.793968,
            'lng': -79.239585,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.793968,
              'lng': -79.239585}],
            'distance': 3900,
            'postalCode': 'M1S 4N3',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['5110 Sheppard Ave E (at Markham Rd)',
             'Scarborough ON M1S 4N3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d113951735',
             'name': 'Gas Station',
             'pluralName': 'Gas Stations',
             'shortName': 'Gas Station',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/gas_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4ddb992bd4c009d3c58b7857-74'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bf0817e24f020a11c33684f',
           'name': 'Pizza Pizza',
           'location': {'address': '31 Tapscott Road, Unit 42A',
            'lat': 43.80661280665735,
            'lng': -79.2212426662445,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.80661280665735,
              'lng': -79.2212426662445}],
            'distance': 2160,
            'postalCode': 'M1B 4Y7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['31 Tapscott Road, Unit 42A',
             'Scarborough ON M1B 4Y7',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1ca941735',
             'name': 'Pizza Place',
             'pluralName': 'Pizza Places',
             'shortName': 'Pizza',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/pizza_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bf0817e24f020a11c33684f-75'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '5050b622e4b0d5301f66f093',
           'name': 'Mucho Burrito Fresh Mexican Grill',
           'location': {'address': '6714 Kingston Rd,',
            'crossStreet': 'Rylander',
            'lat': 43.79756,
            'lng': -79.14927,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79756,
              'lng': -79.14927}],
            'distance': 3761,
            'postalCode': 'M1B 1G8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['6714 Kingston Rd, (Rylander)',
             'Scarborough ON M1B 1G8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1c1941735',
             'name': 'Mexican Restaurant',
             'pluralName': 'Mexican Restaurants',
             'shortName': 'Mexican',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/mexican_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-5050b622e4b0d5301f66f093-76'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4af8cd0bf964a520041022e3',
           'name': "McDonald's",
           'location': {'address': '2260 Markham Road',
            'crossStreet': 'Finch Ave E',
            'lat': 43.81103124719297,
            'lng': -79.2434733548393,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.81103124719297,
              'lng': -79.2434733548393}],
            'distance': 3975,
            'postalCode': 'M1B 2W4',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2260 Markham Road (Finch Ave E)',
             'Scarborough ON M1B 2W4',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d16e941735',
             'name': 'Fast Food Restaurant',
             'pluralName': 'Fast Food Restaurants',
             'shortName': 'Fast Food',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/fastfood_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4af8cd0bf964a520041022e3-77'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '509018aae4b019e9fafaed0f',
           'name': 'Subway',
           'location': {'address': '6714 Kingston Rd. Unit 5',
            'crossStreet': 'at Rylander Ave.',
            'lat': 43.79784949354192,
            'lng': -79.14906297900698,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79784949354192,
              'lng': -79.14906297900698}],
            'distance': 3769,
            'postalCode': 'M1B 1G8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['6714 Kingston Rd. Unit 5 (at Rylander Ave.)',
             'Scarborough ON M1B 1G8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1c5941735',
             'name': 'Sandwich Place',
             'pluralName': 'Sandwich Places',
             'shortName': 'Sandwiches',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/deli_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-509018aae4b019e9fafaed0f-78'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b75e7bbf964a520992d2ee3',
           'name': 'Shoppers Drug Mart',
           'location': {'address': '255 Morningside Ave',
            'crossStreet': 'at Kingston Rd.',
            'lat': 43.770282,
            'lng': -79.185012,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.770282,
              'lng': -79.185012}],
            'distance': 4121,
            'postalCode': 'M1E 3E6',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['255 Morningside Ave (at Kingston Rd.)',
             'Scarborough ON M1E 3E6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f951735',
             'name': 'Pharmacy',
             'pluralName': 'Pharmacies',
             'shortName': 'Pharmacy',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/pharmacy_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b75e7bbf964a520992d2ee3-79'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b9926ddf964a520196535e3',
           'name': 'Subway',
           'location': {'lat': 43.7929630279541,
            'lng': -79.239847,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7929630279541,
              'lng': -79.239847}],
            'distance': 3961,
            'cc': 'CA',
            'country': 'Canada',
            'formattedAddress': ['Canada']},
           'categories': [{'id': '4bf58dd8d48988d1c5941735',
             'name': 'Sandwich Place',
             'pluralName': 'Sandwich Places',
             'shortName': 'Sandwiches',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/deli_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b9926ddf964a520196535e3-80'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c32304f3896e21e971de890',
           'name': 'Petro-Canada',
           'location': {'address': '1525 Markham Rd',
            'crossStreet': 'at Milner Ave.',
            'lat': 43.789695,
            'lng': -79.236952,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.789695,
              'lng': -79.236952}],
            'distance': 3910,
            'postalCode': 'M1B 2W1',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['1525 Markham Rd (at Milner Ave.)',
             'Scarborough ON M1B 2W1',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d113951735',
             'name': 'Gas Station',
             'pluralName': 'Gas Stations',
             'shortName': 'Gas Station',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/gas_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c32304f3896e21e971de890-81'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '5224a1b111d28e35e5688908',
           'name': 'Tim Hortons',
           'location': {'address': '2867 Ellesmere Rd',
            'crossStreet': 'Centenary Hospital',
            'lat': 43.7806719,
            'lng': -79.2057164,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7806719,
              'lng': -79.2057164}],
            'distance': 3036,
            'postalCode': 'M1E 4B9',
            'cc': 'CA',
            'neighborhood': 'Morningside',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2867 Ellesmere Rd (Centenary Hospital)',
             'Scarborough ON M1E 4B9',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-5224a1b111d28e35e5688908-82'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4f5a8a78e4b036906f46053e',
           'name': 'Starbucks',
           'location': {'address': '6714 Kingston Rd.',
            'crossStreet': 'at Rylander Blvd.',
            'lat': 43.79757973441376,
            'lng': -79.14908312372886,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.79757973441376,
              'lng': -79.14908312372886}],
            'distance': 3775,
            'postalCode': 'M1B 1G8',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['6714 Kingston Rd. (at Rylander Blvd.)',
             'Toronto ON M1B 1G8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4f5a8a78e4b036906f46053e-83'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b16e23bf964a520edbe23e3',
           'name': 'Tim Hortons',
           'location': {'address': '8129 Sheppard Ave',
            'crossStreet': 'Morningside Ave',
            'lat': 43.801999861382,
            'lng': -79.1981689631939,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.801999861382,
              'lng': -79.1981689631939}],
            'distance': 605,
            'postalCode': 'M1B 6A3',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['8129 Sheppard Ave (Morningside Ave)',
             'Scarborough ON M1B 6A3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b16e23bf964a520edbe23e3-84'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b6074e3f964a5200fe729e3',
           'name': 'Swiss Chalet Rotisserie & Grill',
           'location': {'address': '4410 Kingston Rd',
            'lat': 43.76769708292701,
            'lng': -79.1899135003439,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.76769708292701,
              'lng': -79.1899135003439}],
            'distance': 4354,
            'postalCode': 'M1E 2N5',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4410 Kingston Rd',
             'Scarborough ON M1E 2N5',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1ca941735',
             'name': 'Pizza Place',
             'pluralName': 'Pizza Places',
             'shortName': 'Pizza',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/pizza_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b6074e3f964a5200fe729e3-85'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c77fc87bd346dcb8c90f0ef',
           'name': 'La Sani Grill',
           'location': {'address': '2058 Ellesmere Rd, Unit 3',
            'lat': 43.776214262045,
            'lng': -79.23484801455352,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.776214262045,
              'lng': -79.23484801455352}],
            'distance': 4700,
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2058 Ellesmere Rd, Unit 3',
             'Toronto ON',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f941735',
             'name': 'Indian Restaurant',
             'pluralName': 'Indian Restaurants',
             'shortName': 'Indian',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/indian_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c77fc87bd346dcb8c90f0ef-86'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c23612211de20a10c4986ce',
           'name': 'Shoppers Drug Mart',
           'location': {'address': '31 Tapscott Road',
            'crossStreet': 'Neilson Rd',
            'lat': 43.8064889218881,
            'lng': -79.2230236530304,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.8064889218881,
              'lng': -79.2230236530304}],
            'distance': 2303,
            'postalCode': 'M1B 4Y7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['31 Tapscott Road (Neilson Rd)',
             'Scarborough ON M1B 4Y7',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f951735',
             'name': 'Pharmacy',
             'pluralName': 'Pharmacies',
             'shortName': 'Pharmacy',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/pharmacy_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c23612211de20a10c4986ce-87'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bf025afc8d920a1bd799430',
           'name': 'Fairview Seafood Chinese Cuisine',
           'location': {'crossStreet': 'Markham Rd and Sheppard Ave E',
            'lat': 43.7929068448252,
            'lng': -79.23934784822218,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7929068448252,
              'lng': -79.23934784822218}],
            'distance': 3927,
            'cc': 'CA',
            'city': 'Toronto Division',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['Toronto Division ON', 'Canada']},
           'categories': [{'id': '4bf58dd8d48988d145941735',
             'name': 'Chinese Restaurant',
             'pluralName': 'Chinese Restaurants',
             'shortName': 'Chinese',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/asian_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bf025afc8d920a1bd799430-88'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c23737b502b952193346e21',
           'name': 'Shoppers Drug Mart',
           'location': {'address': '2863 Ellesmere Rd,Suite 201',
            'crossStreet': 'Centenary Hospital',
            'lat': 43.780599,
            'lng': -79.205009,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.780599,
              'lng': -79.205009}],
            'distance': 3027,
            'postalCode': 'M1E 5E9',
            'cc': 'CA',
            'neighborhood': 'Morningside',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['2863 Ellesmere Rd,Suite 201 (Centenary Hospital)',
             'Scarborough ON M1E 5E9',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10f951735',
             'name': 'Pharmacy',
             'pluralName': 'Pharmacies',
             'shortName': 'Pharmacy',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/pharmacy_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c23737b502b952193346e21-89'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b06eb1cf964a52005f322e3',
           'name': 'Starbucks',
           'location': {'address': '255 Morningside Ave',
            'crossStreet': 'Kingston Rd',
            'lat': 43.77037,
            'lng': -79.18649,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77037,
              'lng': -79.18649}],
            'distance': 4091,
            'postalCode': 'M1E 3E6',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['255 Morningside Ave (Kingston Rd)',
             'Toronto ON M1E 3E6',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b06eb1cf964a52005f322e3-90'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bc78a846501c9b653a13e29',
           'name': 'TD Canada Trust',
           'location': {'address': '299 Port Union Road',
            'lat': 43.7895977,
            'lng': -79.1404776,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.7895977,
              'lng': -79.1404776}],
            'distance': 4728,
            'postalCode': 'M1C 2L3',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['299 Port Union Road',
             'Scarborough ON M1C 2L3',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10a951735',
             'name': 'Bank',
             'pluralName': 'Banks',
             'shortName': 'Bank',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/financial_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bc78a846501c9b653a13e29-91'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4c3fb24ace54e21ee181081a',
           'name': 'Petro-Canada',
           'location': {'address': '900 Progress Ave',
            'crossStreet': 'at Markham Rd',
            'lat': 43.782135,
            'lng': -79.234784,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.782135,
              'lng': -79.234784}],
            'distance': 4245,
            'postalCode': 'M1H 2Z9',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['900 Progress Ave (at Markham Rd)',
             'Scarborough ON M1H 2Z9',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d113951735',
             'name': 'Gas Station',
             'pluralName': 'Gas Stations',
             'shortName': 'Gas Station',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/gas_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4c3fb24ace54e21ee181081a-92'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '58278ca9d1efa65794fd4fd5',
           'name': 'Popeyes Louisiana Kitchen',
           'location': {'address': '6 Rylander Blvd #6',
            'lat': 43.797597,
            'lng': -79.149406,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.797597,
              'lng': -79.149406}],
            'distance': 3750,
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['6 Rylander Blvd #6',
             'Scarborough ON',
             'Canada']},
           'categories': [{'id': '4d4ae6fc7a7b7dea34424761',
             'name': 'Fried Chicken Joint',
             'pluralName': 'Fried Chicken Joints',
             'shortName': 'Fried Chicken',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/friedchicken_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-58278ca9d1efa65794fd4fd5-93'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bdcd893462b2d7f13a3113c',
           'name': 'The Beer Store',
           'location': {'address': '4479 Kingston Rd Unit 1',
            'crossStreet': 'btw Morningside & Lawrence',
            'lat': 43.769793,
            'lng': -79.1875054,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.769793,
              'lng': -79.1875054}],
            'distance': 4143,
            'postalCode': 'M1E 2N7',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4479 Kingston Rd Unit 1 (btw Morningside & Lawrence)',
             'Scarborough ON M1E 2N7',
             'Canada']},
           'categories': [{'id': '5370f356bcbc57f1066c94c2',
             'name': 'Beer Store',
             'pluralName': 'Beer Stores',
             'shortName': 'Beer Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/nightlife/beergarden_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bdcd893462b2d7f13a3113c-94'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4e1ddeca18a8e423cd59a14e',
           'name': 'Tim Hortons',
           'location': {'address': '941 Progress Rd',
            'crossStreet': 'Centennial College',
            'lat': 43.78480874561627,
            'lng': -79.2273447288361,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.78480874561627,
              'lng': -79.2273447288361}],
            'distance': 3599,
            'postalCode': 'M1G 3T8',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['941 Progress Rd (Centennial College)',
             'Scarborough ON M1G 3T8',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1e0931735',
             'name': 'Coffee Shop',
             'pluralName': 'Coffee Shops',
             'shortName': 'Coffee Shop',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/coffeeshop_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4e1ddeca18a8e423cd59a14e-95'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bd22faacaff9521f94cd2f0',
           'name': 'Dollarama',
           'location': {'address': '4525 Kingston Rd,Morningside Mall',
            'crossStreet': 'Morningside Crossing',
            'lat': 43.771085,
            'lng': -79.184288,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.771085,
              'lng': -79.184288}],
            'distance': 4044,
            'postalCode': 'M1E 2P1',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4525 Kingston Rd,Morningside Mall (Morningside Crossing)',
             'Toronto ON M1E 2P1',
             'Canada']},
           'categories': [{'id': '52dea92d3cf9994f4e043dbb',
             'name': 'Discount Store',
             'pluralName': 'Discount Stores',
             'shortName': 'Discount Store',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/discountstore_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bd22faacaff9521f94cd2f0-96'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4bcb5d75937ca593956ba992',
           'name': 'Subway',
           'location': {'address': '4545 Kingston Rd',
            'crossStreet': 'Morningside Crossing',
            'lat': 43.771913360495205,
            'lng': -79.18547467639696,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.771913360495205,
              'lng': -79.18547467639696}],
            'distance': 3936,
            'postalCode': 'M1E 2P1',
            'cc': 'CA',
            'city': 'Toronto',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4545 Kingston Rd (Morningside Crossing)',
             'Toronto ON M1E 2P1',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d1c5941735',
             'name': 'Sandwich Place',
             'pluralName': 'Sandwich Places',
             'shortName': 'Sandwiches',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/food/deli_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4bcb5d75937ca593956ba992-97'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4b931d41f964a520d43534e3',
           'name': 'Centennial Recreation Centre',
           'location': {'address': '1967 Ellesmere Rd',
            'lat': 43.77459330890341,
            'lng': -79.23649962433035,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.77459330890341,
              'lng': -79.23649962433035}],
            'distance': 4922,
            'postalCode': 'M1H 2W5',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['1967 Ellesmere Rd',
             'Scarborough ON M1H 2W5',
             'Canada']},
           'categories': [{'id': '4f4528bc4b90abdf24c9de85',
             'name': 'Athletics & Sports',
             'pluralName': 'Athletics & Sports',
             'shortName': 'Athletics & Sports',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/sports_outdoors_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4b931d41f964a520d43534e3-98'},
         {'reasons': {'count': 0,
           'items': [{'summary': 'This spot is popular',
             'type': 'general',
             'reasonName': 'globalInteractionReason'}]},
          'venue': {'id': '4cc33d971e596dcbe61ac967',
           'name': 'TD Canada Trust',
           'location': {'address': '4515 Kingston Rd',
            'crossStreet': 'at Morningside Ave.',
            'lat': 43.770997118312,
            'lng': -79.18599759390418,
            'labeledLatLngs': [{'label': 'display',
              'lat': 43.770997118312,
              'lng': -79.18599759390418}],
            'distance': 4029,
            'postalCode': 'M1E 2P1',
            'cc': 'CA',
            'city': 'Scarborough',
            'state': 'ON',
            'country': 'Canada',
            'formattedAddress': ['4515 Kingston Rd (at Morningside Ave.)',
             'Scarborough ON M1E 2P1',
             'Canada']},
           'categories': [{'id': '4bf58dd8d48988d10a951735',
             'name': 'Bank',
             'pluralName': 'Banks',
             'shortName': 'Bank',
             'icon': {'prefix': 'https://ss3.4sqi.net/img/categories_v2/shops/financial_',
              'suffix': '.png'},
             'primary': True}],
           'photos': {'count': 0, 'groups': []}},
          'referralId': 'e-0-4cc33d971e596dcbe61ac967-99'}]}]}}




```python
# function that extracts the category of the venue
def get_category_type(row):
    try:
        categories_list = row['categories']
    except:
        categories_list = row['venue.categories']
        
    if len(categories_list) == 0:
        return None
    else:
        return categories_list[0]['name']
```


```python
from pandas.io.json import json_normalize
venues = results['response']['groups'][0]['items']
    
nearby_venues = json_normalize(venues) # flatten JSON

# filter columns
filtered_columns = ['venue.name', 'venue.categories', 'venue.location.lat', 'venue.location.lng']
nearby_venues =nearby_venues.loc[:, filtered_columns]

# filter the category for each row
nearby_venues['venue.categories'] = nearby_venues.apply(get_category_type, axis=1)

# clean columns
nearby_venues.columns = [col.split(".")[-1] for col in nearby_venues.columns]

nearby_venues.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>name</th>
      <th>categories</th>
      <th>lat</th>
      <th>lng</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>African Rainforest Pavilion</td>
      <td>Zoo Exhibit</td>
      <td>43.817725</td>
      <td>-79.183433</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Toronto Pan Am Sports Centre</td>
      <td>Athletics &amp; Sports</td>
      <td>43.790623</td>
      <td>-79.193869</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Toronto Zoo</td>
      <td>Zoo</td>
      <td>43.820582</td>
      <td>-79.181551</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Polar Bear Exhibit</td>
      <td>Zoo</td>
      <td>43.823372</td>
      <td>-79.185145</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Australasia Pavillion</td>
      <td>Zoo Exhibit</td>
      <td>43.822563</td>
      <td>-79.183286</td>
    </tr>
  </tbody>
</table>
</div>




```python
print('{} venues were returned by Foursquare.'.format(nearby_venues.shape[0]))
```

    100 venues were returned by Foursquare.
    

## Clustering analysis of Scarborough



```python
#function to repeat the same process to all the neighborhoods
def getNearbyVenues(names, latitudes, longitudes, radius=500):
    
    venues_list=[]
    for name, lat, lng in zip(names, latitudes, longitudes):
        print(name)
            
        # create the API request URL
        url = 'https://api.foursquare.com/v2/venues/explore?&client_id={}&client_secret={}&v={}&ll={},{}&radius={}&limit={}'.format(
            CLIENT_ID, 
            CLIENT_SECRET, 
            VERSION, 
            lat, 
            lng, 
            radius, 
            LIMIT)
            
        # make the GET request
        results = requests.get(url).json()["response"]['groups'][0]['items']
        
        # return only relevant information for each nearby venue
        venues_list.append([(
            name, 
            lat, 
            lng, 
            v['venue']['name'], 
            v['venue']['location']['lat'], 
            v['venue']['location']['lng'],  
            v['venue']['categories'][0]['name']) for v in results])

    nearby_venues = pd.DataFrame([item for venue_list in venues_list for item in venue_list])
    nearby_venues.columns = ['Neighborhood', 
                  'Neighborhood Latitude', 
                  'Neighborhood Longitude', 
                  'Venue', 
                  'Venue Latitude', 
                  'Venue Longitude', 
                  'Venue Category']
    
    return(nearby_venues)
```


```python
sc_venues = getNearbyVenues(names=df_sc['Neighbourhood'],
                                   latitudes=df_sc['Latitude'],
                                   longitudes=df_sc['Longitude']
                                  )
```

    Rouge,Malvern
    Highland Creek,Rouge Hill,Port Union
    Guildwood,Morningside,West Hill
    Woburn
    Cedarbrae
    Scarborough Village
    East Birchmount Park,Ionview,Kennedy Park
    Clairlea,Golden Mile,Oakridge
    Cliffcrest,Cliffside,Scarborough Village West
    Birch Cliff,Cliffside West
    Dorset Park,Scarborough Town Centre,Wexford Heights
    Maryvale,Wexford
    Agincourt
    Clarks Corners,Sullivan,Tam O'Shanter
    Agincourt North,L'Amoreaux East,Milliken,Steeles East
    L'Amoreaux West
    Upper Rouge
    


```python
print(sc_venues.shape)
sc_venues.head()
```

    (96, 7)
    




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>Neighborhood Latitude</th>
      <th>Neighborhood Longitude</th>
      <th>Venue</th>
      <th>Venue Latitude</th>
      <th>Venue Longitude</th>
      <th>Venue Category</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Rouge,Malvern</td>
      <td>43.806686</td>
      <td>-79.194353</td>
      <td>Wendy's</td>
      <td>43.807448</td>
      <td>-79.199056</td>
      <td>Fast Food Restaurant</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Rouge,Malvern</td>
      <td>43.806686</td>
      <td>-79.194353</td>
      <td>Interprovincial Group</td>
      <td>43.805630</td>
      <td>-79.200378</td>
      <td>Print Shop</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>43.784535</td>
      <td>-79.160497</td>
      <td>Chris Effects Painting</td>
      <td>43.784343</td>
      <td>-79.163742</td>
      <td>Construction &amp; Landscaping</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>43.784535</td>
      <td>-79.160497</td>
      <td>Royal Canadian Legion</td>
      <td>43.782533</td>
      <td>-79.163085</td>
      <td>Bar</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>43.784535</td>
      <td>-79.160497</td>
      <td>Affordable Toronto Movers</td>
      <td>43.787919</td>
      <td>-79.162977</td>
      <td>Moving Target</td>
    </tr>
  </tbody>
</table>
</div>




```python
sc_venues.groupby('Neighborhood').count()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood Latitude</th>
      <th>Neighborhood Longitude</th>
      <th>Venue</th>
      <th>Venue Latitude</th>
      <th>Venue Longitude</th>
      <th>Venue Category</th>
    </tr>
    <tr>
      <th>Neighborhood</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Agincourt</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <td>Agincourt North,L'Amoreaux East,Milliken,Steeles East</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <td>Birch Cliff,Cliffside West</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
    </tr>
    <tr>
      <td>Cedarbrae</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
    </tr>
    <tr>
      <td>Clairlea,Golden Mile,Oakridge</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
      <td>10</td>
    </tr>
    <tr>
      <td>Clarks Corners,Sullivan,Tam O'Shanter</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
      <td>12</td>
    </tr>
    <tr>
      <td>Cliffcrest,Cliffside,Scarborough Village West</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <td>Dorset Park,Scarborough Town Centre,Wexford Heights</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
      <td>7</td>
    </tr>
    <tr>
      <td>East Birchmount Park,Ionview,Kennedy Park</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
      <td>8</td>
    </tr>
    <tr>
      <td>Guildwood,Morningside,West Hill</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
      <td>9</td>
    </tr>
    <tr>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <td>L'Amoreaux West</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
      <td>13</td>
    </tr>
    <tr>
      <td>Maryvale,Wexford</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
      <td>5</td>
    </tr>
    <tr>
      <td>Rouge,Malvern</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
      <td>2</td>
    </tr>
    <tr>
      <td>Scarborough Village</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Woburn</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
      <td>4</td>
    </tr>
  </tbody>
</table>
</div>




```python
print('There are {} uniques categories.'.format(len(manhattan_venues['Venue Category'].unique())))
```

    There are 59 uniques categories.
    

# Analyze Each Neighbourhood


```python
# one hot encoding
sc_onehot = pd.get_dummies(sc_venues[['Venue Category']], prefix="", prefix_sep="")

# add neighborhood column back to dataframe
sc_onehot['Neighborhood'] = sc_venues['Neighborhood'] 

# move neighborhood column to the first column
fixed_columns = [sc_onehot.columns[-1]] + list(sc_onehot.columns[:-1])
sc_onehot = sc_onehot[fixed_columns]

sc_onehot.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>American Restaurant</th>
      <th>Arts &amp; Crafts Store</th>
      <th>Athletics &amp; Sports</th>
      <th>Auto Garage</th>
      <th>Bakery</th>
      <th>Bank</th>
      <th>Bar</th>
      <th>Breakfast Spot</th>
      <th>Bubble Tea Shop</th>
      <th>...</th>
      <th>Print Shop</th>
      <th>Rental Car Location</th>
      <th>Sandwich Place</th>
      <th>Shopping Mall</th>
      <th>Skating Rink</th>
      <th>Soccer Field</th>
      <th>Spa</th>
      <th>Thai Restaurant</th>
      <th>Thrift / Vintage Store</th>
      <th>Vietnamese Restaurant</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Rouge,Malvern</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Rouge,Malvern</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>1</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>...</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>5 rows × 60 columns</p>
</div>




```python
sc_onehot.shape
```




    (96, 60)




```python
sc_grouped = sc_onehot.groupby('Neighborhood').mean().reset_index()
sc_grouped
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>American Restaurant</th>
      <th>Arts &amp; Crafts Store</th>
      <th>Athletics &amp; Sports</th>
      <th>Auto Garage</th>
      <th>Bakery</th>
      <th>Bank</th>
      <th>Bar</th>
      <th>Breakfast Spot</th>
      <th>Bubble Tea Shop</th>
      <th>...</th>
      <th>Print Shop</th>
      <th>Rental Car Location</th>
      <th>Sandwich Place</th>
      <th>Shopping Mall</th>
      <th>Skating Rink</th>
      <th>Soccer Field</th>
      <th>Spa</th>
      <th>Thai Restaurant</th>
      <th>Thrift / Vintage Store</th>
      <th>Vietnamese Restaurant</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Agincourt</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.200000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.20</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Agincourt North,L'Amoreaux East,Milliken,Steel...</td>
      <td>0.0</td>
      <td>0.333333</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Birch Cliff,Cliffside West</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.25</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Cedarbrae</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.125</td>
      <td>0.0</td>
      <td>0.125</td>
      <td>0.125000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.125000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Clairlea,Golden Mile,Oakridge</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.200</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.1</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>5</td>
      <td>Clarks Corners,Sullivan,Tam O'Shanter</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.083333</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.083333</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.083333</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>6</td>
      <td>Cliffcrest,Cliffside,Scarborough Village West</td>
      <td>0.5</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>7</td>
      <td>Dorset Park,Scarborough Town Centre,Wexford He...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.142857</td>
      <td>0.142857</td>
    </tr>
    <tr>
      <td>8</td>
      <td>East Birchmount Park,Ionview,Kennedy Park</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>9</td>
      <td>Guildwood,Morningside,West Hill</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.111111</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.111111</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.111111</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>10</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.333333</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>11</td>
      <td>L'Amoreaux West</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.076923</td>
      <td>0.076923</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.076923</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.076923</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>12</td>
      <td>Maryvale,Wexford</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.2</td>
      <td>0.200</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.200000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.200000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>13</td>
      <td>Rouge,Malvern</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.5</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>14</td>
      <td>Scarborough Village</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
    <tr>
      <td>15</td>
      <td>Woburn</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000</td>
      <td>0.0</td>
      <td>0.000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>...</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.00</td>
      <td>0.0</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
      <td>0.000000</td>
    </tr>
  </tbody>
</table>
<p>16 rows × 60 columns</p>
</div>



### Let's print each neighborhood along with the top 5 most common venues


```python
num_top_venues = 5

for hood in sc_grouped['Neighborhood']:
    print("----"+hood+"----")
    temp = sc_grouped[sc_grouped['Neighborhood'] == hood].T.reset_index()
    temp.columns = ['venue','freq']
    temp = temp.iloc[1:]
    temp['freq'] = temp['freq'].astype(float)
    temp = temp.round({'freq': 2})
    print(temp.sort_values('freq', ascending=False).reset_index(drop=True).head(num_top_venues))
    print('\n')
```

    ----Agincourt----
                           venue  freq
    0  Latin American Restaurant   0.2
    1                     Lounge   0.2
    2               Skating Rink   0.2
    3             Breakfast Spot   0.2
    4             Clothing Store   0.2
    
    
    ----Agincourt North,L'Amoreaux East,Milliken,Steeles East----
                     venue  freq
    0                 Park  0.33
    1           Playground  0.33
    2  Arts & Crafts Store  0.33
    3      Thai Restaurant  0.00
    4        Moving Target  0.00
    
    
    ----Birch Cliff,Cliffside West----
                       venue  freq
    0        College Stadium  0.25
    1  General Entertainment  0.25
    2           Skating Rink  0.25
    3                   Café  0.25
    4     Mexican Restaurant  0.00
    
    
    ----Cedarbrae----
                    venue  freq
    0    Hakka Restaurant  0.12
    1         Gas Station  0.12
    2  Athletics & Sports  0.12
    3              Bakery  0.12
    4                Bank  0.12
    
    
    ----Clairlea,Golden Mile,Oakridge----
                      venue  freq
    0              Bus Line   0.2
    1                Bakery   0.2
    2          Intersection   0.1
    3          Soccer Field   0.1
    4  Fast Food Restaurant   0.1
    
    
    ----Clarks Corners,Sullivan,Tam O'Shanter----
                      venue  freq
    0           Pizza Place  0.17
    1    Italian Restaurant  0.08
    2         Shopping Mall  0.08
    3     Convenience Store  0.08
    4  Fast Food Restaurant  0.08
    
    
    ----Cliffcrest,Cliffside,Scarborough Village West----
                     venue  freq
    0  American Restaurant   0.5
    1                Motel   0.5
    2                 Park   0.0
    3         Intersection   0.0
    4   Italian Restaurant   0.0
    
    
    ----Dorset Park,Scarborough Town Centre,Wexford Heights----
                        venue  freq
    0       Indian Restaurant  0.29
    1   Vietnamese Restaurant  0.14
    2      Chinese Restaurant  0.14
    3  Furniture / Home Store  0.14
    4               Pet Store  0.14
    
    
    ----East Birchmount Park,Ionview,Kennedy Park----
                  venue  freq
    0    Discount Store  0.25
    1  Department Store  0.12
    2       Bus Station  0.12
    3        Hobby Shop  0.12
    4       Coffee Shop  0.12
    
    
    ----Guildwood,Morningside,West Hill----
                    venue  freq
    0   Electronics Store  0.22
    1        Intersection  0.11
    2      Breakfast Spot  0.11
    3         Pizza Place  0.11
    4  Mexican Restaurant  0.11
    
    
    ----Highland Creek,Rouge Hill,Port Union----
                            venue  freq
    0                         Bar  0.33
    1               Moving Target  0.33
    2  Construction & Landscaping  0.33
    3         American Restaurant  0.00
    4                        Park  0.00
    
    
    ----L'Amoreaux West----
                      venue  freq
    0  Fast Food Restaurant  0.15
    1    Chinese Restaurant  0.15
    2           Pizza Place  0.08
    3       Bubble Tea Shop  0.08
    4              Pharmacy  0.08
    
    
    ----Maryvale,Wexford----
                           venue  freq
    0                Auto Garage   0.2
    1                     Bakery   0.2
    2  Middle Eastern Restaurant   0.2
    3             Breakfast Spot   0.2
    4             Sandwich Place   0.2
    
    
    ----Rouge,Malvern----
                      venue  freq
    0  Fast Food Restaurant   0.5
    1            Print Shop   0.5
    2   American Restaurant   0.0
    3          Noodle House   0.0
    4          Intersection   0.0
    
    
    ----Scarborough Village----
                     venue  freq
    0           Playground   1.0
    1  American Restaurant   0.0
    2                 Park   0.0
    3         Intersection   0.0
    4   Italian Restaurant   0.0
    
    
    ----Woburn----
                   venue  freq
    0        Coffee Shop  0.50
    1  Korean Restaurant  0.25
    2           Pharmacy  0.25
    3               Park  0.00
    4       Intersection  0.00
    
    
    

### making dataframe


```python
def return_most_common_venues(row, num_top_venues):
    row_categories = row.iloc[1:]
    row_categories_sorted = row_categories.sort_values(ascending=False)
    
    return row_categories_sorted.index.values[0:num_top_venues]
```


```python
#Now let's create the new dataframe and display the top 10 venues for each neighborhood.
```


```python
num_top_venues = 10

indicators = ['st', 'nd', 'rd']

# create columns according to number of top venues
columns = ['Neighborhood']
for ind in np.arange(num_top_venues):
    try:
        columns.append('{}{} Most Common Venue'.format(ind+1, indicators[ind]))
    except:
        columns.append('{}th Most Common Venue'.format(ind+1))

# create a new dataframe
neighborhoods_venues_sorted = pd.DataFrame(columns=columns)
neighborhoods_venues_sorted['Neighborhood'] = sc_grouped['Neighborhood']

for ind in np.arange(sc_grouped.shape[0]):
    neighborhoods_venues_sorted.iloc[ind, 1:] = return_most_common_venues(sc_grouped.iloc[ind, :], num_top_venues)

neighborhoods_venues_sorted.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Neighborhood</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Agincourt</td>
      <td>Clothing Store</td>
      <td>Breakfast Spot</td>
      <td>Skating Rink</td>
      <td>Lounge</td>
      <td>Latin American Restaurant</td>
      <td>College Stadium</td>
      <td>Construction &amp; Landscaping</td>
      <td>Convenience Store</td>
      <td>Department Store</td>
      <td>Vietnamese Restaurant</td>
    </tr>
    <tr>
      <td>1</td>
      <td>Agincourt North,L'Amoreaux East,Milliken,Steel...</td>
      <td>Arts &amp; Crafts Store</td>
      <td>Playground</td>
      <td>Park</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Birch Cliff,Cliffside West</td>
      <td>General Entertainment</td>
      <td>Skating Rink</td>
      <td>Café</td>
      <td>College Stadium</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
    </tr>
    <tr>
      <td>3</td>
      <td>Cedarbrae</td>
      <td>Hakka Restaurant</td>
      <td>Thai Restaurant</td>
      <td>Athletics &amp; Sports</td>
      <td>Gas Station</td>
      <td>Bakery</td>
      <td>Bank</td>
      <td>Caribbean Restaurant</td>
      <td>Fried Chicken Joint</td>
      <td>Discount Store</td>
      <td>Convenience Store</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Clairlea,Golden Mile,Oakridge</td>
      <td>Bus Line</td>
      <td>Bakery</td>
      <td>Metro Station</td>
      <td>Soccer Field</td>
      <td>Fast Food Restaurant</td>
      <td>Intersection</td>
      <td>Park</td>
      <td>Bus Station</td>
      <td>Vietnamese Restaurant</td>
      <td>Construction &amp; Landscaping</td>
    </tr>
  </tbody>
</table>
</div>



## Cluster Neighborhoods


```python
from sklearn.cluster import KMeans
# set number of clusters
kclusters = 5

sc_grouped_clustering = sc_grouped.drop('Neighborhood', 1)

# run k-means clustering
kmeans = KMeans(n_clusters=kclusters, random_state=0).fit(sc_grouped_clustering)

# check cluster labels generated for each row in the dataframe
kmeans.labels_[0:10]
```




    array([0, 0, 0, 0, 0, 0, 3, 0, 0, 0])



new dataframe that includes the cluster as well as the top 10 venues for each neighborhood.


```python
# add clustering labels
neighborhoods_venues_sorted.insert(0, 'Cluste Labels', kmeans.labels_)

sc_merged = df_sc

# merge toronto_grouped with toronto_data to add latitude/longitude for each neighborhood
sc_merged = sc_merged.join(neighborhoods_venues_sorted.set_index('Neighborhood'), on='Neighbourhood')

sc_merged.head() # check the last columns!
#neighborhoods_venues_sorted
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
      <th>Latitude</th>
      <th>Longitude</th>
      <th>Cluste Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>M1B</td>
      <td>Scarborough</td>
      <td>Rouge,Malvern</td>
      <td>43.806686</td>
      <td>-79.194353</td>
      <td>2.0</td>
      <td>Fast Food Restaurant</td>
      <td>Print Shop</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>General Entertainment</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Electronics Store</td>
      <td>Discount Store</td>
    </tr>
    <tr>
      <td>1</td>
      <td>M1C</td>
      <td>Scarborough</td>
      <td>Highland Creek,Rouge Hill,Port Union</td>
      <td>43.784535</td>
      <td>-79.160497</td>
      <td>0.0</td>
      <td>Moving Target</td>
      <td>Bar</td>
      <td>Construction &amp; Landscaping</td>
      <td>Vietnamese Restaurant</td>
      <td>General Entertainment</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
    </tr>
    <tr>
      <td>2</td>
      <td>M1E</td>
      <td>Scarborough</td>
      <td>Guildwood,Morningside,West Hill</td>
      <td>43.763573</td>
      <td>-79.188711</td>
      <td>0.0</td>
      <td>Electronics Store</td>
      <td>Mexican Restaurant</td>
      <td>Spa</td>
      <td>Medical Center</td>
      <td>Intersection</td>
      <td>Rental Car Location</td>
      <td>Breakfast Spot</td>
      <td>Pizza Place</td>
      <td>Convenience Store</td>
      <td>Coffee Shop</td>
    </tr>
    <tr>
      <td>3</td>
      <td>M1G</td>
      <td>Scarborough</td>
      <td>Woburn</td>
      <td>43.770992</td>
      <td>-79.216917</td>
      <td>4.0</td>
      <td>Coffee Shop</td>
      <td>Korean Restaurant</td>
      <td>Pharmacy</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
    </tr>
    <tr>
      <td>4</td>
      <td>M1H</td>
      <td>Scarborough</td>
      <td>Cedarbrae</td>
      <td>43.773136</td>
      <td>-79.239476</td>
      <td>0.0</td>
      <td>Hakka Restaurant</td>
      <td>Thai Restaurant</td>
      <td>Athletics &amp; Sports</td>
      <td>Gas Station</td>
      <td>Bakery</td>
      <td>Bank</td>
      <td>Caribbean Restaurant</td>
      <td>Fried Chicken Joint</td>
      <td>Discount Store</td>
      <td>Convenience Store</td>
    </tr>
  </tbody>
</table>
</div>




```python
sc_merged[sc_merged['Neighbourhood'] == 'Agincourt']
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Postcode</th>
      <th>Borough</th>
      <th>Neighbourhood</th>
      <th>Latitude</th>
      <th>Longitude</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>12</td>
      <td>M1S</td>
      <td>Scarborough</td>
      <td>Agincourt</td>
      <td>43.7942</td>
      <td>-79.262029</td>
    </tr>
  </tbody>
</table>
</div>



## visualizing the resulting clusters


```python
import matplotlib.cm as cm
import matplotlib.colors as colors
# create map
map_clusters = folium.Map(location=[latitude, longitude], zoom_start=11)

# set color scheme for the clusters
x = np.arange(kclusters)
ys = [i + x + (i*x)**2 for i in range(kclusters)]
colors_array = cm.rainbow(np.linspace(0, 1, len(ys)))
rainbow = [colors.rgb2hex(i) for i in colors_array]

# add markers to the map
markers_colors = []
for lat, lon, poi, cluster in zip(sc_merged['Latitude'], sc_merged['Longitude'], sc_merged['Neighbourhood'], sc_merged['Cluste Labels']):
    label = folium.Popup(str(poi) + ' Cluster ' + str(cluster), parse_html=True)
    folium.CircleMarker(
        [lat, lon],
        radius=5,
        popup=label,
        #color=rainbow[cluster-1],
        fill=True,
        #fill_color=rainbow[cluster-1],
        fill_opacity=0.7).add_to(map_clusters)
       
map_clusters
```




<div style="width:100%;"><div style="position:relative;width:100%;height:0;padding-bottom:60%;"><iframe src="data:text/html;charset=utf-8;base64,PCFET0NUWVBFIGh0bWw+CjxoZWFkPiAgICAKICAgIDxtZXRhIGh0dHAtZXF1aXY9ImNvbnRlbnQtdHlwZSIgY29udGVudD0idGV4dC9odG1sOyBjaGFyc2V0PVVURi04IiAvPgogICAgPHNjcmlwdD5MX1BSRUZFUl9DQU5WQVMgPSBmYWxzZTsgTF9OT19UT1VDSCA9IGZhbHNlOyBMX0RJU0FCTEVfM0QgPSBmYWxzZTs8L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmpzIj48L3NjcmlwdD4KICAgIDxzY3JpcHQgc3JjPSJodHRwczovL2FqYXguZ29vZ2xlYXBpcy5jb20vYWpheC9saWJzL2pxdWVyeS8xLjExLjEvanF1ZXJ5Lm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvanMvYm9vdHN0cmFwLm1pbi5qcyI+PC9zY3JpcHQ+CiAgICA8c2NyaXB0IHNyYz0iaHR0cHM6Ly9jZG5qcy5jbG91ZGZsYXJlLmNvbS9hamF4L2xpYnMvTGVhZmxldC5hd2Vzb21lLW1hcmtlcnMvMi4wLjIvbGVhZmxldC5hd2Vzb21lLW1hcmtlcnMuanMiPjwvc2NyaXB0PgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2Nkbi5qc2RlbGl2ci5uZXQvbnBtL2xlYWZsZXRAMS4yLjAvZGlzdC9sZWFmbGV0LmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL21heGNkbi5ib290c3RyYXBjZG4uY29tL2Jvb3RzdHJhcC8zLjIuMC9jc3MvYm9vdHN0cmFwLm1pbi5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9tYXhjZG4uYm9vdHN0cmFwY2RuLmNvbS9ib290c3RyYXAvMy4yLjAvY3NzL2Jvb3RzdHJhcC10aGVtZS5taW4uY3NzIi8+CiAgICA8bGluayByZWw9InN0eWxlc2hlZXQiIGhyZWY9Imh0dHBzOi8vbWF4Y2RuLmJvb3RzdHJhcGNkbi5jb20vZm9udC1hd2Vzb21lLzQuNi4zL2Nzcy9mb250LWF3ZXNvbWUubWluLmNzcyIvPgogICAgPGxpbmsgcmVsPSJzdHlsZXNoZWV0IiBocmVmPSJodHRwczovL2NkbmpzLmNsb3VkZmxhcmUuY29tL2FqYXgvbGlicy9MZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy8yLjAuMi9sZWFmbGV0LmF3ZXNvbWUtbWFya2Vycy5jc3MiLz4KICAgIDxsaW5rIHJlbD0ic3R5bGVzaGVldCIgaHJlZj0iaHR0cHM6Ly9yYXdnaXQuY29tL3B5dGhvbi12aXN1YWxpemF0aW9uL2ZvbGl1bS9tYXN0ZXIvZm9saXVtL3RlbXBsYXRlcy9sZWFmbGV0LmF3ZXNvbWUucm90YXRlLmNzcyIvPgogICAgPHN0eWxlPmh0bWwsIGJvZHkge3dpZHRoOiAxMDAlO2hlaWdodDogMTAwJTttYXJnaW46IDA7cGFkZGluZzogMDt9PC9zdHlsZT4KICAgIDxzdHlsZT4jbWFwIHtwb3NpdGlvbjphYnNvbHV0ZTt0b3A6MDtib3R0b206MDtyaWdodDowO2xlZnQ6MDt9PC9zdHlsZT4KICAgIAogICAgICAgICAgICA8c3R5bGU+ICNtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUgewogICAgICAgICAgICAgICAgcG9zaXRpb24gOiByZWxhdGl2ZTsKICAgICAgICAgICAgICAgIHdpZHRoIDogMTAwLjAlOwogICAgICAgICAgICAgICAgaGVpZ2h0OiAxMDAuMCU7CiAgICAgICAgICAgICAgICBsZWZ0OiAwLjAlOwogICAgICAgICAgICAgICAgdG9wOiAwLjAlOwogICAgICAgICAgICAgICAgfQogICAgICAgICAgICA8L3N0eWxlPgogICAgICAgIAo8L2hlYWQ+Cjxib2R5PiAgICAKICAgIAogICAgICAgICAgICA8ZGl2IGNsYXNzPSJmb2xpdW0tbWFwIiBpZD0ibWFwXzgzYjExYzQwYTU1ZDQ5MTc4MjU2OWNhZTRiMTkzY2ZlIiA+PC9kaXY+CiAgICAgICAgCjwvYm9keT4KPHNjcmlwdD4gICAgCiAgICAKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGJvdW5kcyA9IG51bGw7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgdmFyIG1hcF84M2IxMWM0MGE1NWQ0OTE3ODI1NjljYWU0YjE5M2NmZSA9IEwubWFwKAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgJ21hcF84M2IxMWM0MGE1NWQ0OTE3ODI1NjljYWU0YjE5M2NmZScsCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB7Y2VudGVyOiBbNDMuNzc2NCwtNzkuMjMxOF0sCiAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB6b29tOiAxMSwKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIG1heEJvdW5kczogYm91bmRzLAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgbGF5ZXJzOiBbXSwKICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgIHdvcmxkQ29weUp1bXA6IGZhbHNlLAogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgY3JzOiBMLkNSUy5FUFNHMzg1NwogICAgICAgICAgICAgICAgICAgICAgICAgICAgICAgICB9KTsKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHRpbGVfbGF5ZXJfMGZhNjI1OTEzYWIwNDMyNDk0MGYwNGJmNWVmOTRjMWEgPSBMLnRpbGVMYXllcigKICAgICAgICAgICAgICAgICdodHRwczovL3tzfS50aWxlLm9wZW5zdHJlZXRtYXAub3JnL3t6fS97eH0ve3l9LnBuZycsCiAgICAgICAgICAgICAgICB7CiAgImF0dHJpYnV0aW9uIjogbnVsbCwKICAiZGV0ZWN0UmV0aW5hIjogZmFsc2UsCiAgIm1heFpvb20iOiAxOCwKICAibWluWm9vbSI6IDEsCiAgIm5vV3JhcCI6IGZhbHNlLAogICJzdWJkb21haW5zIjogImFiYyIKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzM1NjUzYTMzNDZhMTRjZjFiMGM2ODE1Y2ExNGZjYjJjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuODA2Njg2Mjk5OTk5OTk2LC03OS4xOTQzNTM0MDAwMDAwMV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICIjMzM4OGZmIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMzODhmZiIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF84M2IxMWM0MGE1NWQ0OTE3ODI1NjljYWU0YjE5M2NmZSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9lZjRjOGM0MWE0Mjk0ODhiYTc2YmUzMTVkYjQxNTIxZiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9lMmEzMWExOGY0ZGE0ZmI0YWQzOWM0NjFkN2VlMzk1OSA9ICQoJzxkaXYgaWQ9Imh0bWxfZTJhMzFhMThmNGRhNGZiNGFkMzljNDYxZDdlZTM5NTkiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPlJvdWdlLE1hbHZlcm4gQ2x1c3RlciAyLjA8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2VmNGM4YzQxYTQyOTQ4OGJhNzZiZTMxNWRiNDE1MjFmLnNldENvbnRlbnQoaHRtbF9lMmEzMWExOGY0ZGE0ZmI0YWQzOWM0NjFkN2VlMzk1OSk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl8zNTY1M2EzMzQ2YTE0Y2YxYjBjNjgxNWNhMTRmY2IyYy5iaW5kUG9wdXAocG9wdXBfZWY0YzhjNDFhNDI5NDg4YmE3NmJlMzE1ZGI0MTUyMWYpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfMTFlMjU3NmYyNTBkNDZhOGFkMjFjODI4ZjcyNjgwM2EgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43ODQ1MzUxLC03OS4xNjA0OTcwOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICIjMzM4OGZmIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMzODhmZiIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF84M2IxMWM0MGE1NWQ0OTE3ODI1NjljYWU0YjE5M2NmZSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9hMmJhY2ZiYjUzY2U0NTMwYjI1MDY3ZTUyMDA3YzlkNiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF9mMzY2YzgzODBhOGI0YTNkODcwNDc1N2I0ODk3M2YwZiA9ICQoJzxkaXYgaWQ9Imh0bWxfZjM2NmM4MzgwYThiNGEzZDg3MDQ3NTdiNDg5NzNmMGYiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkhpZ2hsYW5kIENyZWVrLFJvdWdlIEhpbGwsUG9ydCBVbmlvbiBDbHVzdGVyIDAuMDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfYTJiYWNmYmI1M2NlNDUzMGIyNTA2N2U1MjAwN2M5ZDYuc2V0Q29udGVudChodG1sX2YzNjZjODM4MGE4YjRhM2Q4NzA0NzU3YjQ4OTczZjBmKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzExZTI1NzZmMjUwZDQ2YThhZDIxYzgyOGY3MjY4MDNhLmJpbmRQb3B1cChwb3B1cF9hMmJhY2ZiYjUzY2U0NTMwYjI1MDY3ZTUyMDA3YzlkNik7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8zMTBmOGYwYmY2NDI0YTE4Yjc0Yjg1NTRhN2FhOWY4MiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjc2MzU3MjYsLTc5LjE4ODcxMTVdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNTZlNGIxOWRkYzBmNGMxZTg0MmRjZWU5MGYzOTk4ZGEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfZjliODU5ODEzYzAzNDhiNmIzN2Y0MTAyMWNiNWQyZmUgPSAkKCc8ZGl2IGlkPSJodG1sX2Y5Yjg1OTgxM2MwMzQ4YjZiMzdmNDEwMjFjYjVkMmZlIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5HdWlsZHdvb2QsTW9ybmluZ3NpZGUsV2VzdCBIaWxsIENsdXN0ZXIgMC4wPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF81NmU0YjE5ZGRjMGY0YzFlODQyZGNlZTkwZjM5OThkYS5zZXRDb250ZW50KGh0bWxfZjliODU5ODEzYzAzNDhiNmIzN2Y0MTAyMWNiNWQyZmUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMzEwZjhmMGJmNjQyNGExOGI3NGI4NTU0YTdhYTlmODIuYmluZFBvcHVwKHBvcHVwXzU2ZTRiMTlkZGMwZjRjMWU4NDJkY2VlOTBmMzk5OGRhKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzg2ZWQ4Yjc5ODc1NTRiYWFhNDQwNTkzNmRjN2YyYjJjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzcwOTkyMSwtNzkuMjE2OTE3NDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNzc3NGI2NzY0ODY3NDYzNjlmZDc2MmE5YTBiMjAyYmEgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYmJkMzI4MjJmOTBmNDBkZjk1NWY2Y2Y2MjExMDA2MTQgPSAkKCc8ZGl2IGlkPSJodG1sX2JiZDMyODIyZjkwZjQwZGY5NTVmNmNmNjIxMTAwNjE0IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Xb2J1cm4gQ2x1c3RlciA0LjA8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzc3NzRiNjc2NDg2NzQ2MzY5ZmQ3NjJhOWEwYjIwMmJhLnNldENvbnRlbnQoaHRtbF9iYmQzMjgyMmY5MGY0MGRmOTU1ZjZjZjYyMTEwMDYxNCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl84NmVkOGI3OTg3NTU0YmFhYTQ0MDU5MzZkYzdmMmIyYy5iaW5kUG9wdXAocG9wdXBfNzc3NGI2NzY0ODY3NDYzNjlmZDc2MmE5YTBiMjAyYmEpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfMDM2NDYxNGJlYmM2NDM2YzllMThiYjQ1NGYzODU4ZGUgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43NzMxMzYsLTc5LjIzOTQ3NjA5OTk5OTk5XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogIiMzMzg4ZmYiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzM4OGZmIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzgzYjExYzQwYTU1ZDQ5MTc4MjU2OWNhZTRiMTkzY2ZlKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzJkMDcxZTQ2MDQyMzQ4Y2Q5NDNiMTIxZGI2ODZiYzUzID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzUxYzA2NTU3ZDJhOTQ2Mjk5MDhmNjc2ZjA3ODBhYjY1ID0gJCgnPGRpdiBpZD0iaHRtbF81MWMwNjU1N2QyYTk0NjI5OTA4ZjY3NmYwNzgwYWI2NSIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Q2VkYXJicmFlIENsdXN0ZXIgMC4wPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8yZDA3MWU0NjA0MjM0OGNkOTQzYjEyMWRiNjg2YmM1My5zZXRDb250ZW50KGh0bWxfNTFjMDY1NTdkMmE5NDYyOTkwOGY2NzZmMDc4MGFiNjUpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfMDM2NDYxNGJlYmM2NDM2YzllMThiYjQ1NGYzODU4ZGUuYmluZFBvcHVwKHBvcHVwXzJkMDcxZTQ2MDQyMzQ4Y2Q5NDNiMTIxZGI2ODZiYzUzKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2I1ZTkyMzUyZWMwZTRmNmRhZGM0MGE4OTlkYWExYzNiID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzQ0NzM0MiwtNzkuMjM5NDc2MDk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfNDY1NzJkNWZhY2VlNGY2MTg0NDU5YWZkOWI5MWYxZDMgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNjY3MDBlN2FlNGM0NGQ3ZWJmMzUzNzY0YzVmNDlkNjMgPSAkKCc8ZGl2IGlkPSJodG1sXzY2NzAwZTdhZTRjNDRkN2ViZjM1Mzc2NGM1ZjQ5ZDYzIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5TY2FyYm9yb3VnaCBWaWxsYWdlIENsdXN0ZXIgMS4wPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF80NjU3MmQ1ZmFjZWU0ZjYxODQ0NTlhZmQ5YjkxZjFkMy5zZXRDb250ZW50KGh0bWxfNjY3MDBlN2FlNGM0NGQ3ZWJmMzUzNzY0YzVmNDlkNjMpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfYjVlOTIzNTJlYzBlNGY2ZGFkYzQwYTg5OWRhYTFjM2IuYmluZFBvcHVwKHBvcHVwXzQ2NTcyZDVmYWNlZTRmNjE4NDQ1OWFmZDliOTFmMWQzKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2Y5NGNhNTJmNTEwYjQ3OTlhMzQwZTE1N2RhMGFlYzViID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzI3OTI5MiwtNzkuMjYyMDI5NDAwMDAwMDJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfOGRlNTIxZGUwYzJkNDU0YzkwMjljMDMzZjQyMTMwZGUgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfODNiYTViNWFlZGU3NDcxNzlkMzkyMTgyMjNkNzIxZmMgPSAkKCc8ZGl2IGlkPSJodG1sXzgzYmE1YjVhZWRlNzQ3MTc5ZDM5MjE4MjIzZDcyMWZjIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5FYXN0IEJpcmNobW91bnQgUGFyayxJb252aWV3LEtlbm5lZHkgUGFyayBDbHVzdGVyIDAuMDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfOGRlNTIxZGUwYzJkNDU0YzkwMjljMDMzZjQyMTMwZGUuc2V0Q29udGVudChodG1sXzgzYmE1YjVhZWRlNzQ3MTc5ZDM5MjE4MjIzZDcyMWZjKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2Y5NGNhNTJmNTEwYjQ3OTlhMzQwZTE1N2RhMGFlYzViLmJpbmRQb3B1cChwb3B1cF84ZGU1MjFkZTBjMmQ0NTRjOTAyOWMwMzNmNDIxMzBkZSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9jZDcyYmM1ZTdlOTU0OWVhODAyMzE2YTNiNWMwMjdkNyA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjcxMTExMTcwMDAwMDAwNCwtNzkuMjg0NTc3Ml0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICIjMzM4OGZmIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMzODhmZiIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF84M2IxMWM0MGE1NWQ0OTE3ODI1NjljYWU0YjE5M2NmZSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF8yZDg1MDljNTBkNDI0YWQ5YTJkMTk3ODI1Y2FmYjYxNiA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF8xNDEyNDA0NjUyMmI0NDZiYjk3MWYxYWY2NWM4OGIyMiA9ICQoJzxkaXYgaWQ9Imh0bWxfMTQxMjQwNDY1MjJiNDQ2YmI5NzFmMWFmNjVjODhiMjIiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNsYWlybGVhLEdvbGRlbiBNaWxlLE9ha3JpZGdlIENsdXN0ZXIgMC4wPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF8yZDg1MDljNTBkNDI0YWQ5YTJkMTk3ODI1Y2FmYjYxNi5zZXRDb250ZW50KGh0bWxfMTQxMjQwNDY1MjJiNDQ2YmI5NzFmMWFmNjVjODhiMjIpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfY2Q3MmJjNWU3ZTk1NDllYTgwMjMxNmEzYjVjMDI3ZDcuYmluZFBvcHVwKHBvcHVwXzJkODUwOWM1MGQ0MjRhZDlhMmQxOTc4MjVjYWZiNjE2KTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzM4MDMwNTYzNjZjNTQ1NzhiMTkwNTY4ZjRmN2E5ZTgwID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzE2MzE2LC03OS4yMzk0NzYwOTk5OTk5OV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICIjMzM4OGZmIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMzODhmZiIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF84M2IxMWM0MGE1NWQ0OTE3ODI1NjljYWU0YjE5M2NmZSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF80ZTcwOWY3ZjY5YzU0NWI4YjlmMmI2OTA5ZjdmNTM4OSA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF83NGZlOTFmYzdlYTc0ZDc0ODcxZTcwYzE2NTI1OTIzOSA9ICQoJzxkaXYgaWQ9Imh0bWxfNzRmZTkxZmM3ZWE3NGQ3NDg3MWU3MGMxNjUyNTkyMzkiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkNsaWZmY3Jlc3QsQ2xpZmZzaWRlLFNjYXJib3JvdWdoIFZpbGxhZ2UgV2VzdCBDbHVzdGVyIDMuMDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfNGU3MDlmN2Y2OWM1NDViOGI5ZjJiNjkwOWY3ZjUzODkuc2V0Q29udGVudChodG1sXzc0ZmU5MWZjN2VhNzRkNzQ4NzFlNzBjMTY1MjU5MjM5KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzM4MDMwNTYzNjZjNTQ1NzhiMTkwNTY4ZjRmN2E5ZTgwLmJpbmRQb3B1cChwb3B1cF80ZTcwOWY3ZjY5YzU0NWI4YjlmMmI2OTA5ZjdmNTM4OSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl9lNGQ0MTgxNDFhOTE0MmUxYTE3NmZhNzNkYTE4YzFiNiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjY5MjY1NzAwMDAwMDAwNCwtNzkuMjY0ODQ4MV0sCiAgICAgICAgICAgICAgICB7CiAgImJ1YmJsaW5nTW91c2VFdmVudHMiOiB0cnVlLAogICJjb2xvciI6ICIjMzM4OGZmIiwKICAiZGFzaEFycmF5IjogbnVsbCwKICAiZGFzaE9mZnNldCI6IG51bGwsCiAgImZpbGwiOiB0cnVlLAogICJmaWxsQ29sb3IiOiAiIzMzODhmZiIsCiAgImZpbGxPcGFjaXR5IjogMC43LAogICJmaWxsUnVsZSI6ICJldmVub2RkIiwKICAibGluZUNhcCI6ICJyb3VuZCIsCiAgImxpbmVKb2luIjogInJvdW5kIiwKICAib3BhY2l0eSI6IDEuMCwKICAicmFkaXVzIjogNSwKICAic3Ryb2tlIjogdHJ1ZSwKICAid2VpZ2h0IjogMwp9CiAgICAgICAgICAgICAgICApLmFkZFRvKG1hcF84M2IxMWM0MGE1NWQ0OTE3ODI1NjljYWU0YjE5M2NmZSk7CiAgICAgICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBwb3B1cF9hMmE0NzAyZTA0MDE0NjhmOGQxYmZhMTAyM2QwNTE1MyA9IEwucG9wdXAoe21heFdpZHRoOiAnMzAwJ30pOwoKICAgICAgICAgICAgCiAgICAgICAgICAgICAgICB2YXIgaHRtbF84YWUzYWFlOThmMmE0NmVjOTI3MDY3ZmVlZTM4YzkzZSA9ICQoJzxkaXYgaWQ9Imh0bWxfOGFlM2FhZTk4ZjJhNDZlYzkyNzA2N2ZlZWUzOGM5M2UiIHN0eWxlPSJ3aWR0aDogMTAwLjAlOyBoZWlnaHQ6IDEwMC4wJTsiPkJpcmNoIENsaWZmLENsaWZmc2lkZSBXZXN0IENsdXN0ZXIgMC4wPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9hMmE0NzAyZTA0MDE0NjhmOGQxYmZhMTAyM2QwNTE1My5zZXRDb250ZW50KGh0bWxfOGFlM2FhZTk4ZjJhNDZlYzkyNzA2N2ZlZWUzOGM5M2UpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfZTRkNDE4MTQxYTkxNDJlMWExNzZmYTczZGExOGMxYjYuYmluZFBvcHVwKHBvcHVwX2EyYTQ3MDJlMDQwMTQ2OGY4ZDFiZmExMDIzZDA1MTUzKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzY5ZmRiZWNkMWM0ZTRjYmJhMzY5OThjMjRlYTc5NDJjID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzU3NDA5NiwtNzkuMjczMzA0MDAwMDAwMDFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfZjM3YjFmMmI3ODMwNGI1NTg5ZGZhNDdhMTQ5NzVlMDIgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfYjYyZGFhYTNjNmMxNGZjZWJiMmM1OGVhNjNmYzg0YWQgPSAkKCc8ZGl2IGlkPSJodG1sX2I2MmRhYWEzYzZjMTRmY2ViYjJjNThlYTYzZmM4NGFkIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5Eb3JzZXQgUGFyayxTY2FyYm9yb3VnaCBUb3duIENlbnRyZSxXZXhmb3JkIEhlaWdodHMgQ2x1c3RlciAwLjA8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2YzN2IxZjJiNzgzMDRiNTU4OWRmYTQ3YTE0OTc1ZTAyLnNldENvbnRlbnQoaHRtbF9iNjJkYWFhM2M2YzE0ZmNlYmIyYzU4ZWE2M2ZjODRhZCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl82OWZkYmVjZDFjNGU0Y2JiYTM2OTk4YzI0ZWE3OTQyYy5iaW5kUG9wdXAocG9wdXBfZjM3YjFmMmI3ODMwNGI1NTg5ZGZhNDdhMTQ5NzVlMDIpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfY2I0MTU1YzRjMWU0NGExNDgxYzE4MmM2YjVlNmU3OTEgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43NTAwNzE1MDAwMDAwMDQsLTc5LjI5NTg0OTFdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfOTYxZjYyMzJhMDM2NDQ5NTk4N2I3MDJhNDZkYTFhMzMgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfY2ZmNjc1MDk4YjFkNGY4NmJkYmYyMDM0YWE2MzY4ODMgPSAkKCc8ZGl2IGlkPSJodG1sX2NmZjY3NTA5OGIxZDRmODZiZGJmMjAzNGFhNjM2ODgzIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5NYXJ5dmFsZSxXZXhmb3JkIENsdXN0ZXIgMC4wPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF85NjFmNjIzMmEwMzY0NDk1OTg3YjcwMmE0NmRhMWEzMy5zZXRDb250ZW50KGh0bWxfY2ZmNjc1MDk4YjFkNGY4NmJkYmYyMDM0YWE2MzY4ODMpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfY2I0MTU1YzRjMWU0NGExNDgxYzE4MmM2YjVlNmU3OTEuYmluZFBvcHVwKHBvcHVwXzk2MWY2MjMyYTAzNjQ0OTU5ODdiNzAyYTQ2ZGExYTMzKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyXzg5ZWQ2ZDU2MTk0MTQ4MTg5ZTJlOTAyZjRmMzc5ZDViID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzk0MjAwMywtNzkuMjYyMDI5NDAwMDAwMDJdLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfY2I1NjhhMDEzNDQ4NDA4MGJhOTNjMDViOGQ1ZDE0YjIgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfNGMyNDgxZTk0ODA5NDA5OGE0NGM2YTVmNTA5ZDliZDcgPSAkKCc8ZGl2IGlkPSJodG1sXzRjMjQ4MWU5NDgwOTQwOThhNDRjNmE1ZjUwOWQ5YmQ3IiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5BZ2luY291cnQgQ2x1c3RlciAwLjA8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwX2NiNTY4YTAxMzQ0ODQwODBiYTkzYzA1YjhkNWQxNGIyLnNldENvbnRlbnQoaHRtbF80YzI0ODFlOTQ4MDk0MDk4YTQ0YzZhNWY1MDlkOWJkNyk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl84OWVkNmQ1NjE5NDE0ODE4OWUyZTkwMmY0ZjM3OWQ1Yi5iaW5kUG9wdXAocG9wdXBfY2I1NjhhMDEzNDQ4NDA4MGJhOTNjMDViOGQ1ZDE0YjIpOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfODQ0Mzg0MjM1MjM4NGM2MDk3NjNkNDI0MTM2ZDc0NDQgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My43ODE2Mzc1LC03OS4zMDQzMDIxXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogIiMzMzg4ZmYiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzM4OGZmIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzgzYjExYzQwYTU1ZDQ5MTc4MjU2OWNhZTRiMTkzY2ZlKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzZjYzkyOGNkYWNlZDRkZDRhMmQyZTlmMjUzNjM1NTIwID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzNiMDczYWJjN2JhZjRkNjk4OTcyM2M4MjIxM2I0MTZkID0gJCgnPGRpdiBpZD0iaHRtbF8zYjA3M2FiYzdiYWY0ZDY5ODk3MjNjODIyMTNiNDE2ZCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+Q2xhcmtzIENvcm5lcnMsU3VsbGl2YW4sVGFtIE8mIzM5O1NoYW50ZXIgQ2x1c3RlciAwLjA8L2Rpdj4nKVswXTsKICAgICAgICAgICAgICAgIHBvcHVwXzZjYzkyOGNkYWNlZDRkZDRhMmQyZTlmMjUzNjM1NTIwLnNldENvbnRlbnQoaHRtbF8zYjA3M2FiYzdiYWY0ZDY5ODk3MjNjODIyMTNiNDE2ZCk7CiAgICAgICAgICAgIAoKICAgICAgICAgICAgY2lyY2xlX21hcmtlcl84NDQzODQyMzUyMzg0YzYwOTc2M2Q0MjQxMzZkNzQ0NC5iaW5kUG9wdXAocG9wdXBfNmNjOTI4Y2RhY2VkNGRkNGEyZDJlOWYyNTM2MzU1MjApOwoKICAgICAgICAgICAgCiAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIGNpcmNsZV9tYXJrZXJfNWNiZGY1N2I0NGY3NGZlNjgyOTg5ZWI0ZjdlNzA1NDkgPSBMLmNpcmNsZU1hcmtlcigKICAgICAgICAgICAgICAgIFs0My44MTUyNTIyLC03OS4yODQ1NzcyXSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogIiMzMzg4ZmYiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzM4OGZmIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzgzYjExYzQwYTU1ZDQ5MTc4MjU2OWNhZTRiMTkzY2ZlKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwX2E1MmQ1YWQyMzUyZDQ3MzNhYWI1NGMyOTNjYWZhNjlmID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sX2FmMDdiOTVlNDhjZDQyMzNiZTk0OGFlOTdlMjZhZDViID0gJCgnPGRpdiBpZD0iaHRtbF9hZjA3Yjk1ZTQ4Y2Q0MjMzYmU5NDhhZTk3ZTI2YWQ1YiIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+QWdpbmNvdXJ0IE5vcnRoLEwmIzM5O0Ftb3JlYXV4IEVhc3QsTWlsbGlrZW4sU3RlZWxlcyBFYXN0IENsdXN0ZXIgMC4wPC9kaXY+JylbMF07CiAgICAgICAgICAgICAgICBwb3B1cF9hNTJkNWFkMjM1MmQ0NzMzYWFiNTRjMjkzY2FmYTY5Zi5zZXRDb250ZW50KGh0bWxfYWYwN2I5NWU0OGNkNDIzM2JlOTQ4YWU5N2UyNmFkNWIpOwogICAgICAgICAgICAKCiAgICAgICAgICAgIGNpcmNsZV9tYXJrZXJfNWNiZGY1N2I0NGY3NGZlNjgyOTg5ZWI0ZjdlNzA1NDkuYmluZFBvcHVwKHBvcHVwX2E1MmQ1YWQyMzUyZDQ3MzNhYWI1NGMyOTNjYWZhNjlmKTsKCiAgICAgICAgICAgIAogICAgICAgIAogICAgCiAgICAgICAgICAgIHZhciBjaXJjbGVfbWFya2VyX2I1Zjk1YTYzMTJjZDQ3MWU4YzcwOWFhNGJhMzMyODZmID0gTC5jaXJjbGVNYXJrZXIoCiAgICAgICAgICAgICAgICBbNDMuNzk5NTI1MjAwMDAwMDA1LC03OS4zMTgzODg3XSwKICAgICAgICAgICAgICAgIHsKICAiYnViYmxpbmdNb3VzZUV2ZW50cyI6IHRydWUsCiAgImNvbG9yIjogIiMzMzg4ZmYiLAogICJkYXNoQXJyYXkiOiBudWxsLAogICJkYXNoT2Zmc2V0IjogbnVsbCwKICAiZmlsbCI6IHRydWUsCiAgImZpbGxDb2xvciI6ICIjMzM4OGZmIiwKICAiZmlsbE9wYWNpdHkiOiAwLjcsCiAgImZpbGxSdWxlIjogImV2ZW5vZGQiLAogICJsaW5lQ2FwIjogInJvdW5kIiwKICAibGluZUpvaW4iOiAicm91bmQiLAogICJvcGFjaXR5IjogMS4wLAogICJyYWRpdXMiOiA1LAogICJzdHJva2UiOiB0cnVlLAogICJ3ZWlnaHQiOiAzCn0KICAgICAgICAgICAgICAgICkuYWRkVG8obWFwXzgzYjExYzQwYTU1ZDQ5MTc4MjU2OWNhZTRiMTkzY2ZlKTsKICAgICAgICAgICAgCiAgICAKICAgICAgICAgICAgdmFyIHBvcHVwXzk4YWVlMDQzMmZjOTQ2YTU5OGI1YzA2ZWZiMjA2ODg5ID0gTC5wb3B1cCh7bWF4V2lkdGg6ICczMDAnfSk7CgogICAgICAgICAgICAKICAgICAgICAgICAgICAgIHZhciBodG1sXzhlOGRiMzVjMTE2OTRiNGViYzk0ODg0ZmVhZWM3NjY0ID0gJCgnPGRpdiBpZD0iaHRtbF84ZThkYjM1YzExNjk0YjRlYmM5NDg4NGZlYWVjNzY2NCIgc3R5bGU9IndpZHRoOiAxMDAuMCU7IGhlaWdodDogMTAwLjAlOyI+TCYjMzk7QW1vcmVhdXggV2VzdCBDbHVzdGVyIDAuMDwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfOThhZWUwNDMyZmM5NDZhNTk4YjVjMDZlZmIyMDY4ODkuc2V0Q29udGVudChodG1sXzhlOGRiMzVjMTE2OTRiNGViYzk0ODg0ZmVhZWM3NjY0KTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyX2I1Zjk1YTYzMTJjZDQ3MWU4YzcwOWFhNGJhMzMyODZmLmJpbmRQb3B1cChwb3B1cF85OGFlZTA0MzJmYzk0NmE1OThiNWMwNmVmYjIwNjg4OSk7CgogICAgICAgICAgICAKICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgY2lyY2xlX21hcmtlcl8yNjM4ZWIxMWYxOGY0ZjAyYTEzMWZiYTUyMGZkNGZjMiA9IEwuY2lyY2xlTWFya2VyKAogICAgICAgICAgICAgICAgWzQzLjgzNjEyNDcwMDAwMDAwNiwtNzkuMjA1NjM2MDk5OTk5OTldLAogICAgICAgICAgICAgICAgewogICJidWJibGluZ01vdXNlRXZlbnRzIjogdHJ1ZSwKICAiY29sb3IiOiAiIzMzODhmZiIsCiAgImRhc2hBcnJheSI6IG51bGwsCiAgImRhc2hPZmZzZXQiOiBudWxsLAogICJmaWxsIjogdHJ1ZSwKICAiZmlsbENvbG9yIjogIiMzMzg4ZmYiLAogICJmaWxsT3BhY2l0eSI6IDAuNywKICAiZmlsbFJ1bGUiOiAiZXZlbm9kZCIsCiAgImxpbmVDYXAiOiAicm91bmQiLAogICJsaW5lSm9pbiI6ICJyb3VuZCIsCiAgIm9wYWNpdHkiOiAxLjAsCiAgInJhZGl1cyI6IDUsCiAgInN0cm9rZSI6IHRydWUsCiAgIndlaWdodCI6IDMKfQogICAgICAgICAgICAgICAgKS5hZGRUbyhtYXBfODNiMTFjNDBhNTVkNDkxNzgyNTY5Y2FlNGIxOTNjZmUpOwogICAgICAgICAgICAKICAgIAogICAgICAgICAgICB2YXIgcG9wdXBfMTNlY2M3MDVjNTExNDJlZDgyYThlM2VkOTEwMTU4ZjAgPSBMLnBvcHVwKHttYXhXaWR0aDogJzMwMCd9KTsKCiAgICAgICAgICAgIAogICAgICAgICAgICAgICAgdmFyIGh0bWxfMmI2ZjY1MDJjZTVjNDBhMThkZmQxNDZkYTY5YjVhOWMgPSAkKCc8ZGl2IGlkPSJodG1sXzJiNmY2NTAyY2U1YzQwYTE4ZGZkMTQ2ZGE2OWI1YTljIiBzdHlsZT0id2lkdGg6IDEwMC4wJTsgaGVpZ2h0OiAxMDAuMCU7Ij5VcHBlciBSb3VnZSBDbHVzdGVyIG5hbjwvZGl2PicpWzBdOwogICAgICAgICAgICAgICAgcG9wdXBfMTNlY2M3MDVjNTExNDJlZDgyYThlM2VkOTEwMTU4ZjAuc2V0Q29udGVudChodG1sXzJiNmY2NTAyY2U1YzQwYTE4ZGZkMTQ2ZGE2OWI1YTljKTsKICAgICAgICAgICAgCgogICAgICAgICAgICBjaXJjbGVfbWFya2VyXzI2MzhlYjExZjE4ZjRmMDJhMTMxZmJhNTIwZmQ0ZmMyLmJpbmRQb3B1cChwb3B1cF8xM2VjYzcwNWM1MTE0MmVkODJhOGUzZWQ5MTAxNThmMCk7CgogICAgICAgICAgICAKICAgICAgICAKPC9zY3JpcHQ+" style="position:absolute;width:100%;height:100%;left:0;top:0;border:none !important;" allowfullscreen webkitallowfullscreen mozallowfullscreen></iframe></div></div>



## Examine Clusters


```python
sc_merged.loc[sc_merged['Cluste Labels'] == 0, sc_merged.columns[[1] + list(range(5, sc_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluste Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Moving Target</td>
      <td>Bar</td>
      <td>Construction &amp; Landscaping</td>
      <td>Vietnamese Restaurant</td>
      <td>General Entertainment</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Electronics Store</td>
      <td>Mexican Restaurant</td>
      <td>Spa</td>
      <td>Medical Center</td>
      <td>Intersection</td>
      <td>Rental Car Location</td>
      <td>Breakfast Spot</td>
      <td>Pizza Place</td>
      <td>Convenience Store</td>
      <td>Coffee Shop</td>
    </tr>
    <tr>
      <td>4</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Hakka Restaurant</td>
      <td>Thai Restaurant</td>
      <td>Athletics &amp; Sports</td>
      <td>Gas Station</td>
      <td>Bakery</td>
      <td>Bank</td>
      <td>Caribbean Restaurant</td>
      <td>Fried Chicken Joint</td>
      <td>Discount Store</td>
      <td>Convenience Store</td>
    </tr>
    <tr>
      <td>6</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Discount Store</td>
      <td>Coffee Shop</td>
      <td>Hobby Shop</td>
      <td>Department Store</td>
      <td>Bus Station</td>
      <td>Convenience Store</td>
      <td>Chinese Restaurant</td>
      <td>Vietnamese Restaurant</td>
      <td>General Entertainment</td>
      <td>Gas Station</td>
    </tr>
    <tr>
      <td>7</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Bus Line</td>
      <td>Bakery</td>
      <td>Metro Station</td>
      <td>Soccer Field</td>
      <td>Fast Food Restaurant</td>
      <td>Intersection</td>
      <td>Park</td>
      <td>Bus Station</td>
      <td>Vietnamese Restaurant</td>
      <td>Construction &amp; Landscaping</td>
    </tr>
    <tr>
      <td>9</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>General Entertainment</td>
      <td>Skating Rink</td>
      <td>Café</td>
      <td>College Stadium</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
    </tr>
    <tr>
      <td>10</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Indian Restaurant</td>
      <td>Vietnamese Restaurant</td>
      <td>Pet Store</td>
      <td>Thrift / Vintage Store</td>
      <td>Furniture / Home Store</td>
      <td>Chinese Restaurant</td>
      <td>Bank</td>
      <td>Construction &amp; Landscaping</td>
      <td>Arts &amp; Crafts Store</td>
      <td>Gas Station</td>
    </tr>
    <tr>
      <td>11</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Middle Eastern Restaurant</td>
      <td>Auto Garage</td>
      <td>Bakery</td>
      <td>Sandwich Place</td>
      <td>Breakfast Spot</td>
      <td>Discount Store</td>
      <td>College Stadium</td>
      <td>Construction &amp; Landscaping</td>
      <td>Convenience Store</td>
      <td>Department Store</td>
    </tr>
    <tr>
      <td>12</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Clothing Store</td>
      <td>Breakfast Spot</td>
      <td>Skating Rink</td>
      <td>Lounge</td>
      <td>Latin American Restaurant</td>
      <td>College Stadium</td>
      <td>Construction &amp; Landscaping</td>
      <td>Convenience Store</td>
      <td>Department Store</td>
      <td>Vietnamese Restaurant</td>
    </tr>
    <tr>
      <td>13</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Pizza Place</td>
      <td>Noodle House</td>
      <td>Thai Restaurant</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Shopping Mall</td>
      <td>Bank</td>
      <td>Chinese Restaurant</td>
      <td>Italian Restaurant</td>
      <td>Pharmacy</td>
    </tr>
    <tr>
      <td>14</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Arts &amp; Crafts Store</td>
      <td>Playground</td>
      <td>Park</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
    </tr>
    <tr>
      <td>15</td>
      <td>Scarborough</td>
      <td>0.0</td>
      <td>Chinese Restaurant</td>
      <td>Fast Food Restaurant</td>
      <td>Grocery Store</td>
      <td>Coffee Shop</td>
      <td>Pharmacy</td>
      <td>Pizza Place</td>
      <td>Bubble Tea Shop</td>
      <td>Breakfast Spot</td>
      <td>Sandwich Place</td>
      <td>Thrift / Vintage Store</td>
    </tr>
  </tbody>
</table>
</div>




```python
sc_merged.loc[sc_merged['Cluste Labels'] == 1, sc_merged.columns[[1] + list(range(5, sc_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluste Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>5</td>
      <td>Scarborough</td>
      <td>1.0</td>
      <td>Playground</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>General Entertainment</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
      <td>Discount Store</td>
    </tr>
  </tbody>
</table>
</div>




```python
sc_merged.loc[sc_merged['Cluste Labels'] == 2, sc_merged.columns[[1] + list(range(5, sc_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluste Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>0</td>
      <td>Scarborough</td>
      <td>2.0</td>
      <td>Fast Food Restaurant</td>
      <td>Print Shop</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>General Entertainment</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Electronics Store</td>
      <td>Discount Store</td>
    </tr>
  </tbody>
</table>
</div>




```python
sc_merged.loc[sc_merged['Cluste Labels'] == 3, sc_merged.columns[[1] + list(range(5, sc_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluste Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>8</td>
      <td>Scarborough</td>
      <td>3.0</td>
      <td>American Restaurant</td>
      <td>Motel</td>
      <td>Gym</td>
      <td>General Entertainment</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
      <td>Discount Store</td>
    </tr>
  </tbody>
</table>
</div>




```python
sc_merged.loc[sc_merged['Cluste Labels'] == 4, sc_merged.columns[[1] + list(range(5, sc_merged.shape[1]))]]
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Borough</th>
      <th>Cluste Labels</th>
      <th>1st Most Common Venue</th>
      <th>2nd Most Common Venue</th>
      <th>3rd Most Common Venue</th>
      <th>4th Most Common Venue</th>
      <th>5th Most Common Venue</th>
      <th>6th Most Common Venue</th>
      <th>7th Most Common Venue</th>
      <th>8th Most Common Venue</th>
      <th>9th Most Common Venue</th>
      <th>10th Most Common Venue</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>3</td>
      <td>Scarborough</td>
      <td>4.0</td>
      <td>Coffee Shop</td>
      <td>Korean Restaurant</td>
      <td>Pharmacy</td>
      <td>Vietnamese Restaurant</td>
      <td>Clothing Store</td>
      <td>Gas Station</td>
      <td>Furniture / Home Store</td>
      <td>Fried Chicken Joint</td>
      <td>Fast Food Restaurant</td>
      <td>Electronics Store</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
