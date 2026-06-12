---
title: "How I can logout when Ubuntu freezes?"
date: 2013-12-06
forum: Desktop Environments
---

### Post by gal007 on 2013-12-06
Hi! I'm having a big trouble. Sometimes when I'm using some applications like Chrome or MagicDraw, Ubuntu freezes and I can't do anything but move the mouse or change to console mode (with CTRL+ALT+F1). I think if I could log off from console and restart the desktop, it would be faster to restart my computer, but I really don't know how to do that. Can you help me, please?

---

### Post by deadflowr on 2013-12-06
If you want to kill and restart the xsession 
then from the console (ctrl+alt+F1-6)
On older versions of Ubuntu(12.04)
```
sudo service lightdm restart
```
and newer versions
```
sudo restart lightdm
```
should work.
[More on lightdm]("https://wiki.ubuntu.com/LightDM")

Also note that the console session you start in tty1-6 will still be running,
so re-enter that and simply type exit and that session will close.

---

