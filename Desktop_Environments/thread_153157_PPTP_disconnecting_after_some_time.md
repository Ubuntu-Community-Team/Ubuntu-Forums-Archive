---
title: "PPTP disconnecting after some time"
date: 2006-03-31
forum: Desktop Environments
---

### Post by pteja on 2006-03-31
I have (finally) successfully installed a PPTP client (pptpconfig). I can start the client from an icon in the toolbar. All cool!

After the connection is made, the internet connection drops after some time (no email & internet - cannot connect to sites/pop servers). Well, it doesn't actually drop - Skype for example remains connected and I can see packets getting up/downloaded. I compared the ifconfig entries before and after. For each of the entries a side-by-side comparison (there seems to be no difference at all:

Help!!!
---------------------------------------------------------------
puneet@ptejaubuntu:~$ ifconfig -a
(before disconnect)
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:DA:54:92
          inet6 addr: fe80::20f:b0ff:feda:5492/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x6000
----
(after disconnect)
eth0      Link encap:Ethernet  HWaddr 00:0F:B0:DA:54:92
          inet6 addr: fe80::20f:b0ff:feda:5492/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:21 Base address:0x6000
-------
(before disconnect)
eth1      Link encap:Ethernet  HWaddr 00:16:6F:08:CC:8A
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe08:cc8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26983 errors:0 dropped:6 overruns:0 frame:0
          TX packets:19978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16196540 (15.4 MiB)  TX bytes:2615202 (2.4 MiB)
          Interrupt:22 Base address:0x2000 Memory:c4007000-c4007fff
-----
(after disconnect)
eth1      Link encap:Ethernet  HWaddr 00:16:6F:08:CC:8A
          inet addr:10.0.0.11  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:6fff:fe08:cc8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:29922 errors:0 dropped:6 overruns:0 frame:0
          TX packets:22436 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18013120 (17.1 MiB)  TX bytes:3010112 (2.8 MiB)
          Interrupt:22 Base address:0x2000 Memory:c4007000-c4007fff
--------
(before  disconnect)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:429946 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429946 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:38108865 (36.3 MiB)  TX bytes:38108865 (36.3 MiB)
-----
(after disconnect)
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:464510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:464510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:41152103 (39.2 MiB)  TX bytes:41152103 (39.2 MiB)
-----
(before disconnect)
ppp0      Link encap:Point-to-Point Protocol
          inet addr:213.102.123.20  P-t-P:83.181.32.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:2516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:1789749 (1.7 MiB)  TX bytes:325900 (318.2 KiB)
----
(after disconnect)
ppp0      Link encap:Point-to-Point Protocol
          inet addr:213.102.123.20  P-t-P:83.181.32.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4649 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4635 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:3430321 (3.2 MiB)  TX bytes:605422 (591.2 KiB)

----
(before disconnect)
sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
---
(after disconnect)
sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---------------------------------------------------------------------------------------
after disconnect
pteja@ptejaubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
83.181.32.1     *               255.255.255.255 UH    0      0        0 ppp0
SpeedTouch.lan  *               255.255.255.255 UH    0      0        0 eth1
10.0.0.0        *               255.255.255.0   U     0      0        0 eth1
default         *               0.0.0.0         U     0      0        0 ppp0
------------------------------------

---

