---
title: "Xubuntu 10.10 Maverick Nvidia issue"
date: 2010-09-20
forum: Desktop Environments
---

### Post by Grendelmon on 2010-09-20
Hi All,

I realize that 10.10 is still beta so I'm not sure if it's appropriate to report issues in these forums; I'm still pretty new around here.

In any case, I installed Xubuntu (32bit) 10.10 beta on my PC and noticed an issue after I activated the Nvidia drivers. When I rebooted, for some reason my CPUs become completely pegged @ 100%. I first noticed this to verify that I had video acceleration but experienced menus/windows were laggy and sometimes unresponsive. The strange thing is that I cannot identify a specific process that indicates it's cpu utilization @ 100%. As far as 'top' is concerned, the system is mostly idle. However if I view the graphical chart in the gnome-system-monitor I can clearly see my CPUs going haywire.

Anyone else experience this? My hardware setup is:

ASUS P5N32-SLI motherboard
Core 2 Duo 6600 @ 2.43mhz
4GB DDR2 RAM
Dual Nvidia GeForce 9600GT's w/ SLI bridge

Thx. :confused:

---

### Post by Grendelmon on 2010-09-23
Okay, I narrowed it down. It only happens when I have xfce4-terminal running, with the xfce compositor.

---

