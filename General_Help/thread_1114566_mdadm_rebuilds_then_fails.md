---
title: "mdadm rebuilds then fails"
date: 2009-04-02
forum: General Help
---

### Post by Wonslung on 2009-04-02
hello....i have a software raid5 setup on ubuntu with 6 1TB drives in raid 5 configuration....last night i noticed one of the drives had fallen out of the array...i didn't think THAT much of it because i had been working on the computer earlier that day and thought i had knocked the sata cable loose....anyways i opened it up, pushed all the cables in tight and it automatically started adding the drive back into the array...no big deal...

well i woke up today and to my horror found that 2 drives were now failed....when...i don't know exactly what happened but long story short, after reading the forums i found out i needed to try to force it to rebuild....well a bug in ubuntu's mdadm was giving me segmentation faults

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/282492](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/282492) 
that's the bug

i decided to put a spare ide hard drive in and install jaunty on it so i could try to force rebuilding the array...well it worked
the array started with 5 drives and one spare rebuilding


BUT.....as soon as it FINISHES rebuilding, it automatically fails again and i'm back where i started...i have to force it again.....i have NO IDEA what's going on...the harddrives SEEM ok...
i'll post as much data as i know how..if you need anything else please let me know...thanks for the help


```
$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jan  7 19:01:36 2009
     Raid Level : raid5
     Array Size : 4883799680 (4657.55 GiB 5001.01 GB)
  Used Dev Size : 976759936 (931.51 GiB 1000.20 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Apr  2 22:16:03 2009
          State : clean, degraded, recovering
 Active Devices : 5
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 4% complete

           UUID : cec547d8:bb56daf4:cf7cba6b:ed693cc5
         Events : 0.1696614

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       6       8       81        4      spare rebuilding   /dev/sdf1
       5       8       33        5      active sync   /dev/sdc1

```

```
$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078868

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00089cab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x401d401d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00094274

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009a290

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00043c93

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdg: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008634f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         978     7855753+  83  Linux
/dev/sdg2             979        1027      393592+   5  Extended
/dev/sdg5             979        1027      393561   82  Linux swap / Solaris

Disk /dev/md0: 5001.0 GB, 5001010872320 bytes
2 heads, 4 sectors/track, 1220949920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```
```
Apr  2 22:02:54 wonslung-raid kernel: [   60.855487] md: md0 stopped.
Apr  2 22:02:54 wonslung-raid kernel: [   60.855498] md: unbind<sdf1>
Apr  2 22:02:54 wonslung-raid kernel: [   60.891343] md: export_rdev(sdf1)
Apr  2 22:02:54 wonslung-raid kernel: [   60.891447] md: unbind<sdb1>
Apr  2 22:02:54 wonslung-raid kernel: [   60.921263] md: export_rdev(sdb1)
Apr  2 22:02:54 wonslung-raid kernel: [   60.921389] md: unbind<sda1>
Apr  2 22:02:54 wonslung-raid kernel: [   60.951262] md: export_rdev(sda1)
Apr  2 22:02:54 wonslung-raid kernel: [   60.951386] md: unbind<sdd1>
Apr  2 22:02:54 wonslung-raid kernel: [   60.981261] md: export_rdev(sdd1)
Apr  2 22:02:54 wonslung-raid kernel: [   60.981384] md: unbind<sdc1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.011262] md: export_rdev(sdc1)
Apr  2 22:02:54 wonslung-raid kernel: [   61.011378] md: unbind<sde1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.041261] md: export_rdev(sde1)
Apr  2 22:02:54 wonslung-raid kernel: [   61.064695] md: bind<sdb1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.064838] md: bind<sdd1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.064977] md: bind<sde1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.065113] md: bind<sdc1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.065654] md: bind<sdf1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.065794] md: bind<sda1>
Apr  2 22:02:54 wonslung-raid kernel: [   61.160679] raid5: device sda1 operational as raid disk 0
Apr  2 22:02:54 wonslung-raid kernel: [   61.160681] raid5: device sdc1 operational as raid disk 5
Apr  2 22:02:54 wonslung-raid kernel: [   61.160683] raid5: device sde1 operational as raid disk 3
Apr  2 22:02:54 wonslung-raid kernel: [   61.160684] raid5: device sdd1 operational as raid disk 2
Apr  2 22:02:54 wonslung-raid kernel: [   61.160685] raid5: device sdb1 operational as raid disk 1
Apr  2 22:02:54 wonslung-raid kernel: [   61.161122] raid5: allocated 6396kB for md0
Apr  2 22:02:54 wonslung-raid kernel: [   61.161124] raid5: raid level 5 set md0 active with 5 out of 6 devices, algorithm 2
Apr  2 22:02:54 wonslung-raid kernel: [   61.161242] RAID5 conf printout:
Apr  2 22:02:54 wonslung-raid kernel: [   61.161243]  --- rd:6 wd:5
Apr  2 22:02:54 wonslung-raid kernel: [   61.161244]  disk 0, o:1, dev:sda1
Apr  2 22:02:54 wonslung-raid kernel: [   61.161245]  disk 1, o:1, dev:sdb1
Apr  2 22:02:54 wonslung-raid kernel: [   61.161246]  disk 2, o:1, dev:sdd1
Apr  2 22:02:54 wonslung-raid kernel: [   61.161247]  disk 3, o:1, dev:sde1
Apr  2 22:02:54 wonslung-raid kernel: [   61.161248]  disk 5, o:1, dev:sdc1
Apr  2 22:02:54 wonslung-raid kernel: [   61.161390] md0: detected capacity change from 0 to 5001010872320
Apr  2 22:02:54 wonslung-raid kernel: [   61.161392]  md0: unknown partition table
Apr  2 22:02:54 wonslung-raid mdadm[2611]: DegradedArray event detected on md device /dev/md0
Apr  2 22:02:54 wonslung-raid kernel: [   61.162683] RAID5 conf printout:
Apr  2 22:02:54 wonslung-raid kernel: [   61.162686]  --- rd:6 wd:5
Apr  2 22:02:54 wonslung-raid kernel: [   61.162687]  disk 0, o:1, dev:sda1
Apr  2 22:02:54 wonslung-raid kernel: [   61.162688]  disk 1, o:1, dev:sdb1
Apr  2 22:02:54 wonslung-raid kernel: [   61.162689]  disk 2, o:1, dev:sdd1
Apr  2 22:02:54 wonslung-raid kernel: [   61.162690]  disk 3, o:1, dev:sde1
Apr  2 22:02:54 wonslung-raid kernel: [   61.162691]  disk 4, o:1, dev:sdf1
Apr  2 22:02:54 wonslung-raid kernel: [   61.162692]  disk 5, o:1, dev:sdc1
Apr  2 22:02:54 wonslung-raid kernel: [   61.163372] md: recovery of RAID array md0
Apr  2 22:02:54 wonslung-raid kernel: [   61.163374] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Apr  2 22:02:54 wonslung-raid kernel: [   61.163376] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
Apr  2 22:02:54 wonslung-raid kernel: [   61.163380] md: using 128k window, over a total of 976759936 blocks.
Apr  2 22:02:54 wonslung-raid mdadm[2611]: RebuildStarted event detected on md device /dev/md0
Apr  2 22:08:34 wonslung-raid kernel: [  400.863193] raid5: Disk failure on sdf1, disabling device.
Apr  2 22:08:34 wonslung-raid kernel: [  400.863195] raid5: Operation continuing on 5 devices.
Apr  2 22:08:34 wonslung-raid kernel: [  400.871430] md: md0: recovery done.
Apr  2 22:08:34 wonslung-raid mdadm[2611]: FailSpare event detected on md device /dev/md0, component device /dev/sdf1
Apr  2 22:08:34 wonslung-raid kernel: [  400.998717] RAID5 conf printout:
Apr  2 22:08:34 wonslung-raid kernel: [  400.998720]  --- rd:6 wd:5
Apr  2 22:08:34 wonslung-raid kernel: [  400.998723]  disk 0, o:1, dev:sda1
Apr  2 22:08:34 wonslung-raid kernel: [  400.998725]  disk 1, o:1, dev:sdb1
Apr  2 22:08:34 wonslung-raid kernel: [  400.998727]  disk 2, o:1, dev:sdd1
Apr  2 22:08:34 wonslung-raid kernel: [  400.998728]  disk 3, o:1, dev:sde1
Apr  2 22:08:34 wonslung-raid kernel: [  400.998730]  disk 4, o:0, dev:sdf1

```

---

### Post by Wonslung on 2009-04-03
it failed again while rebuilding.....if anyone can help.....
```
Apr  3 01:07:53 wonslung-raid kernel: [10566.567158] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 01:07:53 wonslung-raid kernel: [10566.567240] ata4.00: BMDMA stat 0x64
Apr  3 01:07:53 wonslung-raid kernel: [10566.567285] ata4.00: cmd 25/00:c0:3f:7f:c7/00:01:45:00:00/e0 tag 0 dma 229376 in
Apr  3 01:07:53 wonslung-raid kernel: [10566.567286]          res 51/40:00:39:80:c7/40:00:45:00:00/e0 Emask 0x9 (media error)
Apr  3 01:07:53 wonslung-raid kernel: [10566.567449] ata4.00: status: { DRDY ERR }
Apr  3 01:07:53 wonslung-raid kernel: [10566.567492] ata4.00: error: { UNC }
Apr  3 01:07:54 wonslung-raid kernel: [10567.580734] ata4.00: configured for UDMA/133
Apr  3 01:07:54 wonslung-raid kernel: [10567.601696] ata4.01: configured for UDMA/133
Apr  3 01:07:54 wonslung-raid kernel: [10567.601808] ata4: EH complete
Apr  3 01:07:55 wonslung-raid kernel: [10568.574116] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 01:07:55 wonslung-raid kernel: [10568.574171] ata4.00: BMDMA stat 0x64
Apr  3 01:07:55 wonslung-raid kernel: [10568.574217] ata4.00: cmd 25/00:c0:3f:7f:c7/00:01:45:00:00/e0 tag 0 dma 229376 in
Apr  3 01:07:55 wonslung-raid kernel: [10568.574218]          res 51/40:00:39:80:c7/40:00:45:00:00/e0 Emask 0x9 (media error)
Apr  3 01:07:55 wonslung-raid kernel: [10568.574380] ata4.00: status: { DRDY ERR }
Apr  3 01:07:55 wonslung-raid kernel: [10568.574424] ata4.00: error: { UNC }
Apr  3 01:07:56 wonslung-raid kernel: [10569.581578] ata4.00: configured for UDMA/133
Apr  3 01:07:56 wonslung-raid kernel: [10569.600327] ata4.01: configured for UDMA/133
Apr  3 01:07:56 wonslung-raid kernel: [10569.600441] ata4: EH complete
Apr  3 01:07:57 wonslung-raid kernel: [10570.564521] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 01:07:57 wonslung-raid kernel: [10570.564577] ata4.00: BMDMA stat 0x64
Apr  3 01:07:57 wonslung-raid kernel: [10570.564622] ata4.00: cmd 25/00:c0:3f:7f:c7/00:01:45:00:00/e0 tag 0 dma 229376 in
Apr  3 01:07:57 wonslung-raid kernel: [10570.564623]          res 51/40:00:39:80:c7/40:00:45:00:00/e0 Emask 0x9 (media error)
Apr  3 01:07:57 wonslung-raid kernel: [10570.564785] ata4.00: status: { DRDY ERR }
Apr  3 01:07:57 wonslung-raid kernel: [10570.564829] ata4.00: error: { UNC }
Apr  3 01:07:58 wonslung-raid kernel: [10571.560325] ata4.00: configured for UDMA/133
Apr  3 01:07:58 wonslung-raid kernel: [10571.581578] ata4.01: configured for UDMA/133
Apr  3 01:07:58 wonslung-raid kernel: [10571.581692] ata4: EH complete
Apr  3 01:07:59 wonslung-raid kernel: [10572.571512] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 01:07:59 wonslung-raid kernel: [10572.571568] ata4.00: BMDMA stat 0x64
Apr  3 01:07:59 wonslung-raid kernel: [10572.571613] ata4.00: cmd 25/00:c0:3f:7f:c7/00:01:45:00:00/e0 tag 0 dma 229376 in
Apr  3 01:07:59 wonslung-raid kernel: [10572.571614]          res 51/40:00:39:80:c7/40:00:45:00:00/e0 Emask 0x9 (media error)
Apr  3 01:07:59 wonslung-raid kernel: [10572.571776] ata4.00: status: { DRDY ERR }
Apr  3 01:07:59 wonslung-raid kernel: [10572.571820] ata4.00: error: { UNC }
Apr  3 01:08:00 wonslung-raid kernel: [10573.570323] ata4.00: configured for UDMA/133
Apr  3 01:08:00 wonslung-raid kernel: [10573.591577] ata4.01: configured for UDMA/133
Apr  3 01:08:00 wonslung-raid kernel: [10573.591684] ata4: EH complete
Apr  3 01:08:01 wonslung-raid kernel: [10574.537036] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 01:08:01 wonslung-raid kernel: [10574.537092] ata4.00: BMDMA stat 0x64
Apr  3 01:08:01 wonslung-raid kernel: [10574.537137] ata4.00: cmd 25/00:c0:3f:7f:c7/00:01:45:00:00/e0 tag 0 dma 229376 in
Apr  3 01:08:01 wonslung-raid kernel: [10574.537138]          res 51/40:00:39:80:c7/40:00:45:00:00/e0 Emask 0x9 (media error)
Apr  3 01:08:01 wonslung-raid kernel: [10574.537300] ata4.00: status: { DRDY ERR }
Apr  3 01:08:01 wonslung-raid kernel: [10574.537344] ata4.00: error: { UNC }
Apr  3 01:08:02 wonslung-raid kernel: [10575.540326] ata4.00: configured for UDMA/133
Apr  3 01:08:02 wonslung-raid kernel: [10575.561577] ata4.01: configured for UDMA/133
Apr  3 01:08:02 wonslung-raid kernel: [10575.561685] ata4: EH complete
Apr  3 01:08:03 wonslung-raid kernel: [10576.519154] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
Apr  3 01:08:03 wonslung-raid kernel: [10576.519209] ata4.00: BMDMA stat 0x64
Apr  3 01:08:03 wonslung-raid kernel: [10576.519255] ata4.00: cmd 25/00:c0:3f:7f:c7/00:01:45:00:00/e0 tag 0 dma 229376 in
Apr  3 01:08:03 wonslung-raid kernel: [10576.519256]          res 51/40:00:39:80:c7/40:00:45:00:00/e0 Emask 0x9 (media error)
Apr  3 01:08:03 wonslung-raid kernel: [10576.519418] ata4.00: status: { DRDY ERR }
Apr  3 01:08:03 wonslung-raid kernel: [10576.519462] ata4.00: error: { UNC }
Apr  3 01:08:04 wonslung-raid kernel: [10577.510324] ata4.00: configured for UDMA/133
Apr  3 01:08:04 wonslung-raid kernel: [10577.531576] ata4.01: configured for UDMA/133
Apr  3 01:08:04 wonslung-raid kernel: [10577.531705] sd 3:0:0:0: [sdc] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
Apr  3 01:08:04 wonslung-raid kernel: [10577.531710] sd 3:0:0:0: [sdc] Sense Key : Medium Error [current] [descriptor]
Apr  3 01:08:04 wonslung-raid kernel: [10577.531714] Descriptor sense data with sense descriptors (in hex):
Apr  3 01:08:04 wonslung-raid kernel: [10577.531716]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00
Apr  3 01:08:04 wonslung-raid kernel: [10577.531725]         45 c7 80 39
Apr  3 01:08:04 wonslung-raid kernel: [10577.531729] sd 3:0:0:0: [sdc] Add. Sense: Unrecovered read error - auto reallocate failed
Apr  3 01:08:04 wonslung-raid kernel: [10577.531734] end_request: I/O error, dev sdc, sector 1170702393
Apr  3 01:08:04 wonslung-raid kernel: [10577.531787] raid5:md0: read error not correctable (sector 1170702328 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531790] raid5: Disk failure on sdc1, disabling device.
Apr  3 01:08:04 wonslung-raid kernel: [10577.531791] raid5: Operation continuing on 4 devices.
Apr  3 01:08:04 wonslung-raid kernel: [10577.531891] raid5:md0: read error not correctable (sector 1170702336 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531894] raid5:md0: read error not correctable (sector 1170702344 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531897] raid5:md0: read error not correctable (sector 1170702352 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531900] raid5:md0: read error not correctable (sector 1170702360 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531903] raid5:md0: read error not correctable (sector 1170702368 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531905] raid5:md0: read error not correctable (sector 1170702376 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531908] raid5:md0: read error not correctable (sector 1170702384 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531911] raid5:md0: read error not correctable (sector 1170702392 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531914] raid5:md0: read error not correctable (sector 1170702400 on sdc1).
Apr  3 01:08:04 wonslung-raid kernel: [10577.531934] ata4: EH complete
Apr  3 01:08:04 wonslung-raid kernel: [10577.533758] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr  3 01:08:04 wonslung-raid kernel: [10577.536166] sd 3:0:0:0: [sdc] Write Protect is off
Apr  3 01:08:04 wonslung-raid kernel: [10577.536168] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr  3 01:08:04 wonslung-raid kernel: [10577.545334] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  3 01:08:04 wonslung-raid kernel: [10577.650139] md: md0: recovery done.
Apr  3 01:08:04 wonslung-raid kernel: [10577.654418] sd 3:0:1:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr  3 01:08:04 wonslung-raid kernel: [10577.655281] sd 3:0:1:0: [sdd] Write Protect is off
Apr  3 01:08:04 wonslung-raid kernel: [10577.655284] sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Apr  3 01:08:04 wonslung-raid kernel: [10577.655314] sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  3 01:08:04 wonslung-raid kernel: [10577.655345] sd 3:0:0:0: [sdc] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr  3 01:08:04 wonslung-raid kernel: [10577.655360] sd 3:0:0:0: [sdc] Write Protect is off
Apr  3 01:08:04 wonslung-raid kernel: [10577.655362] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
Apr  3 01:08:04 wonslung-raid kernel: [10577.655388] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  3 01:08:04 wonslung-raid kernel: [10577.655415] sd 3:0:1:0: [sdd] 1953525168 512-byte hardware sectors: (1.00 TB/931 GiB)
Apr  3 01:08:04 wonslung-raid kernel: [10577.655429] sd 3:0:1:0: [sdd] Write Protect is off
Apr  3 01:08:04 wonslung-raid kernel: [10577.655432] sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
Apr  3 01:08:04 wonslung-raid kernel: [10577.655457] sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Apr  3 01:08:04 wonslung-raid kernel: [10577.679398] RAID5 conf printout:
Apr  3 01:08:04 wonslung-raid kernel: [10577.679400]  --- rd:6 wd:4
Apr  3 01:08:04 wonslung-raid kernel: [10577.679402]  disk 0, o:1, dev:sda1
Apr  3 01:08:04 wonslung-raid kernel: [10577.679404]  disk 1, o:1, dev:sdb1
Apr  3 01:08:04 wonslung-raid kernel: [10577.679406]  disk 2, o:1, dev:sdd1
Apr  3 01:08:04 wonslung-raid kernel: [10577.679407]  disk 3, o:1, dev:sde1
Apr  3 01:08:04 wonslung-raid kernel: [10577.679409]  disk 4, o:1, dev:sdf1
Apr  3 01:08:04 wonslung-raid kernel: [10577.679410]  disk 5, o:0, dev:sdc1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711256] RAID5 conf printout:
Apr  3 01:08:04 wonslung-raid kernel: [10577.711259]  --- rd:6 wd:4
Apr  3 01:08:04 wonslung-raid kernel: [10577.711261]  disk 0, o:1, dev:sda1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711263]  disk 1, o:1, dev:sdb1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711264]  disk 2, o:1, dev:sdd1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711266]  disk 3, o:1, dev:sde1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711268]  disk 5, o:0, dev:sdc1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711275] RAID5 conf printout:
Apr  3 01:08:04 wonslung-raid kernel: [10577.711276]  --- rd:6 wd:4
Apr  3 01:08:04 wonslung-raid kernel: [10577.711278]  disk 0, o:1, dev:sda1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711279]  disk 1, o:1, dev:sdb1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711281]  disk 2, o:1, dev:sdd1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711283]  disk 3, o:1, dev:sde1
Apr  3 01:08:04 wonslung-raid kernel: [10577.711284]  disk 5, o:0, dev:sdc1
Apr  3 01:08:04 wonslung-raid kernel: [10577.741256] RAID5 conf printout:
Apr  3 01:08:04 wonslung-raid kernel: [10577.741258]  --- rd:6 wd:4
Apr  3 01:08:04 wonslung-raid kernel: [10577.741260]  disk 0, o:1, dev:sda1
Apr  3 01:08:04 wonslung-raid kernel: [10577.741262]  disk 1, o:1, dev:sdb1
Apr  3 01:08:04 wonslung-raid kernel: [10577.741264]  disk 2, o:1, dev:sdd1
Apr  3 01:08:04 wonslung-raid kernel: [10577.741265]  disk 3, o:1, dev:sde1




```

---

### Post by Wonslung on 2009-04-03
i'm dying here guys....the array never comes up, i can make it come up if i force it but then when it rebuilds it fails as soon as it hits 100%

is there anything i can do besides try to copy my data to new hard drives?

will that even work?

---

### Post by Wonslung on 2009-04-03
well i guess noone can help with this....oh well....

---

### Post by fjgaude on 2009-04-04
I can't say if this would help but here goes, try this:

```
sudo mdadm --assemble --force --scan
```

And see what happens.

These huge drives are something else, taking great amounts of time to re-sync after a failure.

I can't say but I would expect two drive failures and without backup all data is lost.

If a drive fails you need to remove it using **mdadm** and its fault and remove commands. See the **man mdadm** pages. This link might help:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)

Let us know how things go.

---

### Post by Wonslung on 2009-04-05
i did that several times, i thought i said that...anyways...


when i'd force it, in ubuntu 8.10, i'd get a segmentation fault due to a bug in mdadm...., i was able to upgrade mdadm and force it which would build the array from 5 out of 6 drives...great right?

wrong...it would resync...and as soon as it hit 100% it would fail 2 drives and drop the array

i could force it again, and as long as i kept it in degraded mode i had access to my data but the whole point of the post was to try to find a solution to the resync issue...which i never did find...

what i ended up doing was forcing it, removing the spare, formating it. copying as much data as i could fit on it , remove it from the system, put in another hard drive, copy as much as i could fit on it....remove THAT drive, copy as much as i could fit onto another hard drive and moving SOME OTHER stuff across the network..when i had everything backed up to my satisfaction i zeroed the superblock and built a new array, then moved all the data back...it took 2 days but i'm now back up and running....this time with 5 drives and 1 spare instead of 6 drives.....

i included a ton of kernel logs in this post and as much info as i could think of that might be important...even though i've solved this for my situation, if you can tell what was wrong by those logs, let me know so i know what to do different next time

---

### Post by fjgaude on 2009-04-05
Well, I've looked over the logs and can't see anything that helps me or you with what was wrong. Sorry about that!

Good luck from here on out.

---

### Post by Wonslung on 2009-04-05
now i have a new annoying problem

my computer has 7 hard drives in it.....6 1TB drives in a raid5 (5+1 spare) and 1 small drive with the OS on it.....for some reason the drives keep changing...the os was originally on /dev/sdg so my mdadm.conf had the partions listed as /dev/sd[abcdef]1  but everytime i reboot it seems to change and i end up with a resyncing raid

also, for some reason a bunch of my uuids are the same....can i change some of them somehow? and if i do can i use uuid in mdadm.conf to keep this reboot issue from occuring?
this the the outcome of blkid
/dev/sda1: UUID="d873d2eb-d15a-4b0c-8d10-b8cf3ff07134" TYPE="ext3" 
/dev/sdb1: UUID="7d599988-cd69-3c56-a0b3-43c46c549bb3" TYPE="mdraid" 
/dev/sdc1: UUID="7d599988-cd69-3c56-a0b3-43c46c549bb3" TYPE="mdraid" 
/dev/sdd1: UUID="7d599988-cd69-3c56-a0b3-43c46c549bb3" TYPE="mdraid" 
/dev/sde1: UUID="7d599988-cd69-3c56-a0b3-43c46c549bb3" TYPE="mdraid" 
/dev/sdf1: UUID="7d599988-cd69-3c56-a0b3-43c46c549bb3" TYPE="mdraid" 
/dev/md0: UUID="5681a0d9-48f1-4b4f-8713-4525f812addf" TYPE="xfs" 
/dev/sdg1: UUID="7d599988-cd69-3c56-a0b3-43c46c549bb3" TYPE="mdraid" 


see how all 6 raid drives have the same uuid? is this normal?

---

### Post by fjgaude on 2009-04-05
It's normal because the UUID is that of the array in which the drives are a part of. Such cannot be used to mount the array, is part of the superblock and shows **mdadm** which drives are associated with a particular array.

The term /dev/md0 can be used directly in your fstab file, no need to use its UUID as shown by **blkid**.

As long as you use an individual drive UUID to mount, as in fstab file, it makes no difference what the drive name is. They change as you mount drives in and out of slots or even simply by re-booting. The anme of any array never changes, is what it is set for a creation time.

I tell you, these huge drives in raid5 scare me. It takes so long to resync the chances are high that another drive will fail during that time. Remember, each drive in a raid5 has received the exact same useage, so they tend to fail together.

---

### Post by Wonslung on 2009-04-05
> **fjgaude said:**
> It's normal because the UUID is that of the array in which the drives are a part of. Such cannot be used to mount the array, is part of the superblock and shows **mdadm** which drives are associated with a particular array.

The term /dev/md0 can be used directly in your fstab file, no need to use its UUID as shown by **blkid**.

As long as you use an individual drive UUID to mount, as in fstab file, it makes no difference what the drive name is. They change as you mount drives in and out of slots or even simply by re-booting. The anme of any array never changes, is what it is set for a creation time.

I tell you, these huge drives in raid5 scare me. It takes so long to resync the chances are high that another drive will fail during that time. Remember, each drive in a raid5 has received the exact same useage, so they tend to fail together.

LOL, again, you misunderstand me....i'm sure it's my fault though
my problem is that my drives randomly change location...dont ask me why.
EXAMPLE
i have 7 hard drives
6 are raid members (raid 5 5active 1 spare)
right NOW they are /dev/sda1, /dev/sdb1, /dev/sdc1, /dev/sdd1 /dev/sde1 and /dev/sdf1

then i have another drive with the os on it, which is /dev/sdg (at least right now)

when i reboot the system the os drive sometimes changes to /dev/sda which makes 2 things happen
first, my boot procedure fails because the raid doesn't assemble, and i get a ckfs error

if i manually assemble the raid with mdadm --assemble --scan it assembles degraded because the mdadm.conf file has the partitons listed as /dev/sd[abcdef]1

now it can't find a AND one of the partitions is now /dev/sdg which was never part of the array to begin with so it starts with 4 out of 5 drives and one spare (/dev/sd[bcdef]1)

my question is can i somehow use the uuid in the /etc/mdadm/mdadm.conf OR is there a better way of wording it
```
  GNU nano 2.0.7                         File: /etc/mdadm/mdadm.conf                                                          

DEVICE /dev/sd[abcdef]1
ARRAY /dev/md0 level=raid5 num-devices=5 metadata=00.90 spares=1 UUID=8899597d:563c69cd:c443b3a0:b39b546c







```

if i used something like DEVICE /dev/sd[*]1 would that work? or can i use DEVICE then the uuid of the drives (which are all the same but DIFFERENT than the uuid for /dev/md0)

---

### Post by Cybie257 on 2009-04-05
What brand drives are you using? There was a problem with some Seagate drives, which I stand by Seagate as they have been overall the best drives I've ever used  in the past 20 years, but they had an issue with a certain batch of the 1TB drives. you can Google search for 1tb Seagate failure and see what shows. It has something to do with reporting the wrong thing(s) to the OS. Look it up for details.

I'm running an Off-Site server with 6qty 1TB Seagate drives using 8.04 (upgraded 7.10), plus 2 750GB drives, one with the OS, the other for not so important data storage. I'm having no issues that you explain.

At home, I am running Jaunty with 3 500GB drives in a RAID-5 set-up. They were built with 8.10 and reassembled flawlessly when I installed (side-by-side) Jaunty. I was able to access the RAID with both versions of the OS. 

If you have the ability to do so, I would recommend a fresh install of Jaunty and mdadm. Reassemble the RAID, but don't use the force option. If you have to force things to happen, you have something else wrong. I've never had to use that. 

Going back to the Seagate issue, if that is the case with you, then you will be chasing a problem you can't fix. Seagate is not only willing to replace the drives, but recover any data (free of charge) if needed. Check into it. 

I would also suggest using all 6 drives. No reason to have a spare, at least in my personal opinion as you can have 2 drives fail without losing any data with 6 drives. But, that would have to be something that you choose with your personal preferences. Plus, it will give you some added space in your array. 

What brand motherboard are you using? You might want to check into the BIOS settings also. Make sure you are NOT using the RAID option through BIOS. mdadm is 100% software RAID, therefore the BIOS fakeraid can be causing problems (if you have that set). This doesn't mean that you assembled the RAID via BIOS, but just have RAID enabled in BIOS (disable any RAID options). If you are using an add-on card, make sure the settings on the are not affecting it. Don't have any experience with add-on cards, so can't help with that. I use a Gigabyte MOBO, both at home and for the off-site server at work with 8 SATA ports. Works great.

I will post a link to the Seagate information later if you verify you are using Seagate drives and I can locate the article I read. 

-Cybie

---

### Post by Cybie257 on 2009-04-05
```
  GNU nano 2.0.7                         File: /etc/mdadm/mdadm.conf                                                          

DEVICE /dev/sd[abcdef]1
ARRAY /dev/md0 level=raid5 num-devices=5 metadata=00.90 spares=1 UUID=8899597d:563c69cd:c443b3a0:b39b546c

```

Here is a copy of my mdadm.conf at home. Look at the DEVICE setting. It is:
DEVICE partitions. 
Maybe this is something you can try to change and see what happens. this might get rid of he reboot issue.?? Not 100%, but something you can try.

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=d89f1d20:e9ad4547:61893a1e:8b5d8522

# This file was auto-generated on Sun, 01 Mar 2009 17:24:59 -0800
# by mkconf $Id$
```

---

### Post by Wonslung on 2009-04-05
> **Cybie257 said:**
> What brand drives are you using? There was a problem with some Seagate drives, which I stand by Seagate as they have been overall the best drives I've ever used  in the past 20 years, but they had an issue with a certain batch of the 1TB drives. you can Google search for 1tb Seagate failure and see what shows. It has something to do with reporting the wrong thing(s) to the OS. Look it up for details.
i too like seagate and use them for most things, one of them is a 1TB seagate baracuda, but the other 5 are samsung drives)

> 
I'm running an Off-Site server with 6qty 1TB Seagate drives using 8.04 (upgraded 7.10), plus 2 750GB drives, one with the OS, the other for not so important data storage. I'm having no issues that you explain.


i'm not having the issues anymore, i figured out the ORIGINAL cause of the problem.  I have the 6 drives installed in 2 3 bay hot swap bays with a trayless design.  It's spring loaded so when you pull the level the drive pops forward....one of the 3 bay units functions perfectly, but the other one was loosing connection to one of the drives (the right most drive) sometimes which caused it to drop from the array from time to time, i was able to solve this issue by bending the spring some, but i'm going to order a replacement asap...i think what happened was that i had that issue occur and then had a power outage right after it or something and it ended up failing 2 drives at once...the event numbers were off by 7 which is why i had to force the array to assemble...the problem was that mdadm in ubuntu 8.10 and before has a bug which causes the force option to give a segmentation fault in some situations..i was able to work past this issue by installing jaunty on another small ide drive which has an updated mdadm....this allowed me to force the array to assemble, but the strange thing is that as soon as it got to 99.9% done resyncing both the resync drive and the drive with the originally lower event number would both fail again...leaving me in the situation of not having access to my data....i tried several times to let if resync but it ALWAYS failed at 99.9%...luckily the data was fine....i was able to force assemble the array, remove the resync drive, leave it degraded and copy all my data to other hard drives....after i had it all backed up i simply took down the array, formated the drives, zeroed the superblock, reinstalled 8.10 server and built a new raid 5

> 
At home, I am running Jaunty with 3 500GB drives in a RAID-5 set-up. They were built with 8.10 and reassembled flawlessly when I installed (side-by-side) Jaunty. I was able to access the RAID with both versions of the OS. 


i was very happy with jaunty but the problem for me was that i use this server as a torrentflux-b4rt/samba/media server and 2 of the machines are ps3's.....i use a program called ps3mediaserver to transcode mkv files on the fly to those 2 machines which requires ffmpeg-mt, mencoder and mplayer-mt...i was unable to get ffmpeg-mt to compile under jaunty.....i tried for about 2 hours with no luck and it works fine under 8.10 so i just went back to that....i also serve media to 2 xbox360's which use fuppes, another upnp server and it does transcoding aswell....i need ffmpeg-mt in order to get 1080p to play smoothly and there just isn't a package available that i can find that works.
> 
If you have the ability to do so, I would recommend a fresh install of Jaunty and mdadm. Reassemble the RAID, but don't use the force option. If you have to force things to happen, you have something else wrong. I've never had to use that. 

again, i TRIED that...the force option was absolutely necessary due to the fact that it was a 6 drive array with 4 good drives and 1 drive who's event number was off by 7 and 1 drive that was in the middle of a resync when it went down originally meaning it was marked as spare
that is what the force option is FOR...the problem is that normally once you force it and it completes the resync, you're ok...you might loose some data (whatever was writen after the event number) but i didn't.....and if i had it would have been the most recent stuff...it was only off by 7
 
> 
Going back to the Seagate issue, if that is the case with you, then you will be chasing a problem you can't fix. Seagate is not only willing to replace the drives, but recover any data (free of charge) if needed. Check into it. 

I would also suggest using all 6 drives. No reason to have a spare, at least in my personal opinion as you can have 2 drives fail without losing any data with 6 drives. But, that would have to be something that you choose with your personal preferences. Plus, it will give you some added space in your array.

This is wrong....if you have a raid 6 you can have 2 drives fail without loosing data but with a raid5 you can only suffer the permanent loss of 1 drive...if i wasn't lucky enough to have most of the data on one of those drives i would have been totally screwed....what happened to me is WHY i am using one as a hot spare now...i WAS using 6 drives without a spare and this is the boat i ended up in and it was WAY too close of a call....

> 
What brand motherboard are you using? You might want to check into the BIOS settings also. Make sure you are NOT using the RAID option through BIOS. mdadm is 100% software RAID, therefore the BIOS fakeraid can be causing problems (if you have that set). This doesn't mean that you assembled the RAID via BIOS, but just have RAID enabled in BIOS (disable any RAID options). If you are using an add-on card, make sure the settings on the are not affecting it. Don't have any experience with add-on cards, so can't help with that. I use a Gigabyte MOBO, both at home and for the off-site server at work with 8 SATA ports. Works great.


i'm well aware of the different types of raid and different raid levels...no, my motherboard is not set to raid...would that even work? i don't think so.....i have a MSI P43 Neo3-F LGA 775 Intel P43
> 
I will post a link to the Seagate information later if you verify you are using Seagate drives and I can locate the article I read. 

-Cybie

like i said, i have a single seagate drive but i'm almost 100% sure my original issue was caused by a faulty tray...the issue of linux changing the drive letters is NOT a unique issue...i've read about it before...i just don't remember what the advice was...i think whoever said changing the mdadm.conf to DEVICES partitions was probably right....i'll try that

---

### Post by Cybie257 on 2009-04-06
> **Wonslung said:**
> i too like seagate and use them for most things, one of them is a 1TB seagate baracuda, but the other 5 are samsung drives)

i'm not having the issues anymore, i figured out the ORIGINAL cause of the problem. 

Glad to see you found the problem

> 
This is wrong....if you have a raid 6 you can have 2 drives fail without loosing data but with a raid5 you can only suffer the permanent loss of 1 drive...if i wasn't lucky enough to have most of the data on one of those drives i would have been totally screwed....what happened to me is WHY i am using one as a hot spare now...i WAS using 6 drives without a spare and this is the boat i ended up in and it was WAY too close of a call....

I stand corrected. you are right. I guess I confused the issue or RAID-5 "with a spare". That would give you the RAID-5 that would allow 2 failed drives. One live, plus the spare.

> 
i'm well aware of the different types of raid and different raid levels...no, my motherboard is not set to raid...would that even work? i don't think so.....i have a MSI P43 Neo3-F LGA 775 Intel P43

Some motherboards have on-board RAID that you can configure your arrays via BIOS. The reason mdadm/software RAID is better and more reliable is because you don't rely on reading BIOS information to get the status, but more importantly, if your MOBO dies, your RAID dies with it. with mdadm, if your MOBO dies, you replace it with just about any other with enough ports and rebuild the array via mdadm. 

> 
like i said, i have a single seagate drive but i'm almost 100% sure my original issue was caused by a faulty tray...the issue of linux changing the drive letters is NOT a unique issue...i've read about it before...i just don't remember what the advice was...i think whoever said changing the mdadm.conf to DEVICES partitions was probably right....i'll try that

That would've been my post following this one you replied to for changing DEVICE partitions in mdadm.conf. 

It would be interesting to know if you changed that and how it worked out. 

-Cybie

---

### Post by Wonslung on 2009-04-06
i did change it and it hasn't happened since but it didn't happen every single time i reboot so we'll see how it works out...and yah, i know mdadm is awesome, i much prefer software raid.  Hardware raid is sweet too if you REALLY need the extra speed but these days it's not much and i can saturate a gigabit line with software raid anyways and it doesn't use much more than 1 of my cpu unless it's resyncing....and even then it's no more than 10%

---

