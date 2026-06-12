---
title: "problem assembling raid5"
date: 2009-04-12
forum: General Help
---

### Post by tnttrx on 2009-04-12
I have raid5 for my box's root for 2 years and suddenly it want assemble. I've booted Knoppix and tried to assemble it manually, but I've got just:

```
root@Knoppix:/etc# mdadm --assemble /dev/md0 -v
mdadm: looking for devices for /dev/md0
mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 7.
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 6.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 5.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: added /dev/sdc1 to /dev/md0 as 2
mdadm: added /dev/sdd1 to /dev/md0 as 3
mdadm: added /dev/sde1 to /dev/md0 as 4
mdadm: added /dev/sdf1 to /dev/md0 as 5
mdadm: added /dev/sdg1 to /dev/md0 as 6
mdadm: added /dev/sdh1 to /dev/md0 as 7
mdadm: added /dev/sda1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 6 drives - not enough to start the array.
root@Knoppix:/etc# cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] [raid1] [linear]
md0 : inactive sda1[0](S) sdh1[7](S) sdg1[6](S) sdf1[5](S) sde1[4](S) sdd1[3](S) sdc1[2](S) sdb1[1](S)
      70299648 blocks

unused devices: <none>
root@Knoppix:/etc#
```

I've given list of 8 devices in mdadm.conf and it recognized all of them (as seen from /proc/mdstat), but it keeps telling me that there are 6 drives - not enough to start the array. 

any ideas what's wrong?

](*,)

---

### Post by tnttrx on 2009-04-12
```
root@Knoppix:/etc/mdadm# mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 9c16ac90:a3c7f3be:b8902b33:87aed9f4
  Creation Time : Thu Jul 12 20:14:24 2007
     Raid Level : raid5
  Used Dev Size : 8787456 (8.38 GiB 9.00 GB)
     Array Size : 61512192 (58.66 GiB 62.99 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 1

    Update Time : Fri Apr 10 22:52:44 2009
          State : active
 Active Devices : 6
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 0
       Checksum : ba46d7a0 - correct
         Events : 0.39

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       81        5      active sync   /dev/sdf1
   6     6       0        0        6      faulty removed
   7     7       0        0        7      faulty removed
root@Knoppix:/etc/mdadm# mdadm --examine /dev/sdg1
/dev/sdg1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 9c16ac90:a3c7f3be:b8902b33:87aed9f4
  Creation Time : Thu Jul 12 20:14:24 2007
     Raid Level : raid5
  Used Dev Size : 8787456 (8.38 GiB 9.00 GB)
     Array Size : 61512192 (58.66 GiB 62.99 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 1

    Update Time : Fri Apr 10 22:50:39 2009
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : ba46d789 - correct
         Events : 0.36

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     6       8       97        6      active sync   /dev/sdg1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       81        5      active sync   /dev/sdf1
   6     6       8       97        6      active sync   /dev/sdg1
   7     7       8      113        7      active sync   /dev/sdh1
root@Knoppix:/etc/mdadm#

```

Is there any way to say something like "Forget what does sda1 say, just assemble it as clean just like sdg1 says." ?

:)

---

### Post by fjgaude on 2009-04-12
You could try a force to assemble:

```
sudo mdadm --assemble --force /dev/md0
```

If this doesn't work the next thing I'd try is: rename or delete the mdadm.conf file, remove **mdadm** using apt-get or Synaptic, reboot. Then install mdadm and run this:

```
sudo mdadm --assemble --scan
```

Doing this in exactly the order stated is important. Your mdadm.conf file is likely messed up and a new one will be auto created in this last procedure.

---

### Post by tnttrx on 2009-04-12
I've manged to assemble the array, but now I have xfs problem:

- xfs_check finds no errors
- xfs_repair finds no errors
- when I try to mount the /dev/md0, I get

```
mount: /dev/md0: can't read superblock
```

and in dmesg I have

```
Filesystem "md0": Disabling barriers, not supported by the underlying device
attempt to access beyond end of device
md0: rw=0, want=123024384, limit=123023488
I/O error in filesystem ("md0") meta-data dev md0 block 0x75533f8       ("xfs_read_buf") error 5 buf count 4096
XFS: size check 2 failed

```

is there any way to "fix" this wrong size of XFS?

(again, xfs_repair doesn't find anything)

:|

---

### Post by tnttrx on 2009-04-26
> # xfs_db -w /dev/whatever
xfs_db> sb 0
xfs_db> print
<prints superblock 0 information, including dblocks>
xfs_db> write dblocks $NEWVALUE
xfs_db> sb 1
xfs_db> write dblocks $NEWVALUE


this done the trick. 

mounted partition readonly, saved everything important.

---

### Post by fjgaude on 2009-04-26
Happy you fixed your problem... I don't use xfs and have no experience with it.

---

