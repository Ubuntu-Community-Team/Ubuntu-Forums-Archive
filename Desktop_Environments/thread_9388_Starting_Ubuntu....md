---
title: "Starting Ubuntu..."
date: 2004-12-28
forum: Desktop Environments
---

### Post by #Greg on 2004-12-28
On booting my pc, it loads the first things up, selects the kernal etc, then it gets to "Starting Ubuntu..." where afterwards is starts loading all the tmpfs and modules etc, but this only works about 1/4 of the time, most of the time it sticks on "Starting Ubuntu..." and will stand there dead until I keep rebooting and eventually it'll kick into action and boot.

I don't seem to be having errors with Ubuntu itself, nothing broken etc, though I do get this while doing an update:

Building Dependency Tree... Done
The following packages have been kept back:
  linux-image-2.6-386 linux-restricted-modules-2.6-386
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

It keeps back those packages instead of upgrading, but I don't think that's it..

This is on an AMD Athlon XP3000+, 512ddr, 64mb nvidia gfx card, 60gb hdd.
On previous installs of Ubuntu I've never had this problem.

Any help?

---

### Post by diebels on 2004-12-28
Try upgrading these packages spesifically, instead of a complete upgrade.

---

### Post by #Greg on 2005-01-01
I managed to update those packages, but still having the same boot-up problem.

Anyone have any ideas why it's happening?

---

