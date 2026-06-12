---
title: "fstab error at start up."
date: 2009-11-07
forum: Desktop Environments
---

### Post by Stephen_at on 2009-11-07
I'm on Karmic and sometimes when I boot up when it gets to first displaying the white ubuntu "friends" logo a message pops up on the bottom of the screen about not being able to mount a partition that was specified in fstab.

The system continues to boot and everything is fine.

My fstab contains:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=f6686c01-070a-492f-ab51-832916434aad /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=73501418-188f-4398-9655-ba937542b74a /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=26ec1f1d-775f-4b3e-a7ad-cd0f55ab2283 none            swap    sw              0       0

```

And everything seems to be fine, and there is nothing recorded any any error log that I can see

Any ideas?

---

### Post by SuperSonic4 on 2009-11-07
Have you swapped around any disks recently? Also could you post the output of ```
sudo fdisk -l
```

---

### Post by Stephen_at on 2009-11-07
Not touched the disk at all. Just reformatted / as ext4 rather than ext3 and did a clean install of KK rather than upgrade from JJ.

Here's the output of the fdisk -l command:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x380e892c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19693   158182998+   7  HPFS/NTFS
/dev/sda2           35618       38914    26468352    c  W95 FAT32 (LBA)
/dev/sda3           19694       20301     4883760   82  Linux swap / Solaris
/dev/sda4           20302       35617   123025770    5  Extended
/dev/sda5           20302       23340    24410736   83  Linux
/dev/sda6           23341       35617    98614971   83  Linux

Partition table entries are not in disk order

```

---

### Post by Stephen_at on 2009-11-08
Its this error:

[http://ubuntuforums.org/showthread.php?t=1301766](http://ubuntuforums.org/showthread.php?t=1301766)

which seems to be "harmless".

---

