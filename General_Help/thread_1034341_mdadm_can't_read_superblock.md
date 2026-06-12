---
title: "mdadm can't read superblock"
date: 2009-01-08
forum: General Help
---

### Post by kreyszig on 2009-01-08
Hi, 

I'm posting after much googling and have yet to find a fix for my particular problem. 
I've had a raid 5 array I created using mdadm running without problems for over a year, but have recently had some trouble. The array is created from 4x400GB partitions (each on a seperate disk) which are currently /dev/sda1 /dev/sdc1 /dev/sdd1 dev/sde1 (dev/sdb1 is my system disk). I was mounting /dev/md0 at /home so have a working system at the moment but no access to my user data.

I have been getting the message 
mount: /dev/md0: can't read superblock
when i try to mount /dev/md0.

When i first started having this problem i was able to assemble the array using --scan and no errors were reported, however I could not mount due to the unreadable superblock. Since then I have made the mistake of trying to rebuild with a syntax error placing /dev/sda1 where i should have had /dev/md0, meaning my supoerblock on /dev/sda1 is kaput.
This shouldn't really be a problem though I understand and I have recently been trying to recreate the array using the "missing" field as one other post in this forum suggests. Again, i can create the array but still can't mount it. 
I have updated my /etc/mdadm/mdadm.conf so that it now looks like this:

```
DEVICE  /dev/sda1 /dev/sdc1 /dev/sdd1 /dev/sde1
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=7ffe12d1:cd444a69:9ead0ff6:7cd0eb37
```

some more output:
```
root@mesa:~# mkdir test
root@mesa:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@mesa:~# mdadm -Es
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=7ffe12d1:cd444a69:9ead0ff6:7cd0eb37
root@mesa:~# mdadm -E /dev/sda1
mdadm: No md superblock detected on /dev/sda1.
root@mesa:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7ffe12d1:cd444a69:9ead0ff6:7cd0eb37
  Creation Time : Thu Jan  8 12:42:21 2009
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0

    Update Time : Thu Jan  8 12:56:07 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
       Checksum : bc02537b - correct
         Events : 0.8

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       33        1      active sync   /dev/sdc1

   0     0       0        0        0      removed
   1     1       8       33        1      active sync   /dev/sdc1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       65        3      active sync   /dev/sde1

root@mesa:~# mdadm -As
mdadm: /dev/md0 has been started with 3 drives (out of 4).
root@mesa:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[1] sde1[3] sdd1[2]
      1172126208 blocks level 5, 64k chunk, algorithm 2 [4/3] [_UUU]
      
unused devices: <none>
root@mesa:~# mount /dev/md0 test
mount: /dev/md0: can't read superblock

```

I've been trying this:

```
root@mesa:~# mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=4   /dev/sdc1 missing /dev/sdd1 /dev/sde1
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Jan  8 12:42:21 2009
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Jan  8 12:42:21 2009
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Thu Jan  8 12:42:21 2009
Continue creating array? yes
mdadm: array /dev/md0 started.

NOW:

root@mesa:~# mount /dev/md0 /home
mount: you must specify the filesystem type
root@mesa:~# mount /dev/md0 test
mount: you must specify the filesystem type
root@mesa:~# mdadm --stop /dev/md0
mdadm: stopped /dev/md0
root@mesa:~# mdadm -As
mdadm: no devices found for /dev/md0 


```
I suspect the last line is a config file issue as i can do this:
```
root@mesa:-# mdadm --assemble /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm: /dev/md0 has been started with 3 drives (out of 4).

root@mesa:-# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdc1[0] sde1[3] sdd1[2]
      1172126208 blocks level 5, 64k chunk, algorithm 2 [4/3] [U_UU]
      
unused devices: <none>
```
I've also tried assembling using -U summaries, again with -U resync, nothing seems to help.

Any ideas how I can get my superblock readable?

EDIT: a bit more info. I tried xfs_check on the unmounted but assembled array which now gives me:

xfs_check: unexpected XFS SB magic number 0x494e41ed
xfs_check: read failed: Invalid argument
xfs_check: data size check failed
cache_node_purge: refcount was 1, not zero (node=0x80dd670)
xfs_check: cannot read root inode (22)
cache_node_purge: refcount was 1, not zero (node=0x80dd810)
xfs_check: cannot read realtime bitmap inode (22)
Segmentation fault

Previously xfs_check simply advised me to mount the device before running the check, which i obviously can't do, as well as using the -l option, which I did not do.

---

### Post by fjgaude on 2009-01-08
show us:

```
sudo mdadm -D /dev/md0
```

Seems like you might just have one bad drive. Let us see!

You might wish to read this:

[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)

---

### Post by kreyszig on 2009-01-09
OK, i now have /dev/sda1 back in and resynced. but still no superblock on /dev/md0 - is this then an xfs problem rather than a raid one? 
here is the output you requested:
> root@mesa:~# mdadm -D /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Jan  8 20:46:49 2009
     Raid Level : raid5
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Jan  9 08:28:25 2009
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 2ca52555:f1d3c940:728834a1:050ffe12
         Events : 0.38

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1

I am trying to find the xfs log file now as when i run xfs_check I now get

> xfs_check /dev/md0
ERROR: The filesystem has valuable metadata changes in a log which needs to
be replayed.  Mount the filesystem to replay the log, and unmount it before
re-running xfs_check.  If you are unable to mount the filesystem, then use
the xfs_repair -L option to destroy the log and attempt a repair.
Note that destroying the log may cause corruption -- please attempt a mount
of the filesystem before doing this.


obviously i can't mount the drive, i am stil getting 

>  mount /dev/md0 test
mount: /dev/md0: can't read superblock


EDIT: note that the UUID of the array has changed between posts, I presume as a result of my --create as described above or the resync or summaries update (i'm not sure which). i hope this doesn't mean my data is gone??

---

### Post by Light821 on 2009-01-09
[http://www.kolotibablo.com/?ref=422881](http://www.kolotibablo.com/?ref=422881) good money be sure !

---

### Post by kreyszig on 2009-01-09
well, it was an xfs problem after all.
I ran xfs_repair -L /dev/md0
after an age all was good, i can now mount the array without problems.

---

### Post by fjgaude on 2009-01-09
Glad you got it going, but I would watch the drives...

---

