---
title: "Monitor Display Problem"
date: 2009-04-15
forum: General Help
---

### Post by rpg on 2009-04-15
I am running Hardy on a desktop.  After I opened the box to insert a
second hard drive, the system would not boot.  When I finally got it
booted (through failsafe, without, I believe, changing any settings),
the hard drive worked fine.  Now it reboots ok, but objects on the
screen (terminal windows, browser windows, application boxes, icons)
are about 2/3 their normal size (even though I have access to the
entire screen).  Furthermore, use of "resize" in the drop-down box on
a terminal window causes the system to hang.

These features (small objects, hang on resize) persist if I log in
as a different user; and even if I boot off of the original
Ubuntu-Live disk!

The file /etc/X11/xorg.conf was not changed (according to its date).
If I attempt to change the resolution (currently 1280x1024) the
screen flickers, and I must reboot.

I'm stumped.  I'd appreciate any suggestions.

---

### Post by JK3mp on 2009-04-15
Do you have it as a full install or are you running it live? Is it your only OS on it or are u dual booting? I would take care of the hardware change in a diffrent OS if you have it (mac, windows). As for the monitor size im gonna assume you tried using the display settings to set your type of monitor and screen resolution?

---

### Post by sahabcse on 2009-04-15
hi

Try to reconfigure the xonfig

#sudo dpkg-reconfigure -phigh xserver-xorg

Then type 

#startx

---

### Post by rpg on 2009-04-15
> **JK3mp said:**
> Do you have it as a full install or are you running it live? Is it your only OS on it or are u dual booting? I would take care of the hardware change in a diffrent OS if you have it (mac, windows). As for the monitor size im gonna assume you tried using the display settings to set your type of monitor and screen resolution?
The Hardy is fully installed.  I am dual with a Windows distribution.  I never set any monitor values explicitly -- I just installed off the Ubuntu-Live disk.  Everything  was working fine before this problem. Somehow, the hardware change started this, but I cannot believe it is the current problem (since I have the same problem when I just run off the Live disk).  Thanks . . .

---

