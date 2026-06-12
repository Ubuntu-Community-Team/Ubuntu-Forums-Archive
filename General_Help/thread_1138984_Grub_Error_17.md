---
title: "Grub Error 17"
date: 2009-04-26
forum: General Help
---

### Post by jebam on 2009-04-26
This problem gives me (even more) grey hair...

After a failed upgrade from 8.10 (my fault), I made a fresh install of Ubuntu 9.04. After that, I've got the Grub Error 17 - and the system will not boot.

Here's details of my system (using Live CD to find the information):

device.map:
```
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
(hd4)    /dev/sde
```menu.lst:
```
title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        d03f3e7f-b2d1-4cdc-95be-5493c528dd0f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d03f3e7f-b2d1-4cdc-95be-5493c528dd0f ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        d03f3e7f-b2d1-4cdc-95be-5493c528dd0f
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=d03f3e7f-b2d1-4cdc-95be-5493c528dd0f ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        d03f3e7f-b2d1-4cdc-95be-5493c528dd0f
kernel        /boot/memtest86+.bin
quiet 


```fdisk -lu gives me this output:
```
Disk /dev/sda: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x658aefce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    39070079    19535008+  83  Linux
/dev/sda2        39070080   490223474   225576697+   5  Extended
/dev/sda5        39070143   490223474   225576666   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00021804

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   485243324   242621631   83  Linux
/dev/sdb2       485243325   976768064   245762370   83  Linux

Disk /dev/sdc: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00018292

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63  1465144064   732572001   83  Linux

Disk /dev/sdd: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22802280

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63   490223474   245111706   83  Linux

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000700df

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *          63     8385929     4192933+  82  Linux swap / Solaris
/dev/sde2         8385930   488392064   240003067+   5  Extended
/dev/sde5         8385993    16771859     4192933+  82  Linux swap / Solaris
/dev/sde6        16771923   488392064   235810071   83  Linux
```fstab:
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=d03f3e7f-b2d1-4cdc-95be-5493c528dd0f /               ext3    relatime,errors=remount-ro 0       1
# /disp1 was on /dev/sdd1 during installation
UUID=074da4e0-a437-4c95-8f82-c17f7023eafe /disp1          reiserfs relatime        0       2
# /film was on /dev/sdc1 during installation
UUID=b066480e-4db8-4345-9074-548223824635 /film           reiserfs relatime        0       2
# /home was on /dev/sdb1 during installation
UUID=e2337fe7-2db2-4925-a581-fe59822898de /home           ext4    relatime        0       2
# /disp2 was on /dev/sda5 during installation
UUID=44e09911-0637-467f-ace6-420985f416c6 /disp2        ext4    relatime        0       2
# /disp3 was on /dev/sdb2 during installation
UUID=22dc3ff2-b797-4670-9059-e38fdfc38ad0 /disp3        ext4    relatime        0       2
# /photos was on /dev/sde6 during installation
UUID=81d6c449-82b3-4b02-8e1e-ed23c27b655d /photos         ext3    relatime        0       2
# swap was on /dev/sde1 during installation
UUID=18df020e-c919-420b-b633-bff424a48998 none            swap    sw              0       0
# swap was on /dev/sde5 during installation
UUID=55f005e3-c283-485c-a9b2-7686714f6597 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

For me, this looks fine.... What am I missing here?

---

### Post by HeadGremlin on 2009-04-26
I have never posted before...

That error always comes up for me when I have some usb device attached to my computer when it boots.  Usually external hard drives or thumb drives.  Take it out and try to boot again.

---

### Post by jebam on 2009-04-26
> **HeadGremlin said:**
> I have never posted before...

That error always comes up for me when I have some usb device attached to my computer when it boots.  Usually external hard drives or thumb drives.  Take it out and try to boot again.

Thanks, but I have no USB devices attached.

---

### Post by jebam on 2009-04-27
Found the [Super Grub Disk]("http://www.supergrubdisk.org/"). This tool fixed it all :)

---

