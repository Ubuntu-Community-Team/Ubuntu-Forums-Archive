---
title: "dual boot Opensuse 11.0 with Xubuntu 8.10 already installed"
date: 2008-12-06
forum: General Help
---

### Post by esmurdo on 2008-12-06
How can I do this? I currently have Xubuntu 8.10 installed with the following /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=a41e12b5-6781-4e91-9a1c-fdcb12624073 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=ae39bd82-38d9-4a55-86d1-36cdc86fe16b /boot           ext3    relatime        0       2
# /dev/sda4
UUID=5b9f4a32-216b-4466-9699-9176bcc8995a /home           ext3    relatime        0       2
# /dev/sda1
UUID=7fe4f2d7-42b1-41db-93a1-a49cc1215290 none            swap    sw              0       0

```

I have about 15 GB free space before sda4 to put a possible /, /boot and swap, but I don't know the next steps.

HELP!!!!!!!!!!!!!!!

---

### Post by TeXtonyx on 2008-12-06
I thought you could do an automatic install to the unallocated
space. They can share the same swap partition. If you want to 
keep your current grub bootloader then install Opensuse's grub 
to the /boot partition. Then you will have to update Xubuntu's
menu.lst. I would just copy over OpenSuse menu.lst section over
to the Xubuntu menu.lst and paste it below the Xubuntu entry.
I haven't used Xubuntu just Ubuntu.

---

### Post by caljohnsmith on 2008-12-07
Based on your fstab, it looks like you might all ready have 4 primary partitions which is the maximum limit. If you want to install OpenSUSE, you'll need to convert one of those partitions to an "extended" partition, and then within that extended partition you can create as many logical partitions as you want. But you may be limited by the physical layout of your partitions, which we don't know yet, so how about opening a terminal (Applications > Accessories > Terminal) and please post:
```
sudo fdisk -lu
```
And we can work from there if you want. :)

---

### Post by esmurdo on 2008-12-07
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeafb050c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     2008124     1004031   82  Linux swap / Solaris
/dev/sda2         2008125    32017544    15004710   83  Linux
/dev/sda3   *    32017545    32403104      192780   83  Linux
/dev/sda4        88389630   488392064   200001217+  83  Linux
```



What's the differences between extended, primary, and logical partitions?

---

### Post by caljohnsmith on 2008-12-07
> **esmurdo said:**
> 
What's the differences between extended, primary, and logical partitions?
Basically it works like this: you can up to four primary partitions on your HDD, or you can have three primary partitions and one extended partition. Inside that extended partition you can create about as many logical partitions as you want to. In other words, the extended partition is merely a "container" for all the logical partitions. But the actual partitions that have your data are the primary and logical partitions. 

If I were in your shoes, would convert the sda4 partition into a logical partition that is inside of an extended partition, and then you can resize it so that you make room for your OpenSUSE install. Or if you don't want to go through that trouble, you could move your sda4 /home files somewhere temporarily, delete sda4, and then create an extended partition which could have your new /home logical partition and also partitions for OpenSUSE. Whichever you decide to do, it would be a good idea to back up your data in sda4 if you can. Let me know what you want to do.

---

