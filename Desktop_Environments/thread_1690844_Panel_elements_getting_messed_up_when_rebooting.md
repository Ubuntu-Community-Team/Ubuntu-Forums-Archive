---
title: "Panel elements getting messed up when rebooting"
date: 2011-02-19
forum: Desktop Environments
---

### Post by bart13 on 2011-02-19
Hello. I've installed Ubuntu on my notebook, but when I reboot it panel elements are getteing messed up. Is there any way to fix it?

---

### Post by jerrrys on 2011-02-19
define 'messed up' or better post a pic

---

### Post by ve4cib on 2011-02-19
I've been noticing that every time I reboot the order of some of my panel applets are being changed.  To be more specific:

**Before reboot** (items listed from left to right)
Locked to left edge:
- Main Menu
- Indicator Applet (Appmenu)

Locked to right edge:
- Clock
- Workspace switcher
- Notificiation Area
- Indicator Applet (Complete)
- Window Buttons (from a PPA repo)

**After reboot**
Locked to left edge:
- same

Locked to right edge:
- Workspace switcher
- Notificiation Area
- Indicator Applet (Complete)
- Window Buttons (from a PPA repo)
- Clock

Basically the clock is just being moved all the way to the right, which is shuffling everything else over.  This only seems to be happening when I reboot.  Suspend is fine, as is log-out/log-back-in.  Haven't tried hibernating to see if that affects it too.

Not sure if this is the same issue the OP is having.  If not I'm sorry for hijacking the thread with my own problem.

---

### Post by jerrrys on 2011-02-20
after you get everything where you want it, lock icon.  are u doing that?

---

### Post by Krytarik on 2011-02-20
The shuffling happens when the resolution has been changed at any point, although it may not occur within the running session, but after relogin/reboot, even when all items are locked.

---

