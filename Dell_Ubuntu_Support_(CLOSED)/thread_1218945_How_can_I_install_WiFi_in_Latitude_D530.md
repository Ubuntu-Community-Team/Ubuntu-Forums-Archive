---
title: "How can I install WiFi in Latitude D530?"
date: 2009-07-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by karumudi7 on 2009-07-21
Hi friends! I am new to Ubuntu!I am using Ubuntu 8.04 on my DELL Latitude D530 laptop.

In ubuntu 9.04 the wifi which came by default is working fine but I want to install in ubuntu 8.04!!!

I want a complete description of installing WiFi on my Laptop!
Plz help me!!!!

---

### Post by karumudi7 on 2009-07-21
Hi friends! I am new to Ubuntu!I am using Ubuntu 8.04 on my DELL Latitude D530 laptop.

The wifi which came in ubuntu 9.04 by default is working fine in my laptop,but I want to install wifi in ubuntu 8.04

I want a complete description of installing WiFi on my Laptop!
Plz help me!!!!

---

### Post by coffeeaddict22 on 2009-07-21
Hi,
The wifi drivers all went into the kernel after 8.04.  You're looking at having to use ndiswrapper- which is as good a reason to stay on 9.04 as anyone could wish for.  If you look [here on the wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") you should find all you need.

---

### Post by MartynT on 2009-07-22
Does anyone know if 9.04 supports Dell's new 1510 wireless n card ?

8.04 doesn't seem to (out of the box).

---

### Post by adempewolff on 2009-07-22
MartynT - It looks like people have had some success using ndiswrapper with your driver with 8.04 - [http://ubuntuforums.org/showthread.php?t=857532&highlight=Dell+1510](http://ubuntuforums.org/showthread.php?t=857532&highlight=Dell+1510)

A lot of cards that needed ndiswrapper solutions in 8.04 work out of box in 9.04.  I would recommend getting a 9.04 live cd and seeing if it works for you and then upgrading if it works and you do not have any other problems with it.

karumudi7-  I have a D630, which I think has a similar chipset for the wireless card.

Please open a terminal (Applications menu -> Accessories -> Terminal) and type
```
lspci
```

somewhere in the list it will have something similar to (this is the entry for my wireless card):
```
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
```

paste the entire output here if you cannot understand it.  This will help determine which chipset your wireless uses and I can direct you to a how to.


However, IMO, I would just stick with 9.04 if it works well.  I have been using it since it comes out with my Dell and I found it fixed many annoying bugs and is very stable.

---

