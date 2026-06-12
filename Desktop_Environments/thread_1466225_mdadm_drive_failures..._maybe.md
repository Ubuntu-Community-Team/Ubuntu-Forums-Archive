---
title: "mdadm drive failures... maybe?"
date: 2010-04-30
forum: Desktop Environments
---

### Post by spazlon on 2010-04-30
[B]hello, i have a mdadm raid 5 with 8 1TB drives. today i logged in and checked the status of my raid like i normally do and it says i have 2 drive failures.

i started troubleshooting by identifying which drives failed. this is what i did:[/B]

ryan@server:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdg1[6](S) sdb1[1](S) sde1[4](S) sda1[0](S) sdf1[5](S) sdd1[2](S) sdc1[3](S) sdh1[7](S)
      7814079488 blocks
       
unused devices: <none>


**this didn't tell me anything specific so i then started examining the disks:**

ryan@server:~$ sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c28b5043:a0779b7d:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Apr 26 09:54:56 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Apr 30 09:10:11 2010
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 8c4249a3 - correct
         Events : 10494

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       81        5      active sync   /dev/sdf1
   6     6       8       97        6      active sync   /dev/sdg1
   7     7       8      113        7      active sync   /dev/sdh1


**this shows that /dev/sdc1 and sdd1 failed. the same stats show for /dev/sdb1 through /dev/sdh1 (except sdc1 and sdd1)**

**when i examine sdc1 or sdd1 it shows all drives are working...**

ryan@server:~$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : c28b5043:a0779b7d:01f9e43d:ac30fbff (local to host server)
  Creation Time : Mon Apr 26 09:54:56 2010
     Raid Level : raid5
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
     Array Size : 6837319552 (6520.58 GiB 7001.42 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Fri Apr 30 09:07:15 2010
          State : active
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 8c421fed - correct
         Events : 10489

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       33        3      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       65        4      active sync   /dev/sde1
   5     5       8       81        5      active sync   /dev/sdf1
   6     6       8       97        6      active sync   /dev/sdg1
   7     7       8      113        7      active sync   /dev/sdh1



**i have already identified exactly which drives failed by listing all drives by serial number:**

ryan@server:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3EP1KK -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3EP1KK-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3EWE4K -> ../../sda
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3EWE4K-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3L3APK -> ../../sdh
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3L3APK-part1 -> ../../sdh1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3M7JEK -> ../../sdg
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-Hitachi_HDT721010SLA360_STF607MH3M7JEK-part1 -> ../../sdg1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-SAMSUNG_HD103UJ_S13PJ1EQ314189 -> ../../sdf
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-SAMSUNG_HD103UJ_S13PJ1EQ314189-part1 -> ../../sdf1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-SAMSUNG_HD103UJ_S13PJ90SC12401 -> ../../sdd
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-SAMSUNG_HD103UJ_S13PJ90SC12401-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-ST31000520AS_5VX0M8Q4 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-ST31000520AS_5VX0M8Q4-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-ST3500630AS_5QG1W0QH -> ../../sdi
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-ST3500630AS_5QG1W0QH-part1 -> ../../sdi1
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-ST3500630AS_5QG1W0QH-part2 -> ../../sdi2
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-ST3500630AS_5QG1W0QH-part5 -> ../../sdi5
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 ata-WDC_WD1001FALS-00J7B1_WD-WMATV1567112 -> ../../sde
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 ata-WDC_WD1001FALS-00J7B1_WD-WMATV1567112-part1 -> ../../sde1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3EP1KK -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3EP1KK-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3EWE4K -> ../../sda
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3EWE4K-part1 -> ../../sda1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3L3APK -> ../../sdh
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3L3APK-part1 -> ../../sdh1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3M7JEK -> ../../sdg
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_Hitachi_HDT7210_STF607MH3M7JEK-part1 -> ../../sdg1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_SAMSUNG_HD103UJS13PJ1EQ314189 -> ../../sdf
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_SAMSUNG_HD103UJS13PJ1EQ314189-part1 -> ../../sdf1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_SAMSUNG_HD103UJS13PJ90SC12401 -> ../../sdd
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_SAMSUNG_HD103UJS13PJ90SC12401-part1 -> ../../sdd1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_ST31000520AS_5VX0M8Q4 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_ST31000520AS_5VX0M8Q4-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_ST3500630AS_5QG1W0QH -> ../../sdi
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_ST3500630AS_5QG1W0QH-part1 -> ../../sdi1
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_ST3500630AS_5QG1W0QH-part2 -> ../../sdi2
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_ST3500630AS_5QG1W0QH-part5 -> ../../sdi5
lrwxrwxrwx 1 root root  9 2010-04-30 10:01 scsi-SATA_WDC_WD1001FALS-_WD-WMATV1567112 -> ../../sde
lrwxrwxrwx 1 root root 10 2010-04-30 10:01 scsi-SATA_WDC_WD1001FALS-_WD-WMATV1567112-part1 -> ../../sde1


[B]so now i know what drives to pull... but i don't want to touch them unless i know for sure that they are bad. is there any way to find out if they have really failed?

thanks![/B]

---

