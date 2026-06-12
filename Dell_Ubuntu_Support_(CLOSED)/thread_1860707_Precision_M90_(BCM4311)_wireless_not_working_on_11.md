---
title: "Precision M90 (BCM4311) wireless not working on 11.10"
date: 2011-10-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by postalservice14 on 2011-10-15
I can't seem to get my wireless to work after upgrading to 11.10.

Here is the output of "lspci -nnk | grep -iA2 net"
```
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
	Subsystem: Dell Device [1028:01cf]
	Kernel driver in use: tg3
--
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
	Subsystem: Dell Wireless 1490 Dual Band WLAN Mini-Card [1028:0007]
	Kernel modules: ssb
```

Also, I have firmware-b54-installer and b43-fwcutter installed and I've restarted.  Didn't seem to do anything different.
[[IMG]http://i.imgur.com/KAXGfl.png[/IMG]]("http://i.imgur.com/KAXGf.png")

ANY help would be hugely appreciated.

Thanks!

---

### Post by varunendra on 2011-10-17
Please post the current outputs of ***lspci -nnk | grep -iA2 net***, and ***lsmod***.

---

