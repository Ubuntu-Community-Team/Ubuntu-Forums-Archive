---
title: "flightgear fonts dont work"
date: 2014-04-21
forum: Gaming &amp; Leisure
---

### Post by peter_mack on 2014-04-21
Apparently this is a known that LiberationSans-Bold.ttf fails to load which causes the menus on the flight display to fail to show up.
There are some pages on this subject found using google, but apparently no solutions yet. the most infomative is debian bug report log #743169 suggests that the 'osgDB_freetype.so' is no longer built. 

I have downloaded to ubuntu 14.04 using the flightgear found in the default repository and using fgrun to start flightgear. it comes up with the start up log showing errors, and proceeds to bring up the flight display without menus.
Adding the salarcot895 ppa doesnt  initiate any updates, and I am not keen on keeping this repository active as it may duplicate ubuntu defaults.

As things stand flight gear is only usable if you know the keyboard codes for the aircraft. This was partly solved by hitting F10 which gets the menu back, however the Liberation font problem still exists.

is there anyone out there that can comment on this or possibly suggest a work around?
pete

---

