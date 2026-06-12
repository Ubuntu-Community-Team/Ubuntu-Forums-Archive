---
title: "secondary monitor in dual monitor setup not soming out of standby after TTY switch"
date: 2008-12-30
forum: Desktop Environments
---

### Post by hatchetman82 on 2008-12-30
Hi.

i have a dual-monitor setup running on 8.10 using the open source nv driver.
the screens are configured using xrandr in XSession.d, and the display works ok after logging in.

when i switch to TTY1 (using CTRL + ALT + F1) the terminal is displayed on the main monitor while the secondary shuts down (goes into standby).

the problem is that when i return to X (using CTRL + ALT + F7) the secondary omnitor remains in standby.

i've tried re-configuring it using xranr from a terminal (this time a graphical terminal running on the gnome desktop) but to no avail - i cant make it turn on and display anything.

Thanks in advance for any assistance.

---

### Post by hatchetman82 on 2008-12-31
well, seeing as no one here had any ideas, i filed an xorg bug report about this issue here : [https://bugs.freedesktop.org/show_bug.cgi?id=19349](https://bugs.freedesktop.org/show_bug.cgi?id=19349)

---

