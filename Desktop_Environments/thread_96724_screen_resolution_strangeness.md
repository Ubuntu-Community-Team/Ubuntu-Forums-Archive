---
title: "screen resolution strangeness"
date: 2005-11-29
forum: Desktop Environments
---

### Post by jgbiggs on 2005-11-29
When I boot up the gdm login screen is at 640x480, as is the desktop.  I tried changing the resolution via the menus but 640x480 was the only selection.

I had a look at /etc/X11/xorg.conf and saw multiple resolutions for color depths from 1 to 24.  I did a ctrl-alt-backspace and relogged in as a user and started x.  The desktop menus gave me all the resolutions available that were shown in /etc/xorg.conf.

Since the monitor is an LCD (1280x1024) I edited the /etc/xorg.conf file to only allow 1280x1024.

Rebooted.  I am still given the gdm screen at 640x480 as well as the desktop.  The only resolution available from the destop menus is still 640x480.

I did the ctrl-alt-backspace and went back into X, the menus still gave a multitude of screen resloutions.  Despite only have 1280x1027 in /etc/xorg.conf.

WTF?  Is the screen reslolution dictated by some other *.conf file?

Strange behavior.  (BTW this is on a clean 5.10 install)

---

### Post by teaker1s on 2005-11-29
sudo dpkg-reconfigure xserver-xorg

---

### Post by jgbiggs on 2005-11-29
I already tried that after the initial strangeness.  Why would gdm/desktop show up at 640x480, when it is not a listed resolution in /etc/xorg.conf?

---

