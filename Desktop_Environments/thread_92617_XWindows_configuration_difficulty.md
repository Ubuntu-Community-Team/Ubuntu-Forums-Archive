---
title: "XWindows configuration difficulty"
date: 2005-11-20
forum: Desktop Environments
---

### Post by Iam8up on 2005-11-20
Upon booting Ubuntu and starting the GNOME Desktop Manager I get X Windows errors.  In the beginning of the X configuration file it suggests trying the command **sudo dpkg-reconfigure -phigh xserver-xorg**.  I select the nv driver set, hit return, and it closes out with the error: xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2005.11.200029

From what I can understand my problem is:
```
(EE) No devices detected.

Fatal server error:
no screens found
```

Which I don't understand - the PCI nVidia GeForce FX 5200 is obviously connected, I'm viewing things with it...

I've attached some notes I've saved, a log, and my conf file for X.

Thanks in advance for anyone that can offer any information to help me!

---

### Post by iH8forcedRegistration on 2005-11-20
Try commenting out the VideoRam line.

---

