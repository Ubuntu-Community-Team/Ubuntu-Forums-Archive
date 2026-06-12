---
title: "Partition as part of RAID - failed?"
date: 2009-04-16
forum: General Help
---

### Post by BrightEyesDavid on 2009-04-16
Hello all,

I'm after some guidance on software RAID, please. The computer I use for my test web server and data storage is running 7.04 Feisty Fawn, and has the following configuration:

/dev/sda1 500MB /boot
/dev/sdb1 500MB /boot
/dev/sdc1 500MB swap
/dev/sdd1 500MB swap
/dev/sda2 500GB /
/dev/sdb2 500GB /
/dev/sdc2 500GB /
/dev/sdd2 500GB /

Here is me checking status:

```
~$ cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4]

     md1 : active raid5 sda2[0] sdd2[3] sdc2[2] sdb2[1]
     1463681856 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]

     md0 : active raid1 sdb1[1]
     489856 blocks [2/1] [_U]

     unused devices: <none>
```As I understand it, the underscore in md0 signifies a failure of one of the two partitions - sda1? - used for /boot which is RAID1. However, the four partitions in use for the rest of the filesystem which is RADI5 - including sda2 - are seemingly okay.

Could someone who is familiar with RAID clarify my understanding and suggest what the next step is please? Thanks.

---

### Post by BrightEyesDavid on 2009-04-17
I'm planning to [wipe the lot and start again]("http://ubuntuforums.org/showthread.php?t=1127352"), but any advice or pointers on what to do in this situation would still be welcome. :)

---

