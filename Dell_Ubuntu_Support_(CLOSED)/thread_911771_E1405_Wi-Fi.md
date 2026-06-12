---
title: "E1405 Wi-Fi"
date: 2008-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Buckman on 2008-09-06
Alright, I'm a new Ubuntu user.  I finally got my wi-fi card working.  It's a Broadcom 1390 wlan card.  The computer is a Dell Inspiron e1405.  The problem is, is that when I restart my computer, I have to go into "Hardware Drivers" and disable and re-enable the driver for the wi-fi light to come on.

Here's what I did to get the card working.  I installed ndiswrapper-utils, ndiswrapper common, and ndiswrapper.  Using ndiswrapper I installed the bcmwl5.inf driver.  Then I blacklisted all of the Broadcom 43xx drivers.  After that, the wi-fi light still didnt come on, but under the "Windows Wireless Driver" application, it shows that the driver is working and hardware is present.

Well during all of this I had the computer plugged into the internet, and after I restarted the computer after doing all of the ndiswrapper stuff, in the top corner I find that there is a "driver update" with driver "Broadcom B43" driver.  After I installed it, the wi-fi works.

The thing is, is that when I re-start the computer, the driver is "enabled" but to the right of it, it says "not in use."  If I disable it and re-enable it, it says "in use."

If this makes sense to anyone, anyone care to help me get this problem figured out so I don't have to keep turning the driver on and off?

---

