---
title: "Inspiron 1525"
date: 2010-08-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JBUZ on 2010-08-17
I just installed the latest Ubuntu (Lynx) and, as with others, wireless isn't working. I've tried a few of the common solutions and nothing is working. Even using the cable directly in my laptop isn't helping, still can't connect to the internet.
 
I think my wireless card is Brodcom 4312.
Help?

---

### Post by jcolyn on 2010-08-17
> **JBUZ said:**
> I just installed the latest Ubuntu (Lynx) and, as with others, wireless isn't working. I've tried a few of the common solutions and nothing is working. Even using the cable directly in my laptop isn't helping, still can't connect to the internet.
 
I think my wireless card is Brodcom 4312.
Help?

First you will need to be wired to the internet.

If you are using KDE Menu-Applications-System-Hardware Drivers.

If you are using Gnome System-Administration-Hardware Drivers.

Click the hardware icon, enter your password and wait till it finds your driver then click Activate..

---

### Post by JBUZ on 2010-08-17
I can't get on the internet at all, even with my ethernet plugged into the laptop so I'm using a friend's. Nothing is showing up with hardware drivers either.

---

### Post by theepdinker on 2010-08-21
Here's the driver information that works on my Dell 1501:

Broadcom STA wireless driver
These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

I had to connect to the internet via hardwire, and the instructions above automatically loaded the driver.

---

### Post by mörgæs on 2010-08-22
If wired access is still a problem: Do you get wired access, if you boot a 10.04.1 (not 10.04.0) live Ubuntu?

---

