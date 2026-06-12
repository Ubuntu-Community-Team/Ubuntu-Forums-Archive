---
title: "Network drivers"
date: 2008-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mark458 on 2008-07-28
I have a dell 1600sc server with 8.04 desktop installed on it. I cant get eh network drivers I have to install... Maybe Im using the wrong one but if so can someone tell me what drivers to use?

---

### Post by Potatoj316 on 2008-07-28
If your using a wired connection you probably dont have to install drivers.  If your problem is your not connected to the internet and wernt connected to the internet when you installed then you will have to configure DHCP manually.  to test this try this command
```
dhclient3
```if that gets you online you will either have to run that command every time you restart or modify your dhcp config.  try googling for how to do that.

---

