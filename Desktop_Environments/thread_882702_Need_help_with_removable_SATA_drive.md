---
title: "Need help with removable SATA drive"
date: 2008-08-07
forum: Desktop Environments
---

### Post by raymond3 on 2008-08-07
I'm running 8.04 in a desktop environment and have 3 Sata drives and 1 IDE drive.  Everything was great until I installed a tray that allows me to slide in/out a SATA drive.

When I installed a new drive in the tray, Ubuntu reordered the drives and though / was on the newly inserted drive.  When I inserted the drive while Ubuntu was already loaded, it wouldn't see it at all. fdisk -l didn't show it.

I removed all of the drives except / /home and swap from fstab, then fdisk -l saw all the drives but had them all renumbered (i.e. the old SDA1 was now SDD1, etc.)

I went ahead and reworked fstab to the new drive numbers but when I removed the removable drive, everything was renumbered again and fstab was now wrong and I couldn't boot.

Is there a way to fix this?

Also, now that fstab is messed up and I can't boot, how can I edit fstab using the live CD?

Thanks for any help!

Ray

---

### Post by mcduck on 2008-08-07
The solution is to use UUID's (or partition labels) in your fstab instead of the device names. UUID will allow Ubuntu to recognize the partitions correctly regardless of what device name they get assigned to.

You can use the 'blkid" command to list UUIDs for all your partitions.

---

