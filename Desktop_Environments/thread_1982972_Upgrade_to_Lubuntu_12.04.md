---
title: "Upgrade to Lubuntu 12.04"
date: 2012-05-19
forum: Desktop Environments
---

### Post by dgharmon on 2012-05-19
Installed Lubuntu 12.04 next to Ubuntu 11.04, no network on 12.04, any solutions?

---

### Post by LeGasp on 2012-05-19
Posting the output of a "sudo iwconfig" command will get you help faster. Also are you using wired or wireless? An iwconfig command will list your network devices and a whole bunch of relevant information that can help you diagnose network issues.

---

### Post by Rodney9 on 2012-05-19
For How-To's and Information on Lubuntu

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

For  Screen-Casts on Lubuntu

[http://blip.tv/rss/bookmarks/206798](http://blip.tv/rss/bookmarks/206798)

Rodney

---

### Post by dgharmon on 2012-05-19
> **LeGasp said:**
> Posting the output of a "sudo iwconfig" command will get you help faster. Also are you using wired or wireless? An iwconfig command will list your network devices and a whole bunch of relevant information that can help you diagnose network issues.

Like I said I have Internet access on version 11.04 but not 12.04, what gives ?
-----------

$iwconfig

lo        no wireless extensions.
eth0      no wireless extensions.
-----------

$ifconfig

lo Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:87 errors:0 dropped:0 overruns:0 frame:0
TX packets:87 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:8279 (8.2 KB)  TX bytes:8279 (8.2 KB)
-------

I reinstalled 12.04 and choose not to select the online update, now the network is working, what gives?

---

