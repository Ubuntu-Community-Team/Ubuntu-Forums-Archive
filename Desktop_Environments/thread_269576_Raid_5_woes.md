---
title: "Raid 5 woes"
date: 2006-10-01
forum: Desktop Environments
---

### Post by crthomas on 2006-10-01
I am trying to build a raid 5 array on 4 sata hard drives.  I can build the array, and format and mount it, but as soon as I reboot the first time, it gives me an error about corrupt superblock.

The exact error:
"fsck.ext2: Invalid argument while trying to open /dev/md2
/dev/md2:
The superblock could not be read r does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, and you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>"

Doing e2fsck -b 8193 /dev/md2 just gives the same error as above.

---

### Post by brum76 on 2006-10-02
I assume your Raid partition does not hold "/" or "/usr"
In this case make sure raid is started before the device is fsck'ed.

---

### Post by crthomas on 2006-10-02
How?

---

