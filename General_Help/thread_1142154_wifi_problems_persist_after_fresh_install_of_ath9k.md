---
title: "wifi problems persist after fresh install of ath9k"
date: 2009-04-28
forum: General Help
---

### Post by asuastrophysics on 2009-04-28
(i hate to start another trouble with wireless thread, but i couldnt find an answer to this anywhere else)

i'm puzzled here. 

i followed this guide to install ath9k:
[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)
(i hate the ...abbreviation thing that happens when u post long URLs in these forums. it makes following a link impossible)

i succeeded, but i still cant connect to any wireless networks. it just says connecting...and then it drops it.
this is sporadic, too, because earlier today it was connecting to my home network. Now it won't connect to any. 

can anyone help me save some time here by telling me what is wrong? 
```
lspci
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)

```

```
ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:68:3f:42:80  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:fe3f:4280/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2519 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2865843 (2.8 MB)  TX bytes:457008 (457.0 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12240 (12.2 KB)  TX bytes:12240 (12.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:e1:11:4c:fd  
          inet6 addr: fe80::21f:e1ff:fe11:4cfd/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:151418 (151.4 KB)  TX bytes:6320 (6.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1F-E1-11-4C-FD-63-66-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

iwlist scan shows tons of networks, none of them connectable. 

Acer Aspire 4720Z Laptop
Atheros AR5BXB63

will provide any other info on request. thanks!!

---

