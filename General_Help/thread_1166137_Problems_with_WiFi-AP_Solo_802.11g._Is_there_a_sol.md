---
title: "Problems with: WiFi-AP Solo 802.11g. Is there a solution?"
date: 2009-05-21
forum: General Help
---

### Post by Eirny on 2009-05-21
Hello everybody!

I have a problem with Ubuntu and WiFi-AP Solo 802.11g.
The problem is that it's working and everything. But the signal i get is very weak. When i used Windows, I had around 90-95% signal strenght. But now, when i'm using Ubuntu Jaunty Jackalope I have 10-15% Signal strenght.

I love everything i've seen of Ubuntu until now, and i don't wan't to go back to windows.

Does anybody have a solution for this?

Btw, this is my first post in here! 

Thanks! 

-Eirik
[B]
[/B]

---

### Post by Eirny on 2009-05-21
Noone that knows anything about it ?

---

### Post by terrrorr on 2009-05-21
Hi,

Could you please tell us what is your WiFi card/chopset and what drivers you are using. I got similar problems when I used Ubuntu 7.10 and Broadcom's WiFi chipset on Hp's laptop

```
sudo lshw -class network 
```

- Terrrorr

---

### Post by Eirny on 2009-05-22
Hi! 

Sorry for the late answer..  But this is what i got:

 *-network:0             
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:3e:c1:bd
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.0.0.2 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: ce:c0:6f:95:74:41
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

### Post by Eirny on 2009-05-22
The motherboard is a Asus M2N32-SLI Deluxe

---

