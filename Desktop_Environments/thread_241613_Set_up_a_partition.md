---
title: "Set up a partition"
date: 2006-08-22
forum: Desktop Environments
---

### Post by jazzman14 on 2006-08-22
I currently am running ubuntu on a 100GB hard drive, Ubuntu is all that is installed on that hard drive, how can i create a partition in ubuntu to lets say split the hard drive in half, so on the other half I can install windows? Thanks.

---

### Post by fermulator on 2006-08-22
Ahoy;

I would suggest using Gparted.

Shrinking a partition can only be done while it's unmounted, so you won't be able to do it from within ubuntu.

Go get Gparted Live CD!
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)

Burn the ISO to CD, and boot 'er up.
From there you should be able to intuitively use it to shrink your parition.

Once that has been applied, ensure your ubuntu still works. :-)

Boot off your Windows installation CD and begin the setup!  It should detect the 'unallocated free space' now, and you should be able to install.

---

