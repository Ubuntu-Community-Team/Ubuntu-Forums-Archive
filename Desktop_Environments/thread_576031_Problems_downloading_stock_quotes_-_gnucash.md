---
title: "Problems downloading stock quotes - gnucash"
date: 2007-10-14
forum: Desktop Environments
---

### Post by rgeddes on 2007-10-14
I was using GNUCash 2.0.5 on Ubuntu 7.04 for the last several months.  Set up some stock investments and downloaded stock prices with Tools -> Price Editor -> Get Quotes.  This worked ok until about 3 weeks ago.  Now I get a message "There was an unknown error while retrieving the price quotes." 

Tried the following:
-----
$0> gnc-fq-dump -v yahoo AMD
No results found for stock AMD.
----
$0> gnc-fq-check
("1.13" "tsp" "vwd" "financecanada" "yahoo_nz" "australia" "usa" "troweprice" "france" "amfiindia" "nasdaq" "usfedbonds" "bmonesbittburns" "aex_options" "yahoo_asia" "troweprice_direct" "tiaacref" "canada" "yahoo" "seb_funds" "yahoo_brasil" "fidelity" "aiahk" "greece" "dwsfunds" "yahoo_australia" "unionfunds" "finland" "lerevenu" "asia" "indiamutual" "hex" "brasil" "asegr" "deka" "nyse" "canadamutual" "fidelity_direct" "asx" "tdwaterhouse" "fool" "trustnet" "ftportfolios_direct" "uk_unit_trusts" "dutch" "ftportfolios" "tdefunds" "nzx" "za" "aex_futures" "fundlibrary" "stockhousecanada_fund" "aex" "yahoo_europe" "nz" "vanguard" "bourso" "europe" "platinum" "maninv")
 ----

I did install a firewall management program called "Firestarter" between the time gnucash was working and when it stopped working... I've since  uninstalled Firestarter.  I tried getting stock quotes after stopping my firewall using "/etc/init.d/iptables stop".  No difference.

I also upgraded to gnucash 2.2.1.  No dice.

I uninstalled gnucash altogether and reinstalled it, but still getting the same message.

Can someone help me troubleshoot this problem?  Thanks.

Richard

---

### Post by rgeddes on 2007-10-22
I finally resolved my problem... took a little head scratching.

I forgot I modified my hosts file as specified by:

ad blocker [http://everythingisnt.com/hosts.html]("http://everythingisnt.com/hosts.html")

this modifies the hosts file so that all known advertising sources are aliased to 127.0.0.1

Don't really understand why Finance::Quote needs to resolve the ad based web page components, but apparently it affects the operation.

---

