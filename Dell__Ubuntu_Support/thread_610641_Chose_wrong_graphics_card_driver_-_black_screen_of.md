---
title: "Chose wrong graphics card driver - black screen of death on load."
date: 2007-11-12
forum: Dell  Ubuntu Support
---

### Post by ftaylor on 2007-11-12
I'm a complete novice with Linux. I have an ATI Radeon Mobility graphics card. I was playing about with the graphics settings in my ubuntu installation to try and use an ATI driver for it. Now when I try and load Ubuntu 7.1.0 all I get is a black screen. Is there anything I can type into the recovery mode console to revert back to the generic driver?

---

### Post by Sandlst on 2007-11-12
You could edit the xorg.conf file with nano by using the command ```
sudo nano /etc/X11/xorg.conf
```To switch drivers back (when done, press F2 then y to save).  
Also, you could enter ```
sudo dpkg-reconfigure xserver-xorg
```That will reconfigure X for you, just be sure to select the right video driver when it asks, and leave questions to the default answer if you are unsure about them.  Good luck, post back if you have any problems.

---

