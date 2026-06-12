---
title: "New drive halting bootup."
date: 2009-03-19
forum: General Help
---

### Post by ac7ss on 2009-03-19
Yes, I have searched for this...

I just installed a second BIG drive in my machine. (/dev/sda1)

```
$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2610995e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8a066e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00064282

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9566    76838863+  83  Linux
/dev/sdc2            9567        9729     1309297+   5  Extended
/dev/sdc5            9567        9729     1309266   82  Linux swap / Solaris

```
When it boots I am getting:
```
$ cat checkfs
Log of fsck -C3 -R -A -a 
Thu Mar 19 18:29:01 2009

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Not a directory while trying to open /dev/sda1/
/dev/sda1/: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sdb1: clean, 174555/61054976 files, 63518994/244190000 blocks
fsck died with exit status 8

Thu Mar 19 18:29:02 2009
----------------

```
After I CTRL-D out of the root prompt I do this:
```
$ sudo fsck /dev/sda1
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
/dev/sda1: clean, 349/61054976 files, 120007800/244190000 blocks

```
This drive is a dedicated backup drive and is not supposed to mount at boot. It's entry in /etc/fstab is:
```
/dev/sda1/	/backup	ext3	noauto,defaults,errors=remount-ro	0	1

```
It mounts fine. It is holding the backups fine (using backup2l). But it halts the boot sequence.

HELP!!!

---

### Post by fieroboom on 2009-03-19
Try setting the third column in the fstab entry to auto instead of ext3:
```
/dev/sda1/	/backup	auto	noauto,defaults,errors=remount-ro	0	1

```

Do the reboot dance and see what happens...
:D
-Paul

---

### Post by ac7ss on 2009-03-19
That did it!!! thank you!!! 
:D :D :D :D :D :D :D

Now how do I mark the thread as solved?

---

### Post by fieroboom on 2009-03-19
> **ac7ss said:**
> That did it!!! thank you!!! 
:D :D :D :D :D :D :D

Now how do I mark the thread as solved?

I'm still kind of a new forum member, but from what I've read in other threads, a forum update killed that feature...
In any case, I'm glad I could help!
:D
-Paul

---

