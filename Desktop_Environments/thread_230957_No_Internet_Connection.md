---
title: "No Internet Connection"
date: 2006-08-06
forum: Desktop Environments
---

### Post by Ryan H on 2006-08-06
After deleting Fedora Core 5 and getting Grub to work with Ubuntu again I can't connect to the internet. I allways used to be able to use the internet with no problem. And on Knoppic 4.0 Live at first I could, then Kouquer couldn't find the host. After booting up to Ubuntu I also couldn't connect to anything. And there isn't an IP address asigned to my computer. I use cable and I am running Ubuntu Drapper Drake 6.06 64-Bit version.

-Ryan H

---

### Post by Ryan H on 2006-08-06
I could really use any help you guys would have.

-Ryan H

---

### Post by dennisharrison on 2006-08-06
do you have your default gateway setup under network conections?

---

### Post by stoeptegel on 2006-08-06
How is the IP on your computer assigned, static or dynamic?
Have your tried restarting your modem/router?
What does *ifconfig* say?
If using DHCP (dynamic), have you tried *sudo dhclient*?

---

### Post by Ryan H on 2006-08-06
I tried restarting the router, but it works on the other computers connected, so.
It's assigned dynamicaly.
ifconfig says ```
Etho0
Link encap:Ethernet  HWaddr 00:13:D4:A4:AC:17
inet6 addr: fe80::213:d4ff:fea4:ac17/64 Scope:Link
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
RX packets:467 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:61313 (59.8 KiB)  TX bytes:0 (0.0 b)
Interrrupt:50
```
*sudo dhclient* Says No DHCPOFFERS recieved.

-Ryan H

---

### Post by dennisharrison on 2006-08-06
what happens if you switch that computer to static and configure it inside of the scope the dhcp server is assigned to?

---

### Post by Ryan H on 2006-08-06
How do I do that?

-Ryan H

---

### Post by dennisharrison on 2006-08-06
system settings / network settings / administrator mode (enter password) / right click on the network interface you are using / configure interface / manual / check activate when computer starts / advanced settings / fill in gateway and ip address fields / click ok / click on the routes tab / fill in default gateway / apply 

reset your connection and see if it works

---

### Post by peabody on 2006-08-07
What kind of ethernet adapter?  Wireless or Wired?  If I recall, Fedora's kernel has some support for the nforce onboard ethernet that Ubuntu and other distros don't out of the box (easy download to get working, although how do you download it if your Internet isn't working :D).

---

### Post by Ryan H on 2006-08-07
> **peabody said:**
> What kind of ethernet adapter?  Wireless or Wired?  If I recall, Fedora's kernel has some support for the nforce onboard ethernet that Ubuntu and other distros don't out of the box (easy download to get working, although how do you download it if your Internet isn't working :D).
Um, I'm using Gnome, is that for KDE?

It's wired. And it was working in Ubuntu before without me doing anything.

-Ryan H

---

### Post by peabody on 2006-08-07
It was just a guess at your ethernet card, if it was working in Ubuntu before, then that's not the problem.  You might want to try and post information from the dmesg command with any "eth0" lines in them.

---

### Post by Ryan H on 2006-08-07
Well I'm on another computer so I can't copy and paste. But there is around 1000 lines about eth0. There will be a sentence about eth0 then a lot of numbers and 8-bit alphanumerical characters. The last one is > 64436.135159 nv_stop_tx: TransmitterStatus remained busy<7>eth0: tx_timeout: dead entries!

-Ryan H

---

### Post by kvalis on 2006-08-07
Hallo there Ryan

I presume your card is eth0 and not etho0 as listed from your ifconfig.

This might be a shot in the dark, but open a terminal windows and try to start your connection with the command:

**sudo ifup eth0**

Then you hopefully get something like this:

I> nternet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/eth0/00:0c:76:26:4f:7e
Sending on   LPF/eth0/00:0c:76:26:4f:7e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.106 -- renewal in 34283 seconds.


I have that problem that I have to restart my connection every time I reboot my PC.

Kvalis

---

### Post by Ryan H on 2006-08-07
I get the response: > ifup: interface eth0 already configured

-Ryan H

---

### Post by Ryan H on 2006-08-07
Bump.

---

### Post by louistan3 on 2006-08-07
maybe your DNS aint set up right.. just a guess :)

---

### Post by Ryan H on 2006-08-07
How do I set it right?

-Ryan H

---

### Post by louistan3 on 2006-08-07
ud have to knw the IP addresses of ur isp's DNS servers.. then go to system > administration > networking .. click on ur network card.. then properties.. then i thnk thers a tab there for DNS.. 

im not sure on that cos im in not at my ubuntu box right now.. il get back to you later when i get home if thats not right.. or some other people might be able to tell you.. 

hope this helps..[-o<

---

### Post by stoeptegel on 2006-08-07
If you can ping google,
ping 64.233.167.99
then indeed your internet works and there's probably a dns issue.

---

### Post by Ryan H on 2006-08-07
It says: > connect: Network is unreachable

=\

-Ryan

---

### Post by louistan3 on 2006-08-08
maybe its a firewall issue? somethings blocking u from goin out of the network? if u have another box, try pinging that..

---

