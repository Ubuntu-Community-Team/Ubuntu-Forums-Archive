---
title: "could this be a zero-length partition?"
date: 2009-03-23
forum: General Help
---

### Post by brallan on 2009-03-23
(EDIT: nothing seemed to work, not even badblocks. in the end i am having to simply ignore the drive.)

on my eeepc at a normal reboot, i got grub errors and after rebooting with a liveCD, discovered that my sda1 partition was corrupted.

attempting to fix with fsck doesn-t seem to do it:

```
root@ubuntu:/home/ubuntu# fsck.ext2 -f /dev/sda1
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

fdisk doesn't show anything out of the ordinary:

```
root@ubuntu:/home/ubuntu# fdisk -l /dev/sda

Disk /dev/sda: 4034 MB, 4034838528 bytes
255 heads, 63 sectors/track, 490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001d3cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         462     3710983+  83  Linux
/dev/sda2             463         490      224910    5  Extended
/dev/sda5             463         490      224878+  82  Linux swap / Solaris

```

Now i am regretting using the ext2 filesystem (It was recommended in order to extend drivelife). I can only guess that the superblock got corrupted, but i have no idea what to do about that.

can anyone help?

---

### Post by alanwalterthomas on 2009-07-04
I just got that zero-length partition message too. As far as I know the disk is irrecoverably bad. I'm sending it back to the manufacturer.

---

### Post by Gizenshya on 2009-07-04
is there anything there you want to save?

---

### Post by bab1 on 2009-07-04
Here are 2 good howto's on partiton recovery:

[**_http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html_**]("http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html")

[***http://www.cyberciti.biz/tips/mounting-with-an-alternative-superblock.html***]("http://www.cyberciti.biz/tips/mounting-with-an-alternative-superblock.html")

These came from this Ubuntu forum thread
[***http://ubuntuforums.org/showthread.php?t=1203483&page=3***]("http://ubuntuforums.org/showthread.php?t=1203483&page=3")

See the posts starting at #30

---

