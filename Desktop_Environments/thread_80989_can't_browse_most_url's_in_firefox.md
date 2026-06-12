---
title: "can't browse most url's in firefox"
date: 2005-10-23
forum: Desktop Environments
---

### Post by sickOfWindows on 2005-10-23
newb to linux.  installed ubuntu 5.10 yesterday.  1.5 mbps lan/cat5 cable connected.  firefox set as default browser, set to detect proxy settings automatically (direct internet connection didn't work either).  can browse some url's in the default bookmarks in firefox, but not all, and can't even connect to google.  error: timed out (or something similar).  any pointers on what needs changed or where to find documentation already posted on this problem much appreciated.  thx.

---

### Post by poptones on 2005-10-23
this is likely an ipv6 problem. Type about:config in the url bar and hit enter, then input in the "filter" for ipv6. You will see an entry network.dns.disableIPv6; double-click it and the value will change to "true." After that you should restart the browser and things will probably be much better.

---

### Post by sickOfWindows on 2005-10-23
that did the trick.  much thanks!  now to get ubuntu to detect my wireless card - will STFW.

---

