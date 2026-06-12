---
title: "mount point query"
date: 2009-05-31
forum: General Help
---

### Post by lucifuge on 2009-05-31
How do edit the fstab file _and_ associated Linux commands to change the mount point of 
 /mydata (was on /dev/sdb1)  to

/home/brett/mydata (which currently does not exist...but /home is on sda3)

--------------------------------------------------------------------------------------
Here is the copy of my **fstab**  file


[FONT=Courier New][SIZE=1]# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=dc6624c0-0e16-40d5-8ff6-99a8b0306831 /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=901297f6-d55f-4637-8056-0f062cdbf8be /home           ext3    relatime        0       2
# /mydata was on /dev/sdb1 during installation
UUID=72c19fa6-df56-4345-b454-ea1d7e546dd1 /mydata         ext3    relatime        0       2
# swap was on /dev/sda2 during installation
UUID=0254673c-bf14-4ecc-aad8-f28bdbf82a1a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/SIZE][/FONT]

---

