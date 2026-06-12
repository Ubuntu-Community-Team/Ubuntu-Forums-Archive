---
title: "can't mount usb drive?"
date: 2009-05-19
forum: General Help
---

### Post by Shadowfaux on 2009-05-19
Hey,
Everytime I try and open a usb drive it says that it can't be mounted, I've tried different usb drives and it gives me the same thing each time.

My results from sudo fdisk -l are:
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cc594

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee3cee3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdc: 131 MB, 131596288 bytes
8 heads, 32 sectors/track, 1004 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x0d0c0b0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1004      128496    6  FAT16

```

The device I'm wanting to access is /dev/sdc1, can anyone see why I can't access the drive?

---

### Post by taurus on 2009-05-19
```
sudo mkdir /media/sdc1
sudo mount -t vfat /dev/sdc1 /media/sdc1 -o umask=000
```

---

### Post by Shadowfaux on 2009-05-19
Thank you! Can I ask you to explain what I did wrong?

---

