---
title: "have fstab unusual listing"
date: 2005-12-23
forum: General Help
---

### Post by vk5hsx on 2005-12-23
Greetings,
                I am not a linux newbie and am aware of what the fstab does and the configuration of it..  Anyway, what I am curious is I went to organise making a partition for my Windows XP system, where I looked at the fstab file (shown below) for the first time since install..  I have two (2) drives ide0 20GB WinXP & ide1 40GB with linux system on. The usual install has /dev/hda1 winxp and /dev/hdb1 /, /dev/hdb3 /home, /dev/hdb2 swap

Now for some reason with ubuntu install, they ended up with..

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd3       /home           reiserfs defaults        0       2
/dev/hdd2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Any ideas.? I have installed ubuntu previously, which resulted in the proper setup, however, this more recent installed ended up like this..

regards,
Stef

---

### Post by BathroomNinja on 2005-12-23
Looks like you have the HD setup as a slave instead of Master on IDE1 (or possibly IDE2).  Drives are setup in odd places on the cables.

---

