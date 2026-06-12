---
title: "Can't mount ntfs partitions with nautilus"
date: 2010-06-25
forum: Desktop Environments
---

### Post by kirbyboy on 2010-06-25
Hi, after searching the web i could not find the right solution, here is my problem:
I used the famous script for ubuntu 10.04 after installing ubuntu to make ntfs partitions automount when the computer is booted, and works(i think it only writes in fstab).  The problem is if i unmount throught nautilus a partition, i can't mount it, it prompts the next message:
"Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://ntfs-3g.org/support.html#unprivileged"
but i can mount them if i do a "gksudo nautilus", what can i do so any user can mount the drives?
I tried to change permissions to /media/sdaX but it did not work either, and looks like fstab has some problems with privileges(that's what i heard from the web).  Tried ntfs-config and MountManager, no results, i think it is because all those tools change fstab directly.

---

