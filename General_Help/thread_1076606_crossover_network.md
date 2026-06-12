---
title: "crossover network"
date: 2009-02-21
forum: General Help
---

### Post by bertolo on 2009-02-21
How can i configure a network for internet sharing using a crossover cable ?
i want to connect ubuntu 8.04 to linux mint 6.

thks all

---

### Post by doas777 on 2009-02-21
well, assuming you already have filesharing set up, all you really have to do is set up the IP addressing and plug in the cable.

on PC1 go to system -> administration -> Network, and unlock it.
select the interface that you plugged your crossover cable into, and click Properties.
Configuration: Static
IP Address : 192.168.0.1
SubnetMask: 255.255.255.0
GateWay: 192.168.0.1

then open a terminal and run:```
sudo ifdown <interface>
sudo ifup <interface>
```.

on the mint PC, you want to set
IP Address : 192.168.0.2
SubnetMask: 255.255.255.0
GateWay: 192.168.0.2

I don't know mint, so the steps will probably be different.

if you want to share an internet connection on one of the pcs, set the gateway on the other PC to point to the dual-networked one.


you can also set these settings in your /etc/network/interfaces file. check out this link for instructions [http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

if you need help setting up samba for file sharing check out this link:
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

there are other options for linux -> linux file serving, so you may wanna do some googling.

have fun

---

### Post by bertolo on 2009-02-21
mint pc is the one with internet :9....i want to pass internet to my ubuntu 8.04. mint it's equal to ubuntu
i dont understood where should i set the gateway

---

### Post by doas777 on 2009-02-21
ok, have the 8.04 box point to the mint box as gateway then. that way, all packets sent to an undesignated network (the internet for instance) will be sent to the mint box as the first hop.

8.04
IP Address : 192.168.0.1
SubnetMask: 255.255.255.0
GateWay: 192.168.0.2

mint
IP Address : 192.168.0.2
SubnetMask: 255.255.255.0
GateWay: <your network router>

if you don;t have a router (mint is directly connected to the ISP network), then use the ip address of the interface connected to the isp.

---

### Post by bertolo on 2009-02-21
ok thks :). lol now i figured that minst is not exactly the same, but i understand the ideia. thank you very much

---

### Post by bertolo on 2009-02-21
i only don't figured out what is brodcast address ... :/
i have what u said on ubuntu, but in mint i got 4 ip's
ip address:192.168.0.2
broadcast add:192.168.0.255 ?hum...?
subnet mask:255.255.255.0
default route:89.214.207.30

---

### Post by doas777 on 2009-02-21
a broadcast is a packet addressed to every host on a network. your broadcast address (192.168.0.255) is correct for a subnet mask 255.255.255.0.

everything looks good. should work.

hope that helps

---

### Post by bertolo on 2009-02-21
but it doesn't... :/
at least they are both conected.
i tried connect using telnet server in ubuntu 8.04 and telnet client in min and it did't work

---

### Post by doas777 on 2009-02-21
can they ping each other?

please post the output of 
```
sudo ifconfig

sudo route
```
from both boxes

---

### Post by bertolo on 2009-02-23
Mint : 
eth0      Link encap:Ethernet  HWaddr 00:08:54:0a:13:b8  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:10341 (10.3 KB)
          Interrupt:11 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30080 (30.0 KB)  TX bytes:30080 (30.0 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:89.214.141.121  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3950 errors:3 dropped:0 overruns:0 frame:0
          TX packets:3646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:4177794 (4.1 MB)  TX bytes:528576 (528.5 KB)

usb0      Link encap:Ethernet  HWaddr 36:0d:61:b2:f0:f8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:4 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.64.64.64     *               255.255.255.255 UH    0      0        0 ppp0
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 ppp0
default         10.64.64.64     0.0.0.0         UG    0      0        0 ppp0

Ubuntu 8.04

bertolo@bertolo:~$ sudo ifconfig
[sudo] password for bertolo: 
eth0      Link encap:Ethernet  HWaddr 00:17:31:5a:8d:6b  
          inet6 addr: fe80::217:31ff:fe5a:8d6b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:94 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:15076 (14.7 KB)  TX bytes:492 (492.0 B)
          Base address:0xc800 Memory:cdee0000-cdf00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1732 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1732 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86600 (84.5 KB)  TX bytes:86600 (84.5 KB)

bertolo@bertolo:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

---

### Post by doas777 on 2009-02-24
have you noticed that there is no IPv4 address in the 8.04 ifconfig? that is your problem. you need to set the eth0 interface on your 8.04 box to be 192.168.0.1.

---

