---
title: "removable device desktop icon not showing"
date: 2009-07-08
forum: Desktop Environments
---

### Post by sashaK on 2009-07-08
Hi,
I was trying to do a few things to stop my Toshiba Portege M300 Laptop running Ubuntu 9.04 from getting hot. While running a command line utility called powertop, hal-disable-polling --device /dev/cdrom option was in amongst other things the utililty suggested doing. That done, I realised that I wanted my system to automatically mount my removable media for me as well as have the removable device desktop icon back on which was disabled by running the 'hal-disable...' command.

I ran hal-disable-polling --enable-polling --device /dev/cdrom, which did enable my removable media to be automatically mounted. But alas, no desktop icon.

How do I bring it back?

Thanks.

---

### Post by Tamlynmac on 2009-07-08
applications/system/configuration editor/apps/nautilus/desktop

On the right side of the window, check the box (left click one time on empty box - a check mark should appear in the box) next to "volumes_visible".

This will permit icons linked to mounted volumes to be placed on desktop.

Hope this helps....

---

### Post by sashaK on 2009-07-09
Thanks. I'll give it a try. Will let you know how I go.

---

