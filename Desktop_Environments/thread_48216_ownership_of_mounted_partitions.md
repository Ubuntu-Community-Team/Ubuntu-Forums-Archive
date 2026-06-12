---
title: "ownership of mounted partitions"
date: 2005-07-11
forum: Desktop Environments
---

### Post by wuselbox on 2005-07-11
Hi,
i try to mount another partition on bootup by /etc/fstab.
The problem is, that only root can create and manipulate files on that partition, what i want to is, that every user on my machine is able to do that.
From other linux-dists i was used to change the group and owner of the mounting point and edit the fstab. This seems not to work in ubuntu hoary. 
But maybe there is a trick how it works with it, so i will send you my config files right here (the problem exists on device hda5):
[FONT=Courier New]
[COLOR=RoyalBlue]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /daten          vfat    auto,user,exec        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0[/COLOR][/FONT]

The directory ownership is:

[FONT=Courier New][COLOR=RoyalBlue]drwxr-xr-x    2 root root 16384 1970-01-01 01:00 daten[/COLOR][/FONT]

When I try to change ownership or modes the following error occurs:

[FONT=Courier New][COLOR=RoyalBlue]root@dido:/ # sudo chgrp users /daten/
chgrp: changing group of `/daten/': Die Operation ist nicht erlaubt (Operation not permitted)[/COLOR][/FONT]

So what to do?

Thank you for help!

---

### Post by alastair on 2005-07-11
I think FAT/VFAT is a little different. Try using the fstab file to set user/group i.e.

uid=<value>
gid=<value>

in the fstab options. See "man mount".

---

