---
title: "Karmic: netbook-launcher crashes"
date: 2009-11-30
forum: Desktop Environments
---

### Post by loneowais on 2009-11-30
I wanted to try out the Ubuntu Netbook Remix UI so desperately but looks like I'll have to wait.

I installed the Netbook-Remix meta package from synaptic. All the dependencies got installed. I switched off compiz and arranged my panel as required.

The only problem is that netbook-launcher wont start.
Here is the output

owais@Linbook:~$ netbook-launcher
(netbook-launcher:3836): libnetbook-launcher-DEBUG: CONFIG: Low graphics mode: False
(netbook-launcher:3836): libnetbook-launcher-DEBUG: CONFIG: Font dpi: 96.000000
(netbook-launcher:3836): libnetbook-launcher-DEBUG: CONFIG: Font changed: Droid Sans 9

> (netbook-launcher:3836): libnetbook-launcher-DEBUG: CONFIG: Connecting to ConsoleKit for suspend/resume restarting
(netbook-launcher:3836): liblauncher-DEBUG: launcher-menu.c:361
ORPHAN: Ubuntu Software Center
(netbook-launcher:3836): liblauncher-DEBUG: Workarea: (0, 21) (0, 0)
do_wait: drmWaitVBlank returned -1, IRQs don't seem to be working correctly.
Try adjusting the vblank_mode configuration parameter.
Segmentation fault


---

### Post by gwinston99 on 2009-12-31
I have the exact same problem, with the exact same output.  Help!!

Gregg

---

### Post by akaihola on 2010-01-02
This issue exists also in current builds of Lucid (Ubuntu 10.04) Netbook, and is tracked in Lauchpad as [bug #495066]("https://bugs.launchpad.net/ubuntu/+source/netbook-launcher/+bug/495066").

---

### Post by mexlinux on 2010-01-19
Any solution?

---

