---
title: "Ubuntu 13.04 Gnome Shell - Reinstall gnome shell"
date: 2013-06-10
forum: Desktop Environments
---

### Post by SurfaceUnits on 2013-06-10
Was working in desktop, went up to Activities to open a program and computer locked up. Hit ctrl-alt-F1 and rebooted and now only the gnome fallback no effects DE will work (I have to have Gnome Settings Daemon disabled in Startup for it to work). Gnome DE brings up partial background image and then desktop icons, which are unresponsive and nothing else. Any help is appreciated.

---

### Post by dino99 on 2013-06-10
from synaptic, purge then reinstall gnome-shell
and also glance at ~/.xsession-errors to know about possible warnings/errors (ctrl+h to unhide that file)

---

### Post by SurfaceUnits on 2013-06-10
> **dino99 said:**
> from synaptic, purge then reinstall gnome-shell
and also glance at ~/.xsession-errors to know about possible warnings/errors (ctrl+h to unhide that file)

[http://we.tl/eE8TsQlqrs](http://we.tl/eE8TsQlqrs)   file here

---

### Post by SurfaceUnits on 2013-06-10
Will have to wait until the gnome3 team gets their repo unwhacked - details here  [http://ubuntuforums.org/showthread.php?t=2152404](http://ubuntuforums.org/showthread.php?t=2152404)

---

### Post by dino99 on 2013-06-10
sudo dpkg  --purge gnome-shell

should do the trick, and/or purge-ppa also might help in case

---

### Post by SurfaceUnits on 2013-06-10
Ran ppa-purge 2 times to get Current status: 0 broken [-14], 6 new [-2].
PPA purged successfully using aptitude fallback

Gnome Fallback is working without gnome settings daemon loaded
indicator-datetime-service has cpus at 90%

Gnome DE will load, but accessing Activities will lock up the desktop, the harddisk light lights up and have to restart computer to get out
gnome settings daemon still causing gnome de to crash

---

### Post by SurfaceUnits on 2013-06-10
Reinstalled gnome settings daemon and the problem it was causing in Fallback cleared up but it was consuming more and more memory, up to 2.3GB when I shut it down and disabled it again.

---

### Post by SurfaceUnits on 2013-06-11
Back to last month's backup iso

---

### Post by SurfaceUnits on 2013-06-14
Thank Chalchihuitlicue for /home
 Time for a new image backup

---

