---
title: "No internet but have Wifi  with Dell Latitude"
date: 2011-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shane wiley on 2011-12-11
Dell Latitude D430, dual boot, Windows and Ubuntu 10.04 LTS.

Under Windows sees/connects home router and then Firefox connects to internet with no problems.
Under Ubuntu sees/connects home router and then Firefox sends request to internet site but nothing happens, just grinds on and on.

Any help appreciated.  Any help given in idiot simple steps really appreciated. 

Shane Wiley

---

### Post by mikewhatever on 2011-12-11
Can you post the outputs of the following commands:

```

ifconfig

lspci -k | grep Net -A10

less /etc/resolv.conf
```

---

