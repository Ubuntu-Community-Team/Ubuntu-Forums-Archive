---
title: "Spooky connection, gateway hassle"
date: 2009-05-03
forum: General Help
---

### Post by Liket on 2009-05-03
Hi, I have a strange problem. I have a ubuntu box that I have used as a gateway for my LAN. 

Ever since a fuse popped my ubuntu gateway has been unable to access the internet.
However, it is able to dynamically retrive ip from a router and use this router for dns requests. But it cannot ping the router... And the router does accept ping from other connected machines. 

eth0 is used for external connections.

the ifconfig, route, lookup and ping printouts:

```
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:dc:53:7c:99  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::210:dcff:fe53:7c99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1428 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123385 (123.3 KB)  TX bytes:150868 (150.8 KB)

eth2      Link encap:Ethernet  HWaddr 00:e0:43:b5:00:f3  
          inet addr:192.168.2.1  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:43ff:feb5:f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:4716 (4.7 KB)
          Interrupt:17 Base address:0x2700 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6042 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6042 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3652326 (3.6 MB)  TX bytes:3652326 (3.6 MB)

~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.2.0     *               255.255.255.0   U     0      0        0 eth2
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0

~$ nslookup www.google.com
Server:        192.168.1.1
Address:    192.168.1.1#53

Non-authoritative answer:
www.google.com    canonical name = www.l.google.com.
Name:    www.l.google.com
Address: 72.14.221.104
Name:    www.l.google.com
Address: 72.14.221.99
Name:    www.l.google.com
Address: 72.14.221.103

~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
^C
--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3014ms
```I'm hoping it's something very simple that I've overlooked.

thankfull for any help/ideas
//Liket

---

