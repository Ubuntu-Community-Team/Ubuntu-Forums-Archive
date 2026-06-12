---
title: "[SOLVED] xserver trying to start wacom"
date: 2007-04-25
forum: Desktop Environments
---

### Post by DantePasquale on 2007-04-25
Hi, I had a failure on my laptop HP Pavilion dv1000 running 6.06 LTS on the / file system. When fsck corrected the errors the graphic display no longer starts up properly. I get a spinner and the mouse moves, but that's it. <ctrl-alt>bksp 3 or 4 times it finally pukes. the log file errors only have one error, multiple times, and that error is that it can't open /dev/wacom. Where is this coming from??? I ran dpkg-reconfigure xserver-xorg and it still is there????? :confused: 

URGENT HELP NEEDED! Do not want to re-install 6.06 once again (3x already).

 
Dante

---

### Post by RedSquirrel on 2007-04-25
If you look in /etc/X11/xorg.conf, there will be some lines about the /dev/wacom device. You can comment them out (put # in front) or delete them altogether if you don't have a wacom device. There will likely also be entries for "eraser", "stylus", and "cursor" in the ServerLayout section near the end of the xorg.conf file. Get rid of those too.

Make a backup of xorg.conf first, just in case something goes wrong:

```
 sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```Then edit xorg.conf to make the changes:

```
 gksudo gedit /etc/X11/xorg.conf
```or if you prefer nano:

```
 sudo nano -w /etc/X11/xorg.conf
```

It sounds to me like you're having hardware issues though. I have my doubts that simply removing the wacom lines will be the total cure.

---

### Post by DantePasquale on 2007-04-26
RESOLVED: 

Hi, Thanks for the info and I'll keep that in mind if that ever happens again. It turns out that more files than the xorg.conf file were toast. I couldn't start vi, more, and most shell commands so I re-installed again!

Culprit is bad memory probably caused by the laptop over heating because acpi doesn't see the fan.

I'm getting pretty good at re-installing ;)

Dante

---

