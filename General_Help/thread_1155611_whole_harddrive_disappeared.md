---
title: "whole harddrive disappeared"
date: 2009-05-11
forum: General Help
---

### Post by hypermaniac on 2009-05-11
hi recently my couldn't boot into their computer. first it gave a grub error 17, then after using supergrub it shows grub error 21. booting into live cd i checked gparted and it shows the whole disk is unallocated. the output for sudo fdisk -l is this

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       30076       30401     2618563+   c  W95 FAT32 (LBA)
/dev/sda2           29650       30401     6040440    5  Extended
/dev/sda5           29650       30401     6040408+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         123      987104    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(121, 254, 63) logical=(122, 227, 40)

Disk /dev/sdc: 1010 MB, 1010826752 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1          38      305203+   b  W95 FAT32
/dev/sdc2              39         122      674730    b  W95 FAT32

can anyone help and tell me what happened to my friends computer?

---

### Post by hypermaniac on 2009-05-11
is the hard drive just damaged? do i have to reinstall ubuntu because there are files on the computer that needs to be saved. is there anyway to save the file?

---

### Post by gamblor01 on 2009-05-11
Sounds like the hard drive might just be damaged.  :(

Which partition are you having problems with specifically?  You might be able to boot up with the live CD and mount the partition manually.  Even if drives cannot boot they can sometimes still be mounted and you can at least copy the files off that way.

---

### Post by geraldvillorente on 2009-05-11
you can recover your files by booting into Livecd...

Read this thread before you reformat your friend PC...it might help you
[http://ubuntuforums.org/showthread.php?p=7261638#post7261638](http://ubuntuforums.org/showthread.php?p=7261638#post7261638)

---

### Post by hypermaniac on 2009-05-17
thank guys, i finally fixed it. just booted up with live cd, used test disk to find the partition. after that i edited grub with geraldvillorente's link and it worked! 

but she also said some of her files were lost. does this mean her harddrive is dying? i'm remember reading signs of hard drive failure having these symtoms.

---

