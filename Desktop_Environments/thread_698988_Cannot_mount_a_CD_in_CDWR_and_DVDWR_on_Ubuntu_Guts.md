---
title: "Cannot mount a CD in CDWR and DVDWR on Ubuntu Gutsy 7.10"
date: 2008-02-16
forum: Desktop Environments
---

### Post by dphan on 2008-02-16
Hi Ubunu Fella,
I cannot mount CDs in a CDWR/DVDWR on Ubuntu Gutsy7.10 after a minor update routinely:

My Linux Box installed Gutsy from scratch, everything works fine, even CDs automount in two CD drives (CDWR and DVDWR). CDs automount work like a charm b4 update
I touched nothing in fstab or mtab as well as any /dev/scd*, the problem happened (I reckon) after a update kernel from 2.6.22-14.11 to 2.6.22.14.25. It is a routinely update set by Update Manager.
Please give me a hint to solve this issue out. the following is my fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=ad25fc49-c371-4595-8dc0-db3c0396833d /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=0f310812-3844-49cd-b206-1cfb61695ff6 /boot           ext3    defaults        0       2
# /dev/sdc5
UUID=946009f3-0e59-44a1-9d47-66869cc5a9b7 /home           ext3    defaults        0       2
# /dev/sdb1
UUID=82b82982-12c4-464c-af0c-a6205b33743a /media/sdb1     ext3    defaults        0       2
# /dev/sdb2
UUID=2dd48225-a941-4715-8be7-b519b93394a3 /media/sdb2     ext3    defaults        0       2
# /dev/sdc1
UUID=39bd272a-c203-43ae-b8e8-ad05cc199df6 /media/sdc1     ext3    defaults        0       2
# /dev/sda4
UUID=a25c252a-4bda-475b-b187-666b88057517 /opt            ext3    defaults        0       2
# /dev/sda3
UUID=14f515a8-dcbe-4286-a74d-c4f3b1d6189c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0

---

### Post by dphan on 2008-02-18
I come back,
Is that look like a bug with Gutsy which I have read from Ubuntu launchpad?
I tried to edit fstab with no success at all. Please any guys who got any ideas, just help me to find a wayout of this issue
thanks
James

Notes: If I log out of Gnome and/or restart Gutsy with a CD in drive, then it is auto-mount and on Desktop, I can see that CD title mounted and be ready for use/

---

