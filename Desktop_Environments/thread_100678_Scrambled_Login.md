---
title: "Scrambled Login?"
date: 2005-12-08
forum: Desktop Environments
---

### Post by wynterbourne on 2005-12-08
When booting up Ubuntu using GRUB, it comes to the graphical login screen but the problem occurs when attempting to log in from here. The mouse doesn't initially work and the keyboard is scrambled. 

IF I use the boot menu to log in using Recovery mode, which drops me down to root. From there I can GDM and log in successfully with mouse and keyboard support. 

How can I fix this so that I don't have to drop to root before logging in?

I'm a very new user, please be gentle.

[edit] Using fujitsu lifebook n 3010

---

### Post by Ampersand on 2005-12-08
Try booting normally and pressing Ctrl, Alt and F2 when you reach the login screen, and log in at the terminal screen that appears. Run
```
sudo dpkg-reconfigure xserver-xorg
```
then
```
sudo /etc/init.d/gdm restart
```
to restart the display manager (you may have to press Ctrl, Alt and F7 after this to get back to it)
or
```
sudo reboot
```
to restart.

---

### Post by wynterbourne on 2005-12-08
[QUOTE=Ampersand]Try booting normally and pressing Ctrl, Alt and F2 when you reach the login screen, and log in at the terminal screen that appears. Run
```
sudo dpkg-reconfigure xserver-xorg
```[/QUOTE]

If I boot normally, no keystrokes work properly. :confused:

---

