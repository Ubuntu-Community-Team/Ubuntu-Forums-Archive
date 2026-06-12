---
title: "Cannot login normally after removing misbehaving compiz"
date: 2007-08-08
forum: Desktop Environments
---

### Post by grupotux on 2007-08-08
I removed compiz by way of apt-get as it appears to cause gdm to misbehave. Now I cannot
login normally. The initial rotating cursor goes on and on without giving way to the login page. Can anyone help?

Update: After considerable effort, I managed to raise KDE (I always install it as a backup). It now appears that I have
no available swap space. My current ftab  listing follows:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=353c4258-d1cd-464b-9511-0ffe1020b321 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda4
UUID=77c0ccba-624d-4fdf-9bb7-65816607d944 /home           ext3    defaults        0       2
# /dev/sda2
UUID=0b3b204c-eb10-4bfd-a651-0af072b4baff /usr/local      ext3    defaults        0       2
[B]# /dev/sda3
UUID=3c1781c7-7bf9-4d4e-92a0-6146946daf21 none            swap    sw              0       0[/B]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

The line next to last (bold) refers to the swap partition, yet the functionality is gone. The machine (an older Toshiba Satellite) slows down with firefox running and several open tabs. Gkrellm reports huge disk activity during every freeze or near-freeze. It also reports zero available swap space. Rebooting changes nothing. What is going on?

---

