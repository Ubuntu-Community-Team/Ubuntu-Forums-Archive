---
title: "fsck help, removed hard drive"
date: 2005-10-18
forum: Desktop Environments
---

### Post by mcpish on 2005-10-18
I just removed an old extra hard drive from my system and now I'm getting a message on bootup:

> 
e2fsck 1.38 (30-Jun-2005)
fsck.ext3: No such file or directory while trying to open /dev/hdb1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

I have to hit Control-D always to keep the bootup going, how can I fix this so that Ubuntu is no longer searching for the missing 2nd hard drive?  There is no longer a mount-point for it but is there something else I have to do?

---

### Post by metoo on 2005-10-18
Is there still an entry in /etc/fstab telling to auto mount hdb1?

If so, delete the line or set an '#' in front of it.

---

### Post by mcpish on 2005-10-18
that worked thanx :)

---

