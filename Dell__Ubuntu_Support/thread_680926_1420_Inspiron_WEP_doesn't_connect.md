---
title: "1420 Inspiron WEP doesn't connect"
date: 2008-01-28
forum: Dell  Ubuntu Support
---

### Post by factor2 on 2008-01-28
Wireless frustration on Ubuntu 7.04. I can join up to unsecure AP's without any problem, but if I try to enter my WEP key it doesn't work (AP doesn't support WPA). The only way I've been able to do it so far, but even this doesn't always work, is turn off wireless in Network Manager, then add key to eth1 in terminal with "iwconfig eth1 key XXX", then turn wireless back on in Network Manager. 

Default network card with pre-installed Dell is Intel 3945 WLAN 

when it isn't connecting properly, typing iwconfig by itself reveals that the machine is connected to the correct AP, but for some reason a bogus IP address is listed in ifconfig. 

Thoughts? Thanks!

---

### Post by pytheas22 on 2008-01-28
I can't offer any specific ideas, but maybe trying wicd instead of NM would work...NM is notorious for being buggy.  wicd site is [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

