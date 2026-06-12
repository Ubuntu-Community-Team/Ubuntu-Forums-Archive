---
title: "Gaim Messenger not working in Wifi Dell B130"
date: 2007-07-10
forum: Dell  Ubuntu Support
---

### Post by hiltonman78 on 2007-07-10
Hi I just got the drivers on my dell installed and just got the wifi working as well.  My problem is that the gaim doesn't seem to think it can connect or doesn't see the connection.  Not really sure what it thinks.  All I know is when I use the wifi radar to connect to the internet gaim will not connect.  It opens.  It shows up but for some reason will not connect.  My computer is a dell b130.  I am running a broadcom chipset. 


brett@brett-laptop:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I looked around i forums and did not see this issue with anyone else.  I am using wifi radar as my wireless connection program.  Any help would be appreciated thanks.  Brett

---

### Post by scrooge_74 on 2007-07-19
Try using network-manager instead of wifi-radar. You will probably have better luck.  Broadcom cards are hard to configure.  I have one myself.

For me I had to follow [this]("http://www.ubuntuforums.org/showthread.php?t=185174") to get it working

---

### Post by hiltonman78 on 2007-07-22
Thanks for the heads up.  I changed to a different messenger which works well on wireless.  I think its called Kopete.  A very versitle messenger like game.  Brett

---

### Post by chyrania on 2007-07-22
> **hiltonman78 said:**
> Hi I just got the drivers on my dell installed and just got the wifi working as well.  My problem is that the gaim doesn't seem to think it can connect or doesn't see the connection.  Not really sure what it thinks.  All I know is when I use the wifi radar to connect to the internet gaim will not connect.  It opens.  It shows up but for some reason will not connect.  My computer is a dell b130.  I am running a broadcom chipset. 


brett@brett-laptop:~$ lspci | grep Broadcom\ Corporation
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

I looked around i forums and did not see this issue with anyone else.  I am using wifi radar as my wireless connection program.  Any help would be appreciated thanks.  Brett

From my limited experience of gaim, I would say look at your connection settings in preferences. You may find gaim is trying to use an unsuitable connection method for the service you are trying to connect to.

---

