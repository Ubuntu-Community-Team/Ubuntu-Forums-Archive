---
title: "XPS M1330: Wireless stops working after 8.10 upgrade"
date: 2009-03-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by geoffm on 2009-03-03
I think I read at some point in the forum someone with the XPS 1330 saying he upgraded early to 8.10, a bunch of his stuff didn't work at first but eventually it got fixed in updates. So I went with the upgrade.
The first time I booted after the upgrade, I clicked the network icon in the panel, the wireless networks apeared, I selected the one I normally connect to and then everthing disappeared, including the network icon and the stuff filling the network settings window.
After another boot it became a little more normal, now the wireless *seems* to work (I can see the networks) but it won't connect to it!
I don't know much about configuring and troubleshooting drivers in linux.
I don't know where to get support... I figure Dell will tell me they don't support other versions than 8.04...

here's what ifconfig says
wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:cf:1d:2f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

here's what lshw says:
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 82:09:13:9c:f2:74
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Nxion on 2009-03-09
So you ran the upgrade and went from 8.04 to 8.10. I would say back up your data and reload from scratch. I tried doing a upgrade from 8.04 to 8.10 3 times and all three times failed with drivers getting screwed, mostly my wireless.

---

