---
title: "Bandwidth usage"
date: 2009-01-09
forum: General Help
---

### Post by 0perator on 2009-01-09
Is there a program that monitors the bandwidth a certain address is using, for instance if i were to set up 3 VHosts in an apache2 server, can i monitor the bandwith being used for each individual host?

---

### Post by 0perator on 2009-01-09
bump

---

### Post by unutbu on 2009-01-09
The output of ifconfig gives the bandwidth usage per interface. For example,

```
wlan0     Link encap:Ethernet  HWaddr 00:1c:f0:93:54:20  
          inet addr:192.168.1.81  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:f0ff:fe93:5420/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19979 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          **RX bytes:26917854 (26.9 MB)  TX bytes:1330551 (1.3 MB)**
```
shows 26.9 MB received and 1.3 MB sent.

If you want bandwidth usage segregated by process, then perhaps check out the nethogs package. I haven't used it myself, but the description sounds promising:

```
Description: Net top tool grouping bandwidth per process
 NetHogs is a small 'net top' tool. Instead of breaking the traffic down per
 protocol or per subnet, like most tools do, it groups bandwidth by process.
 NetHogs does not rely on a special kernel module to be loaded.

```

---

