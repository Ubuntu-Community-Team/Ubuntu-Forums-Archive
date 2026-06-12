---
title: "Network Manager panel icon not reappearing on restart (Mate)"
date: 2016-07-11
forum: Desktop Environments
---

### Post by kawedel on 2016-07-11
I accidentally deleted the Network Manager and Sound icons from the panel on Ubuntu Mate and cannot get them back. An earlier forum post said restarting or logging out would work if Network Manager was a startup app, but it makes no difference, at least if nm-applet is what was referred to. I also changed "Managed=false" to "Managed=true" in /etc/NetworkManager/NetworkManager.conf to no effect. What more can be done?

---

### Post by wildmanne39 on 2016-07-12
This should do it:
```
sud apt-get install --reinstall network-manager-gnome
```
Thanks

---

