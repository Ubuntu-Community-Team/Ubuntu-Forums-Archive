---
title: "mounting - what SHOULD the results look like?"
date: 2007-02-03
forum: Desktop Environments
---

### Post by johnbl on 2007-02-03
Mounting a device for me reults in multi mount points being displayed across the top  of the screen.
NB Insert CD, and multi versions of apparently the same information appear rather than what I would have presumed as correct, one.

Anyob able to comment on this being ' normal ' or is my set up some how incorrect?

John:confused:

---

### Post by gradedcheese on 2007-02-04
So, you're saying that if you insert a CD its icon shows up more than once?

What do you get if you insert the CD, open a terminal, and run 'mount'?  Does that show more than one mount point for the CD?

---

### Post by johnbl on 2007-03-22
> **gradedcheese said:**
> So, you're saying that if you insert a CD its icon shows up more than once?

What do you get if you insert the CD, open a terminal, and run 'mount'?  Does that show more than one mount point for the CD?

Thankyou for your response and sorry for the delay in getting to this. Been hectic here for months!

This is the result when a device is inserted.
> john@interserve~$ mount
/dev/mapper/Ubuntu-root on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-28-386/volatile type tmpfs (rw)
/dev/hda1 on /boot type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/usbdisk type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid =1000,gid=1000,umask=077,iocharset=utf8)
/dev/sda1 on /media/SANSA E250 type vfat (rw,nosuid,nodev,quiet,shortname=mixed, uid=1000,gid=1000,umask=077,iocharset=utf8)


I know there is a problem with line 9 of fstab, but can't see what. However, CD or SanDisk, same  multi icon display!


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/Ubuntu-root /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/mapper/Ubuntu-swap_1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/disk/by-id/usb-SanDisk_Sansa_e250_00000000-00000000-3524b389-501ceb10-00000000-part2
/media/Sansa_e250 vfat mask=000,uid=0,gid=0,noauto,rw,user 0 0

Any help would be most appreciated getting this minor irritation solved.

Johnbl

---

