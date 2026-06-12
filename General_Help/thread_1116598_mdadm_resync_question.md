---
title: "mdadm resync question"
date: 2009-04-05
forum: General Help
---

### Post by Wonslung on 2009-04-05
i'm just currious....what would cause mdadm to resync?
i didn't add any new drives and a cat /proc/mdstat shows that all drives are good

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[5](S) sda1[0] sdf1[4] sde1[3] sdd1[2] sdb1[1]
      3907039744 blocks level 5, 128k chunk, algorithm 2 [5/5] [UUUUU]
      [=======>.............]  check = 38.9% (380444160/976759936) finish=150.3min speed=66120K/sec

---

### Post by garcher42 on 2009-10-04
Hi,

The same thing just happened to me. :(
This thread might be worth a bump to try again.

Is there any way to find out what caused a resync?

Thanks,
Geoff

---

### Post by Mihai Cilidariu on 2011-03-05
mdadm arrays are checked every month at 00:57 on the first Sunday.

This is scheduled from this file:
/etc/cron.d/mdadm

---

