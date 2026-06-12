---
title: "gnome login problem: edgy"
date: 2006-11-23
forum: Desktop Environments
---

### Post by dalem on 2006-11-23
I'm experiencing a problem logging into gnome. If I do a full reboot, I can login without any problems, but if I log out, I can't log back in. I just get a blue screen with a light colored terminal sized box in the left hand corner of the display. If I try to login using gnome-safe it locks up the display and the splash screen doesn't come up.

I can log into other window managers (fvwm xfce) without any problems. Just when I try and log back into gnome that I have trouble. I've tried deleting .gnome directory and .gnome2 directory but it still doesn't help.

Anyone else experience this?

---

### Post by dalem on 2006-11-23
What was causing the problem was network-manager, network-manager-gnome and the configuration I did to make nm-applet work. I followed the directions [here:]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html") and then edited my /etc/network/interfaces file as indicated. 

Somehow that caused a problem which is gone now that I removed network-manager and network-manager-gnome. I hope I can logon to a password protected hotspot...

---

