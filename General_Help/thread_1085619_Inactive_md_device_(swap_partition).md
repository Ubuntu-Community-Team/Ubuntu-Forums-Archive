---
title: "Inactive md device (swap partition)"
date: 2009-03-03
forum: General Help
---

### Post by gwielen on 2009-03-03
First of some basics of my system. I run Ubuntu 8.04.2 on a Shuttle K45 with a E6600, 2x 1 GB memory and 2x 750 GB in a software RAID 1 setup.

The disks are partitioned like this:
> 
/dev/md0    /boot       197.41
/dev/md1    /swap       3997.49
/dev/md2    /           50001.48
/dev/md3    /home       50001.48
/dev/md4    /data       645955.92


Last Thursday I started receiving the following in my mail:

> This is an automatically generated mail message from mdadm
running on rigel

A Fail event had been detected on md device /dev/md4.

It could be related to component device /dev/sda7.

Faithfully yours, etc.

P.S. The /proc/mdstat file currently contains the following:

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md4 : active raid1 sda7[0](F) sdb7[1]
      630816192 blocks [2/1] [_U]
      
md3 : active raid1 sda6[0] sdb6[1]
      48829440 blocks [2/2] [UU]
      
md2 : active raid1 sda5[2](F) sdb5[1]
      48829440 blocks [2/1] [_U]
      
md1 : active raid1 sda2[0] sdb2[1]
      3903680 blocks [2/2] [UU]
      
md0 : active raid1 sda1[0] sdb1[1]
      192640 blocks [2/2] [UU]
      
unused devices: <none>

After this e-mail I got some other for the md device 0 through 3. I found out one of my disks was failing (/dev/sda to be exact) and started to remove it from my software raid with the remove commando. Replaced the disk, partitioned it the same as /dev/sdb (cfdisk) and was able to restore all my md device but one.

> 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md4 : active raid1 sda7[0] sdb4[1]
      630816192 blocks [2/2] [UU]

md3 : active raid1 sda6[0] sdb6[1]
      48829440 blocks [2/2] [UU]

md2 : active raid1 sda5[0] sdb5[1]
      48829440 blocks [2/2] [UU]

md1 : inactive sda2[0](S)
      3903680 blocks

md0 : active raid1 sda1[0] sdb1[1]
      192640 blocks [2/2] [UU]

unused devices: <none>


md1 is my swap partition/device as you can see but I'm unable to add to it.

> root@rigel:~# mdadm /dev/md1 -a /dev/sdb2
mdadm: cannot get array info for /dev/md1
root@rigel:~# mdadm --detail /dev/md1
mdadm: md device /dev/md1 does not appear to be active.

Does anybody have an idea how to fix this? Cause at the moment I don't have any swap it seems:

> root@rigel:~# free
             total       used       free     shared    buffers     cached
Mem:       2053288    2035960      17328          0       4664    1595532
-/+ buffers/cache:     435764    1617524
Swap:            0          0          0

---

### Post by alkk on 2009-05-20
Looks like md1 is not running, try to force it by executing ```
mdadm -R /dev/md1
```

---

### Post by gwielen on 2009-05-20
> **alkk said:**
> Looks like md1 is not running, try to force it by executing ```
mdadm -R /dev/md1
```

Thx for the reply. Replaced the entire disk a few weeks back ;)

---

