---
title: "Network Connections Question"
date: 2009-04-24
forum: General Help
---

### Post by OneMixDJ on 2009-04-24
Greetings,

After converting my kids T22 laptop from XP to Ubuntu, I noticed some problems in getting the wireless started automatically.

First, let me back up a bit:

I configured both the Wired (eth0) and Wireless (eth1) with static addresses (my preference).  Both are checked to automatically connect, and both are checked as system settings.

What I am trying to do is have the Wired be the primary interface and the Wireless kick in if there is no Wired connection present. If I disconnect the ethernet cable, then I want the Wireless to activate in "failover" fashion and vice versa when I reconnect the cable. 

I tried configuring the metric of the wireless to a higher cost (25-30) to give "eth0" preference. But after I save my metric settings, then go back to check things, the route entries are gone as if they were never saved.

**Note: Yes, I am administrator (in case anyone asks...) and I do authenticate changes when prompted.*

Second problem I have is when booting up laptop without the cable to "eth0" connected, the Wireless doesn't turn on at all, even when checked to automatically connect. I would have to manually search for my wireless network and select it, put in the key, etc.

This creates a second wireless profile (automatic), which I do not want.

If I already have a working configuration in my Wireless tab, I shouldn't have to select my Wireless network every time I boot up the laptop. 

Instead, I expect it to be found and connect (especially when I know it's there). 

Below if a snapshot of my ifconfig. 
Note that the address on eth1 is DHCP as opposed to the preferred static.
Any help or direction would be most appreciated.


eth0      Link encap:Ethernet  HWaddr 00:01:03:84:ae:5c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 Base address:0x4400 

eth1      Link encap:Ethernet  HWaddr 00:06:25:01:de:b2  
          inet addr:**_192.168.26.210_**  Bcast:192.168.26.255  Mask:255.255.255.0
          inet6 addr: fe80::206:25ff:fe01:deb2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:178450 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112947 errors:180 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:205695475 (205.6 MB)  TX bytes:23558387 (23.5 MB)
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:404 errors:0 dropped:0 overruns:0 frame:0
          TX packets:404 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:27124 (27.1 KB)  TX bytes:27124 (27.1 KB)


Thanks!

---

