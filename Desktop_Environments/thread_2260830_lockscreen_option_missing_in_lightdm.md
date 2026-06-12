---
title: "lockscreen option missing in lightdm"
date: 2015-01-14
forum: Desktop Environments
---

### Post by anbu-s on 2015-01-14
I'm using Ubuntu 14.04 with gnome. I switched my desktop display environment from gdm to lightdm.
Now I've no option to lock my screen, With gdm, i used to have this on the top bar (either lock or reboot/shutdown). 

After reading on this, I've remove gnome-screensaver and installed light locker and enable it that in the light locker setting. Nothing seem to work.

Command line light-locker- command -l works. But how do i get this option in the menu?

Please help

---

### Post by kerry_s on 2015-01-15
/etc/lightdm/lightdm.conf

there so many settings in there i don't know which you need.

---

### Post by anbu-s on 2015-01-15
> **kerry_s said:**
> /etc/lightdm/lightdm.conf

there so many settings in there i don't know which you need.

All I have in this file is this:

[SeatDefaults]
autologin-user=

Even the shortcut keys like super+L don't work. Same locks the laptop if I use gdm.

---

