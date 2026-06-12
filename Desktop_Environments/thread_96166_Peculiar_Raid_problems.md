---
title: "Peculiar Raid problems"
date: 2005-11-28
forum: Desktop Environments
---

### Post by Gisli Ottarsson on 2005-11-28
I am experiencing a strange problem with Raid on my Breezy installation.

Using the live CD, I created a raid5 and a raid 1+0 with the following commands:

mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
mdadm --create /dev/md1 --level=0 --raid-devices=2 /dev/sda3 /dev/sdb3
mdadm --create /dev/md2 --level=0 --raid-devices=2 /dev/sdc4 /dev/sdd4
mdadm --create /dev/md3 --level=1 --raid-devices=2 /dev/md1 /dev/md2

and when I looked at /proc/mdistat I saw:

Personalities : [raid0] [raid1] [raid5]
md3 : active raid1 md2[1] md1[0]
      216877248 blocks [2/2] [UU]

md2 : active raid0 sdd4[1] sdc4[0]
      216877312 blocks 64k chunks

md1 : active raid0 sdb3[1] sda3[0]
      216877312 blocks 64k chunks

md0 : active raid5 sdd1[2] sdc1[1] sdb1[0]
      16578816 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

unused devices: <none>

which is what I wanted.  I formatted the raids and other non-raid partitions with the Reiser filesystems.  No problems were reported.  I then switched to the install CD and proceeded to install Breezy on the machine with /usr on the raid5 and /home on the raid1+0.  I do not recall encountering any difficulties when I told the Breezy installer about the raid drives.

After installing, when I 'cat /prod/mdstat' I see something altogether different.
It is currently showing me the following:

Personalities : [raid0] [raid1] [raid5]
md255 : active raid5 dm-2[2] dm-1[1] dm-0[0]
      16578816 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md3 : active raid1 md0[2](F) md2[1]
      216877248 blocks [2/1] [_U]

md2 : active raid0 sdc4[0] sdd4[1]
      216877312 blocks 64k chunks

md1 : active raid5 sdb1[0] sdd1[2] sdc1[1]
      16578816 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md0 : active raid0 sda3[0] sdb3[1]
      216877312 blocks 64k chunks

unused devices: <none>

Here are some questions I am grappling with:

1) What is md255?

2) Why is the raid5, which I created as /dev/md0 showing up as /dev/md1?

3) Note /dev/md3 which has drives 1 and 2 but no drive 0.  It has md0 showing up as a faulty drive 2.  Initially, md0 was not showing up at all.  When I ran mdadm --detail drive 0 showed up with a 'removed' state.  I used mdadm --add to add /dev/md0 and everything seemed to be going well for about 30 minutes.  /prod/mdstat showed that /dev/md0 was being synced into the array but ultimately it showed up as faulty.   Meanwhile mdistat is showing /dev/md0 as being OK.  

My syslog contains the following information corresponding to the --add command:

Nov 28 11:38:56 localhost kernel: [4517749.713000] md: bind<md0>
Nov 28 11:38:56 localhost kernel: [4517749.713000] RAID1 conf printout:
Nov 28 11:38:56 localhost kernel: [4517749.713000]  --- wd:1 rd:2
Nov 28 11:38:56 localhost kernel: [4517749.713000]  disk 0, wo:1, o:1, dev:md0
Nov 28 11:38:56 localhost kernel: [4517749.713000]  disk 1, wo:0, o:1, dev:md2
Nov 28 11:38:56 localhost kernel: [4517749.713000] .....<6>md: syncing RAID array md3
Nov 28 11:38:56 localhost kernel: [4517749.713000] md: minimum _guaranteed_ reconstruction speed: 1000 KB/sec/disc.
Nov 28 11:38:56 localhost kernel: [4517749.713000] md: using maximum available idle IO bandwith (but not more than 200000 KB/sec) for reconstruction.
Nov 28 11:38:56 localhost kernel: [4517749.713000] md: using 128k window, over a total of 216877248 blocks.
Nov 28 11:56:19 localhost -- MARK --
Nov 28 12:06:00 localhost kernel: [4519374.687000] ata2: translated ATA stat/err 0x35/00 to SCSI SK/ASC/ASCQ 0x4/00/00
Nov 28 12:06:00 localhost kernel: [4519374.687000] ata2: status=0x35 { DeviceFault SeekComplete CorrectedError Error }
Nov 28 12:06:00 localhost kernel: [4519374.687000] SCSI error : <1 0 1 0> return code = 0x8000002
Nov 28 12:06:00 localhost kernel: [4519374.687000] sdb: Current: sense key: Hardware Error
Nov 28 12:06:00 localhost kernel: [4519374.687000]     Additional sense: No additional sense information
Nov 28 12:06:00 localhost kernel: [4519374.687000] end_request: I/O error, dev sdb, sector 99433349
Nov 28 12:06:00 localhost kernel: [4519374.688000] raid1: Disk failure on md0, disabling device.
Nov 28 12:06:00 localhost kernel: [4519374.688000] ^IOperation continuing on 1 devices
Nov 28 12:06:00 localhost kernel: [4519374.688000] md: md3: sync done.
Nov 28 12:06:01 localhost kernel: [4519374.708000] RAID1 conf printout:
Nov 28 12:06:01 localhost kernel: [4519374.708000]  --- wd:1 rd:2
Nov 28 12:06:01 localhost kernel: [4519374.708000]  disk 0, wo:1, o:0, dev:md0
Nov 28 12:06:01 localhost kernel: [4519374.708000]  disk 1, wo:0, o:1, dev:md2
Nov 28 12:06:01 localhost kernel: [4519374.711000] RAID1 conf printout:
Nov 28 12:06:01 localhost kernel: [4519374.711000]  --- wd:1 rd:2
Nov 28 12:06:01 localhost kernel: [4519374.711000]  disk 1, wo:0, o:1, dev:md2

If this is indeed a hardware problem, why isn't the md0 raid complaining.  This is the raid which is talking directly to hardware.  md3 is only talking to two raids, both of which claim to be OK.  This does not make any sense.

After the --add command, mdadm --detail /dev/md3 shows:

/dev/md3:
        Version : 00.90.01
  Creation Time : Fri Nov 25 13:29:43 2005
     Raid Level : raid1
     Array Size : 216877248 (206.83 GiB 222.08 GB)
    Device Size : 216877248 (206.83 GiB 222.08 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 3
    Persistence : Superblock is persistent

    Update Time : Mon Nov 28 13:57:24 2005
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           UUID : 5b3f905f:8e04b703:aaf20c04:211f58e9
         Events : 0.46901

    Number   Major   Minor   RaidDevice State
       0       0        0        -      removed
       1       9        2        1      active sync   /dev/evms/.nodes/md/md2

       2       9        0        -      faulty   /dev/.static/dev/md0

I have backed up all the data from /dev/md3 and am thinking about rebuilding the array, but I am bothered by the alleged hardware problems and the mysterious musical chairs of /dev/mdi0 and /dev/md1 (see question 2).

Any suggestions about what I may be doing wrong would be most welcome.

Is it possible that there is a bug in the installer?  How would I go about gathering information for an intelligent bug report?  Is there a better way to fix the problem than building /home from scratch?

Thanks

    Gisli

---

### Post by hoakz on 2007-02-21
I have a similar problem (md255 turning up) with a different RAID setup.

At first (with only the raid-5 device with four disks) everything worked just fine, 
but when I added the linear and the raid-1 I got this problem.  I'm also seeing 
devices changing names after reboot (not sure however if that just happens a 
limited number of times...)

Here's my setup:
$ cat /proc/mdstat
Personalities : [linear] [raid1] [raid5]
md255 : active raid5 dm-9[3](S) dm-8[2] dm-7[1] dm-6[0]
     586067072 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
     unused devices: <none>

md2 : active linear hdd1[0] hdb1[1]
     195366272 blocks 64k rounding

md1 : active raid5 sdd1[0] sde1[3](S) sdf1[2] sdb1[1]
     586067072 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md0 : active raid1 sda1[0] sdc1[1]
     390708736 blocks [2/2] [UU]

---

