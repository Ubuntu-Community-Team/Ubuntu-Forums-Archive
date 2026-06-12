---
title: "Grub error 17 on 8.04 beta"
date: 2008-04-20
forum: Desktop Environments
---

### Post by GoliathWest on 2008-04-20
I installed 8.04 beta on a Dell laptop. Everything appeared OK until reboot. Now I am unable to get past the Grub screen as it returns Error 17.

I booted with a live CD and brought up a terminal- Here is my partition table:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2       299805030   312576704     6385837+   5  Extended
/dev/sda5       299805093   312576704     6385806   82  Linux swap / Solaris

Partition table entries are not in disk order
------------------------------------------------
I saw a few posts but none seem clear on how to overcome the booting issue. Should the boot be changed to the /dev/sda5 partition that has Linux? How do I set that up?

Thanks!

---

### Post by brownknight on 2008-04-20
I found this compilation of Grub 17 error solutions. Hope this helps.

[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

Just search for error 17 section.

---

### Post by dmakfan on 2008-04-28
Just thought I'd pipe in too that my machine was running fine (upgraded from 7.10 to 8.04 the other day).  I was doing an apt-get and my machine appeared to crash.  I did a ctrl-alt-backspace to try and restart gnome, and it hung, so I hit my power-off button to force ubuntu to shut down.  After it shutdown successfully, I turned the machine back on, and I got a grub 17 error.  Crap.

---

