---
title: "Dell Inpiron B120 Conneectivity"
date: 2012-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ira miles on 2012-05-29
Hi all, 
I just installed Ubuntu on this laptop (wiping out XP) and have only two initial issues. First, after downloading and installing the b43 firmware the computer, the computer sees the wireless network, but wont connect to it. It connects momentarily, and when I try to connect to google, it drops. I ran ifconfig and got the following:
eth0      Link encap:Ethernet  HWaddr 00:14:22:95:b8:19  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:5463 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3395963 (3.3 MB)  TX bytes:235776 (235.7 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:56551 (56.5 KB)  TX bytes:56551 (56.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:96:ce:c1:29  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:312 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29317 (29.3 KB)  TX bytes:58672 (58.6 KB)

Any help?

---

### Post by ira miles on 2012-05-29
Turns out I can connect to my home network. However, I wasn't able to keep a signal at the office network. Each time I opened a webpage there was no connectivity. Even at home the signal is quite weak. Is this due to a bad wireless card? Is there another alternative or anything I can do to improve my ability to pick up the signal?

---

