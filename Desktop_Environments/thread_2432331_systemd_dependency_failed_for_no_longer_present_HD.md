---
title: "systemd dependency failed for no longer present HD"
date: 2019-11-30
forum: Desktop Environments
---

### Post by kdx7214 on 2019-11-30
My system had 4 hard drives and is used as a general storage device in the apartment.  One of these drives is being upgraded, so I unmounted the disk, removed the entry from fstab, and powered down.  I tried booting back up just to make sure things were working and now Ubuntu won't load.  The journalctl shows that systemd has a dependency fail for /storage/disk3, which is the mount point for the old HD.  I removed the entry from fstab so don't have the UUID and can't change it to nofail.   How do I get this machine going again?

Thanks!

---

