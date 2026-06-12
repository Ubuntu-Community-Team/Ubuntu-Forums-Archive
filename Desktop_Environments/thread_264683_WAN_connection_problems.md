---
title: "WAN connection problems"
date: 2006-09-25
forum: Desktop Environments
---

### Post by lerrup on 2006-09-25
I have a minimal home network consisting of 2 computers (a desktop and a laptop) connected to a router and then a cable modem; the laptop connects wirelessly.  The desktop runs dapper while the laptop dual-boots edgy and XP.  

Edgy cannot connect to the internet, it stopped being able to do this overnight with no changes being made to the system.  It can connect to the desktop via the network without any problem. None of the usual internet services can connect –I cannot ping any servers and so mail, web browsing, etc. are of course dead. Confusingly, both the desktop and XP can connect to the internet.  

Any ideas what the problem could be? Are there any settings that govern how the system connects to the outside world beyond the router?

---

### Post by dcstar on 2006-09-25
> **lerrup said:**
> I have a minimal home network consisting of 2 computers (a desktop and a laptop) connected to a router and then a cable modem; the laptop connects wirelessly.  The desktop runs dapper while the laptop dual-boots edgy and XP.  

Edgy cannot connect to the internet, it stopped being able to do this overnight with no changes being made to the system.  It can connect to the desktop via the network without any problem. None of the usual internet services can connect –I cannot ping any servers and so mail, web browsing, etc. are of course dead. Confusingly, both the desktop and XP can connect to the internet.  

Any ideas what the problem could be? Are there any settings that govern how the system connects to the outside world beyond the router?

Open a terminal and do:
```
ifconfig
netstat -rn
```

If you are using DHCP then you may have an issue with leases getting confused with the booting to different OS's

---

### Post by bigken on 2006-09-25
I have a the same problem except I can use the internet but not email or apt-get
this is my output 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:81:E4:64  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe81:e464/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4679 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3552 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5200365 (4.9 MiB)  TX bytes:498236 (486.5 KiB)
          Interrupt:7 Base address:0x2000 Memory:faffc000-faffcfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1

dont whats happend it has worked for over 6 months without fault and now it dont my adsl/router is a safecom SWAMR-54108 ](*,)

---

### Post by lerrup on 2006-09-25
Funnily enough, my router's a Safecom as well (SWBR-5400), haven't had a chance to try the commands (above) as I am in windows at the moment...

The router has worked well for 18mths up till now.

---

### Post by bigken on 2006-09-25
its doing my head in this is happening in dapper and edgy all is well in winxp ](*,)

---

### Post by lerrup on 2006-09-25
> **bigken said:**
> its doing my head in this is happening in dapper and edgy all is well in winxp ](*,)

Are you having this problem with Dapper?  I've filed a [bug]("https://launchpad.net/distros/ubuntu/+bug/62278").

---

### Post by bigken on 2006-09-25
yep it started on saturday after I did the updates ](*,)

---

### Post by bigken on 2006-09-25
sorted had to add dns to /etc/resolv.conf ;)

question is why now and not before ?

---

### Post by lerrup on 2006-09-26
> **bigken said:**
> sorted had to add dns to /etc/resolv.conf ;)

question is why now and not before ?

No idea; I used networkmanager and it seems to be working.

---

