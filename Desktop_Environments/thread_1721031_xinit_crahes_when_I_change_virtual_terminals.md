---
title: "xinit crahes when I change virtual terminals"
date: 2011-04-03
forum: Desktop Environments
---

### Post by gizmo720 on 2011-04-03
I am running Ubuntu 10.10. When I manually run xinit from a virtual terminal it works as expected, however when I switch terminals, then switch back, xinit has stopped working, but is still running in the terminal until I ^C it. The last three lines printed (those following the 'Markers' section) read:
(==) Log file: "?var/log/Xorg.).log", TIme: Sun Apr 3 23:36:19:2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) [KMS] Kernel modesetting enabled.

The last line in the logfile says:
[ 4844.640] (II) AIGLX: Suspending AIGLX clients for VT switch

I tried this with TWM running when i switched, and nothing running when I switched.

I am able to switch to and from my normal desktop (tty7, running gnome)fine

---

