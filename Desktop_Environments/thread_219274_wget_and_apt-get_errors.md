---
title: "wget and apt-get errors"
date: 2006-07-19
forum: Desktop Environments
---

### Post by redwolf963 on 2006-07-19
When I try to install via wget or apt-get,I keep getting errors in connecting to localhost(80).Says can't connect to localhost.My firewall shows localhost listening on port 631 lpp.I know this is a CUPS port.So how did it become my port for localhost and how do I fix it?
Any help much appreciatted!
     Thanks, Scott

---

### Post by svaucher on 2006-07-20
Check your (wget) proxy configuration.

The default one is: /etc/wgetrc

I configured mine to ignore proxies (since I don't use them)

use_proxy = off

---

