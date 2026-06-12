---
title: "Ubuntu does not detect my LAN"
date: 2009-04-07
forum: General Help
---

### Post by maph3rs on 2009-04-07
Hi, Im very new to ubuntu and have not stopped singing its praises, however all of a sudden it does not recognise my LAN card. When i run the sudo eth0 commands i get the following:
ames@james-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:d4:ed:78:92  
          inet6 addr: fe80::213:d4ff:feed:7892/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1194 (1.1 KB)
          Interrupt:23 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:376 (376.0 B)  TX bytes:376 (376.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:91:02:de  
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe91:2de/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3500 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3677 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2629278 (2.6 MB)  TX bytes:645757 (645.7 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-12-17-91-02-DE-32-64-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

james@james-desktop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
james@james-desktop:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0.

I would appreciate any bodys help :o) Thanks in advance!

---

### Post by spiderbatdad on 2009-04-07
might take a look at /etc/network/interfaces and /etc/hosts
In /etc/hosts make sure james-desktop is listed after 127.0.0.1
In /etc/network/interfaces add or look for auto eth0

---

### Post by maph3rs on 2009-04-08
Thanks for your reply. How do i check in /etc/hosts  or /etc/network/interfaces?
I have right clicked the connection manager and deleted the LAN connection and tried to set it back up but it still does not connect.

---

### Post by garyalexza on 2009-04-08
You can use the vi (to edit) or less (to view).

> sudo vi /etc/hosts

---

### Post by maph3rs on 2009-04-08
> **garyalexza said:**
> You can use the vi (to edit) or less (to view).

So " less /etc/hosts "?
If its not listed do i need to add it? How do i do that?

---

### Post by spiderbatdad on 2009-04-11
```
gksu gedit /etc/network/interfaces
or 
gksu gedit /etc/hosts
```

---

