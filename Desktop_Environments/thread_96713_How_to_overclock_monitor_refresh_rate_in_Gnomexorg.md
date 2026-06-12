---
title: "How to overclock monitor refresh rate in Gnome/xorg?"
date: 2005-11-29
forum: Desktop Environments
---

### Post by Altefrau on 2005-11-29
Hi, I have a simple question:
Is it possible to overclock my monitor to use 1600x1200@70Hz or more? At the moment it uses 1600x1200@60Hz, which is a bit too low...

My Monitor is an Sun GDM 20E20 with a selfmade 13W13-VGA-connector. horiz 31.5-84.5, vert 50.0-120.0. Graphics card is an Ati Radeon 9600.

I know that this could damage my screen, but I'd like to take that risk :)

---

### Post by Remmelas on 2005-11-29
It's possible by specifying ModeLines in your xorg.conf file, but you are correct that it can (and likely WILL) damage your monitor.  I had a monitor with refresh rates ranging 30-70(Horiz) and 50-160(Vert), bumped my monitor from 60 to 75hz refresh at 1280x1024(monitor was rated for 60hz at this resolution), and the monitor was dead within a week.

---

### Post by Altefrau on 2005-11-29
Hm, do you have an working modeline for me? I tried some, but either Gnome would not start or the screen remained in standby-mode. So I guess you made it to work in an overclocked mode?

---

### Post by Remmelas on 2005-11-29
Well, i don't have those modelines anymore since that monitor was fried, and every model seems to have different modelines for how far you can overclock.  The other problem with overclocking monitors, is the newer ones usually protect themselves by going into standby when they hit a refresh rate they can't handle, which sounds like is what is happening to you.  I don't know if there is a way to disable that.

---

