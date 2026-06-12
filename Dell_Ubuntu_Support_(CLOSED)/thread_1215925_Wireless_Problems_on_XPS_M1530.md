---
title: "Wireless Problems on XPS M1530"
date: 2009-07-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xtremeshredder on 2009-07-17
Hello,

I am using Ubuntu 9.04 and I cannot get my wireless to work (or even ethernet). I have tried using ndiswrapper only to get an error message that ndiswrapper is not a .conf file or something like that. and when i plug in my ethernet, at the top, the thing rotates and then suddenly says "Wired Network disconnected". I have not gotten either to work. I have also tried ndisgtk but did not get the windows driver to work.

Dell Wireless 1505 Draft 802.11n  WLAN Mini-Card
Marvell Yukon 88E8040 PCI-E Fast Ethernet Controller

---

### Post by coffeeaddict22 on 2009-07-18
Hi,
Wireless drivers for most Broadcom cards moved to be part of the distribution recently.  Which means a lot of us found we couldn't get wireless working after an upgrade, because ndiswrapper installs it's config files in your ~/home directory, so it doesn't get uninstalled with the upgrade.  And if I had to guess, that'll be your problem. 
Bottom line, you shouldn't need ndiswrapper (and you don't really want it if you can get a native Linux driver).  If you check in System/Admin/Hardware Drivers, there should be a wireless driver sitting there you need to activate; you should also uninstall ndiswrapper ("sudo modprobe -r ndiswrapper" should do the trick).

---

