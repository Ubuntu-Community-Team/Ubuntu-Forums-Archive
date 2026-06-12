---
title: "Need to Re-Install X11"
date: 2009-05-09
forum: General Help
---

### Post by jbeiter on 2009-05-09
I tried to "turn on glx" and to make a long story of a painful 7 hours short, X11 is FUBAR. Nothing works except for a fugly 800x600 failsafe.

I have a acer lcd al2016w monitor and Nvidia fx 5700 adapater.

Can someone please guide me thorough purging my system of a mix of the latest nvidia.run drivers, some concoction of too many ubuntu repository drivers, and get this stuff back on track?

I'm going in circles and there seems to be 80 million wrong ways to install X11 for Nvidia on ubuntu.

I really don't want to do it but my only recourse at this point is to wipe everything and try to install Jaunty in hopes it will come out right, which I highly doubt from past experiences with Nvidia and glx.

---

### Post by jbeiter on 2009-05-09
I gave envy a shot, installed "envyng" via synaptics and then ran envyng -g from a terminal and let it do its thing.

To my relief, everything came backup with good resolutions and glx appears to work, but the X server is dying at seemingly random times.

----------------xorg.0.log.old
Backtrace:
0: /usr/bin/X(xf86SigHandler+0x7e) [0x80c780e]
1: [0xb7fa7420]
2: /usr/lib/libpixman-1.so.0(pixman_region_subtract+0xb2) [0xb7efabb2]
3: /usr/bin/X(miSubtract+0x2b) [0x812cfcb]
4: /usr/bin/X [0x8131384]
5: /usr/bin/X(miValidateTree+0x250) [0x8131b00]
6: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0xb6b7a843]

Fatal server error:
Caught signal 11.  Server aborting
-------------------------snip

No clue what this means..

---

### Post by KhurramM on 2009-05-09
If u r on 8.04+ flavour of ub.s, then try to go into auto recovery mode, try to recover the display/X.

Hope this works.

As usual, the drill, BACKUP data first in case.

Adios.

---

