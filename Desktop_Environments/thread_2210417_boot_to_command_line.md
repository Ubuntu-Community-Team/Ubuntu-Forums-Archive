---
title: "boot to command line"
date: 2014-03-10
forum: Desktop Environments
---

### Post by NyteRukh on 2014-03-10
hi, im running ubuntu 13.10 64bit on a lenova g530 laptop....earlier today i had installed plymouth manager to manage my boot animations...
now however when i boot up it goes straight to the command line...and from there i have to type sudo lightdm to get the graphical login screen. i tried several instructions found here on the forum like
unity --reset     nope
dconf reset -f /org/compiz    nope
nautlus -q             nope
sudo dpkg-reconfigure light dm nope
i ran cat /etc/X11/default-display-manager and light dm is the default manager
any help would be greatly appreciated thanks in advance



ok apparantly it's fixed....i re-installed plymouth manager and adjust some settings and rebooted...and it booted up like it should to the graphical logon screen

---

