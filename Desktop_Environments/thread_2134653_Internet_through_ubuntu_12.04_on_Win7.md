---
title: "Internet through ubuntu 12.04 on Win7"
date: 2013-04-11
forum: Desktop Environments
---

### Post by Matth1as on 2013-04-11
I'm trying to access the internet on my desktop machine (win7) through my laptop (ubuntu 12.04) via wifi. But I have tried everything and come up short. Trying a lot of google searches gave me only information about connecting from windows to ubuntu! I use ubuntu all the time on my laptop in school and at home so i'm comfortable using the terminal system and editing config files. This is my first time calling out for help! I get no internet access on the windows machine and ubuntu let's me know constantly the ethernet connection is disabled and tries to reconnect coming back with the same message. I have a crossover cat5 cable. I have allow all user checked in wifi settings on ubuntu.

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:90:f5:c9:e0:74  
          inet6 addr: fe80::290:f5ff:fec9:e074/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:371 errors:0 dropped:16 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42402 (42.4 KB)  TX bytes:65179 (65.1 KB)
          Interrupt:20 Memory:f7e00000-f7e20000 

ipconfig /all
Ethernet adapter Local Area Connection:


   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Realtek RTL8168B/8111B Family PCI-E Gigab
it Ethernet NIC (NDIS 6.20)
   Physical Address. . . . . . . . . : 00-19-DB-F6-5D-E6
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::a80a:b607:a55c:bd63%11(Preferred)
   Autoconfiguration IPv4 Address. . : 169.254.189.99(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.0.0
   Default Gateway . . . . . . . . . :
   DHCPv6 IAID . . . . . . . . . . . : 234887643
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-18-E2-59-5E-00-19-DB-F6-5D-E6

---

