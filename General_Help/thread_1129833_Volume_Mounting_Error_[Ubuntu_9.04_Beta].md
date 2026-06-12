---
title: "Volume Mounting Error [Ubuntu 9.04 Beta]"
date: 2009-04-19
forum: General Help
---

### Post by iFargle on 2009-04-19
A little background on this..

First off, I had no clue what I was doing this for, but I right clicked on the icon on the desktop, went down to properties, over to volume, and down to settings, and I entered text for "Mount Point", "File System" and "Mount Options"

It says "Changes in settings will not take effect until the volume is remounted", so I unmounted the volume (according to my /media/ file, I have four items mounted: cdrom, cdrom0, disk (which is mounted as "23.6Gb media), and FreeAgent Drive (Which is mounted as FreeAgent Drive).)  My main drive is a 1.5Tb Seagate and that's the one I'm having trouble mounting.  

When I double click, right click -> Mount from either Computer:/// in the File Browser or from the "Places" in the side bar I get an error that says

> Cannot mount volume.
Error org.freedesktop.Hal.Device.UnknownError.

Details
libhal.c 1399 : wrong reply from hald.  Expecting an array.org.freedesktop.Hal.Device.Volume.InvalidMountOption

Any help on this would be greatly appreciated.  This is my main hard drive, and all of my music is stored on it :(

FYI:  I have three HDD's plugged in to this:  one main 1.5Tb Seagate, one 160Gb backup (for Windows) and an external 250Gb Drive (FreeAgent)

A screen shot of the error message is supplied.

EDIT:  Also, here's my "sudo fdisk -l"

> Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x176b9f35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      179346  1440595721    7  HPFS/NTFS
/dev/sda2          179347      182401    24539287+   5  Extended
/dev/sda5          179534      182401    23037178+  83  Linux
/dev/sda6          179347      179533     1502014+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00007a0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19458   156288000    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS


Hope that helps

---

### Post by Vadi on 2009-04-19
What does *cat /etc/fstab* say? (or open /etc/fstab in the text editor and copy/paste contents)

---

### Post by iFargle on 2009-04-19
/etc/fstab:

> a# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro,relatime 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0


---

### Post by Vadi on 2009-04-19
Here is mine from a non-modified 9.04 install. backup yours and try replacing it with this:

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=3a495a10-0c33-4b6d-b898-528f718f6c8c /               ext3    relatime,errors=remount-ro 0       1
# none was on /dev/sda5 during installation
UUID=59475734-f659-428b-89b7-b8181ae082c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

use alt+f1 and "gksudo gedit /etc/fstab" to edit your file.

---

### Post by Vadi on 2009-04-19
Oh, slight problem, you'll need to find your own UUIDs for your drives. not sure how to do that, but google should help

---

### Post by iFargle on 2009-04-20
> **Vadi said:**
> Oh, slight problem, you'll need to find your own UUIDs for your drives. not sure how to do that, but google should help

Ah, well it turns out I messed this installation up more than I thought.  It wouldn't boot into Ubuntu after I switched them, so I booted into Windows Vista and I had 2 (?) installations of Ubuntu, one on the C: Drive 1500GB) and one on the G: Drive (160GB).  So I'm going to try and reinstall later.

---

### Post by jfp11 on 2009-04-25
Same problem here...
Solved installing "mountpy" from Synaptic

Just install and then run ...

---

