---
title: "Dual monitors setup, mouse disappears in invisible area"
date: 2008-04-28
forum: Desktop Environments
---

### Post by mairabc on 2008-04-28
I have an ATI X1150 graphics card, running with the open source driver, in a very clean installation of the final release of Hardy Heron 8.04. 

After struggling a bit with the gnome-display-properties, I managed to get my dual monitors setup (Laptop screen 1280x800 and a HP external monitor 1680x1050) running quite well (attached is my xorg.conf).

The only problem is that, because of my settings of the Virtual Screen, which is big enough to hold both monitors resolutions, there is an invisible area on top pf my Laptop screen (see screenshot: the red squares are the visible areas of each monitor, the blue square is the invisible area).

In my previous setup, using Xinerama with Ubuntu 7.10 and the open source drivers, the mouse would gracefully jump from the top of the external monitor to the top of the laptop monitor. It was even better than what happens in Vista, where the mouse gets stuck in the edge of the screen and you need to move it in a square-like movement to move it to the other monitor.

So, does anyone know what could be the solution for this?

1) A way of telling X that the monitors have different resolutions and the extra area should be ignored?
2) A way of telling Gnome that the extra area of the Virtual screen should be ignored?
3) Or simply telling the panel to hold the mouse and not let it go to the invisible area?

Thanks a lot!

---

### Post by howlingmadhowie on 2008-05-22
has anyone found a solution to this? a friend of mine has this problem too :(

---

### Post by manifoldronin on 2008-05-22
I'm researching for a new 24" lcd, so also interested in this topic.  Here are a few links I found:

[http://ubuntuforums.org/showthread.php?t=130002]("http://ubuntuforums.org/showthread.php?t=130002")
[http://lunapark6.com/dual-head-configuration-with-different-resolutions-per-screen-linux.html]("http://lunapark6.com/dual-head-configuration-with-different-resolutions-per-screen-linux.html")
[http://gentoo-wiki.com/HOWTO_Dual_Monitors]("http://gentoo-wiki.com/HOWTO_Dual_Monitors")

I haven't got the lcd yet, so I haven't tried anything suggested from above.  Please keep us updated as to how it goes for you guys. :)

---

### Post by michal6103 on 2010-04-16
Anythig new?

---

### Post by mkhamis on 2011-11-02
I've just had this problem, I opened the Display settings, chose a different resolution for the monitor in which the mouse doesn't appear, once I did that the mouse re-appeared.. You can then change the resolution back to the desired one

---

