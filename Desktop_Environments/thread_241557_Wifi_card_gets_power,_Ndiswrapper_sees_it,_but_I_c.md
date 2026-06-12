---
title: "Wifi card gets power, Ndiswrapper sees it, but I cant connect!"
date: 2006-08-22
forum: Desktop Environments
---

### Post by nzk on 2006-08-22
I installed ndiswrapper, configured it for my wificard, and rebooted

Now the little blinking (now they are solid) lights are on, but I am not getting a connection! Why?!

Its a Belkin F5D8010 with some airgo chipset or something the wiki for ndiswrapper said to use some netgear card drivers, which worked


ndiswrapper -l returns:
Installed ndis drivers:
netani driver present, hardware present


Thanks in advance

---

### Post by nzk on 2006-08-22
Bump...argh

---

### Post by snakyjake on 2006-08-23
Might want to try from the command line.  I usually find it easier, faster, less fickle, and works no matter what distribution or X windows I'm playing on.

To see if the card is recognized, or get status of the card:
ifconfig (example: ifconfig wlan0)

Scan for access points:
iwlist scan

Configure what access point to connect to:
iwconfig (example: iwconfig wlan0 essid Jake)

Connect to access point:
dhclient (example: dhclient wlan0)

---

### Post by nzk on 2006-08-23
OOps I forgot about this...

Damn submit button madde a double thread

---

