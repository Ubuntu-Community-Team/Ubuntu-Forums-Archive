---
title: "intel installation"
date: 2009-05-13
forum: General Help
---

### Post by mario1 on 2009-05-13
hey guys im trying to get my intel drivers to work on ubuntu but with no success, pioneer makes the machine im trying to install it on and the instructions of how to do it are posted below but im extremely new to ubuntu and linux in general, is there anyway somebody could tell me exactly what to type in the terminal to get this working?

[instructions from pioneer]
If you are installing Ubuntu, all of the system drivers can be detected and installed automatically. But because Ubuntu is using intel's latest VGA driver it causes some problem. So you will have to edit the X configuration file, xorg.conf. Change the line with "Intel" to "i810" then restart the X windows and you should be fine.


--any help or info would be greatly appreciated, thanks!

---

### Post by mb_webguy on 2009-05-14
```
sudo gedit /etc/X11/xorg.conf
```
Look for the Device section, and the line that starts with Driver.  This should say "Intel".  Change "Intel" to "i810".  Save and exit, then reboot.

---

### Post by mario1 on 2009-05-14
thanks for the help, i did everything you said but had no luck, then i changed the name of the driver from "i810" to "intel" and it works alot better now, some things like compiz-fusion don't render properly but general desktop use and resolutions work great.

---

