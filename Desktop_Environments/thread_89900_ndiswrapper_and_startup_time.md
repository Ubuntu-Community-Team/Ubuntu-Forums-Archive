---
title: "ndiswrapper and startup time"
date: 2005-11-13
forum: Desktop Environments
---

### Post by rold50 on 2005-11-13
Hi,

I have ndiswrapper installed for my wireless card. However, when I restart my laptop, it seems to take a loong time to load it.


Is there any way to fix this?

---

### Post by Lambert on 2005-11-13
I found that if I have two different interfaces enabled (eth0-hardwire and ath0-wireless) that it tries to get a dhcp offer on the eth0 line and waits. When I disabled the eth0 interface it solved the load times for me.

---

