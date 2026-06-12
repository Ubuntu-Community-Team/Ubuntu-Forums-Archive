---
title: "Slow ethernet transfers"
date: 2009-05-03
forum: General Help
---

### Post by spearmint100 on 2009-05-03
Hello, I have ubuntu 8.10 and slow ethernet transfers when copying files. its around 1.9MB / Sec. Can someone give me a idea how to increase the speed? I have attached my ipconfig. Thanks

alan@Server:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:f0:4c:4f:87  
          inet addr:192.168.0.12  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:f0ff:fe4c:4f87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1901685 errors:1 dropped:0 overruns:0 frame:0
          TX packets:1248101 errors:9 dropped:0 overruns:0 carrier:9
          collisions:0 txqueuelen:1000 
          RX bytes:2328069435 (2.3 GB)  TX bytes:672921010 (672.9 MB)
          Interrupt:11 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:129 errors:0 dropped:0 overruns:0 frame:0
          TX packets:129 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14560 (14.5 KB)  TX bytes:14560 (14.5 KB)

---

