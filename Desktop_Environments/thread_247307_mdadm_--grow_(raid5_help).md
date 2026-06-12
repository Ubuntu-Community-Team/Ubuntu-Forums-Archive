---
title: "mdadm --grow (raid5 help)"
date: 2006-08-30
forum: Desktop Environments
---

### Post by paca on 2006-08-30
I have made a working test raid5 array of 3 disks, added a spare disk to it.
in /proc/mdstat it looks like this:

**cat /proc/mdstat**

Personalities : [raid5]
md0 : active raid5 loop4[3](S) loop3[2] loop2[1] loop1[0]
      20352 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

Then i try to grow it (mdadm - v1.12.0 - 14 June 2005):

**mdadm --grow /dev/md0 --raid-disks=4**
mdadm: Cannot set device size/shape for /dev/md0: Invalid argument

and with newest mdadm (mdadm - v2.5.3 -  7 August 2006):

**mdadm --grow /dev/md0 --raid-disks=4**
mdadm: Need to backup 384K of critical section..
mdadm: /dev/md0: Cannot get array details from sysfs

maybe it doesnt work with loop devices (just using it for testing)?
or am I doing something wrong?

---

### Post by paca on 2006-08-30
I think I found it... u need kernel 2.6.17 and newer mdadm then 2.3.1
Thanks anyway :)
/Patrik

---

