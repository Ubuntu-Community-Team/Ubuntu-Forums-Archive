---
title: "Booting Problem"
date: 2009-01-31
forum: General Help
---

### Post by Shady3D on 2009-01-31
hi all, i have a problem, i wanted to make a grub on it own partition so i created a PRIMARY partition and called it GRUB then next time i made a boot there is an error, so i am on live CD and trying to fix the problem without reinstalling ubuntu, so can any one help :(

---

### Post by mikewhatever on 2009-01-31
Post the output of <sudo fdisk -l> from the Terminal. That should get us started, but if you know how to access your grub partition, post also your menu.lst file contents.

---

### Post by Shady3D on 2009-01-31
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x36a236a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3054    24531223+   7  HPFS/NTFS
/dev/sda2            3055       17511   116125852+   5  Extended
/dev/sda5            5101       10322    41945683+   7  HPFS/NTFS
/dev/sda6           10323       15264    39696583+  83  Linux
/dev/sda7           15265       17249    15944481   83  Linux
/dev/sda8           17250       17511     2104483+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4f8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 8086 MB, 8086617600 bytes
255 heads, 63 sectors/track, 983 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d5a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         983     7895916    b  W95 FAT32


```

---

### Post by mikewhatever on 2009-01-31
Right, it looks like sda6 and sda7 are the root and boot partitions or vice versa. Let's find out.
sudo mkdir /media/part6
sudo mount /dev/sda6 /media/part6

The above should mount sda6, then post the output of the following:
ls /media/part6

---

