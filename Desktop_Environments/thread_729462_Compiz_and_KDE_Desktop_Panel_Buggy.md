---
title: "Compiz and KDE Desktop Panel Buggy?"
date: 2008-03-19
forum: Desktop Environments
---

### Post by MountainX on 2008-03-19
I have Kubuntu Gutsy set up with compiz. I'm using a desktop cube with 4 desktops.

Under Desktop Size in CCSM I have:
Horizontal Virtual Size = 4
Vertical Virt Size = 1
Number of Desktops = 1

Everything works. However, the area in the KDE taskbar that shows multiple desktops is flaky. It stops showing all 4 of my desktops. I have to open CCSM and edit the settings. Basically, I just change something, then put it back to Horizontal Virtual Size = 4, and my 4 desktops are immediately shown in the taskbar -- for a while.

Any ideas what this could be? Thanks

---

### Post by luisromangz on 2008-03-20
It is a problem of what KDE and Compiz understand as desktops. The number of virtual desktops is defined by the window manager, in this case compiz. But in compiz you have the "Number of Desktops = 1" so you really have just one virtual desktop. So KDE works like if there is just one desktop, because that's what really happens, even if that desktop has four times the screen's width.

---

### Post by MountainX on 2008-03-20
The problem does not exit under Ubuntu (GNOME), so I would hope there is a resolution under Kubuntu. Anyone have an idea? Thanks.

---

