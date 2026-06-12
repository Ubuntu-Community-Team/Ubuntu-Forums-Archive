---
title: "Xubuntu boot problem (kernel panic)"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Cable on 2006-08-16
I installed Xubuntu on an older computer yesterday, and had it working perfectly fine.  I shut it down last night when I went to bed.  My brother turned it on today, and right after the "uncompressing kernel" part, it paused, then showed a crc error, and said something along the lines of "Kernel panic- VFS:  Unable to mount root fs on unknown block (0,0)."

Nothing has been done to the computer between the time I turned it off last night and my brother turning it on today.  Can I fix this somehow??  Please help!

---

### Post by goatflyer on 2006-08-17
Sounds like the drive may be flaky.

Try booting with the live cd, open up a terminal, and run

```

sudo fdisk -l /dev/hda

```

See if your partitions look reasonable, then (assuming /dev/hda2 is your ubuntu partition)

```

sudo fsck /dev/hda2

```

---

### Post by Cable on 2006-08-17
What you said to do seemed to work fine.  The only thing I noticed that may be weird is that when I ran the first command you suggested, the last thing it said was "Partition table entries are not in disk order."  I know what that means, I just don't know if it's bad for it to be that way or not.   Here is the terminal output from both commands.
```

ubuntu@ubuntu:~$ sudo fdisk -l /dev/hda

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1            2222        2482     2096482+  82  Linux swap / Solaris
/dev/hda2               1        2221    17840151   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$ sudo fsck /dev/hda2
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/dev/hda2: clean, 94920/2231456 files, 825106/4460037 blocks

```

---

