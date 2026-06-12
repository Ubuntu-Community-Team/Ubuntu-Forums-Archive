---
title: "Wired Ethernet Not Working"
date: 2005-11-17
forum: Desktop Environments
---

### Post by Agarax on 2005-11-17
I just got the 5.10 Live CD and booted it up on my Dell Inspiron 6000 laptop to try out Ubuntu.

Problem is that it won't connect to the internet through my wired network through my onboard ethernet.

The Cat 5 cable is plugged in and I restarted it twice (service network restart wasn't working for some reason) but it still wouldn't work.

---

### Post by Goddess_of_Linux on 2005-11-17
Are you using a router... If you aren't then you need to wait 4 hours or a little more and then you will be able to get on the net. I haven't used linux yet but I have had this problem with Mac OSX and Windows XP sharing the same direct dsl modem connection. One would not give up its IP address that was stored in the modem and the other wouldn't get that IP address and use it. 

The best remedy for this problem is to go out and by a wired or wireless router from D-Link or NetGear or Linksys or Belkin, my favorite is D-Link. and once you get it activate DHCP server on it and it will give Windows its own IP and then when you use Linux or OSX it give it its own IP address.

---

### Post by Agarax on 2005-11-18
I am using a router.

---

### Post by Goddess_of_Linux on 2005-11-18
Is it working as a DHCP server... most routers are capable but don't have it enabled by default...

---

### Post by kosmic on 2005-11-18
please post where the result of the comand 
 
sudo ifconfig

---

### Post by Agarax on 2005-11-18
[QUOTE=Goddess_of_Linux]Is it working as a DHCP server... most routers are capable but don't have it enabled by default...[/QUOTE]

I would assume so, considering I am talking to you right now from my Windows drive on  the same connection.

[QUOTE=kosmic]please post where the result of the comand 
 
sudo ifconfig[/QUOTE]

eth0      Link encap:Ethernet  HWaddr 00:12:3F:E7:60:05  
          inet6 addr: fe80::212:3fff:fee7:6005/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69095 (67.4 KiB)  TX bytes:1090 (1.0 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:414501 (404.7 KiB)  TX bytes:414501 (404.7 KiB)

I tried to ping google.com but it didn't work.

---

### Post by dcstar on 2005-11-19
[QUOTE=Agarax]I would assume so, considering I am talking to you right now from my Windows drive on  the same connection.



eth0      Link encap:Ethernet  HWaddr 00:12:3F:E7:60:05  
          inet6 addr: fe80::212:3fff:fee7:6005/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:493 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69095 (67.4 KiB)  TX bytes:1090 (1.0 KiB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4561 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:414501 (404.7 KiB)  TX bytes:414501 (404.7 KiB)

I tried to ping google.com but it didn't work.[/QUOTE]
There is no IP4 address allocated to your connection.

Go to System-Administration-Networking and select a Static address, and fill in the appropriate details for your system.

If you want to use DHCP, go in Synaptic and make sure the DHCP3-client is installed.

This is what my ifconfig looks like by comparison (I also have IP6 disabled):

eth0      Link encap:Ethernet  HWaddr 00:0D:61:22:B6:60
          **inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0**
          UP BROADCAST RUNNING MULTICAST  MTU:1472  Metric:1
          RX packets:4912 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4336005 (4.1 MiB)  TX bytes:563999 (550.7 KiB)
          Interrupt:18 Base address:0xe400
........

---

### Post by Vorian on 2005-11-20
```
dhclient eth0
``` should do the trick

---

