---
title: "mdadm: DeviceDisappeared event detected on md device /dev/md0, component device Wron"
date: 2008-03-24
forum: Desktop Environments
---

### Post by Gadgetman on 2008-03-24
I have a working dual RAID0 setup (2 lots of 2x250GB IDE drives) using LVM to form one large volume (1TB) running on 7.10 (Gutsy) with all the latest updates. The OS is on a separate std bootable 250GB drive. This has been stable for 6 months. This setup is my backend for mythtv. Lately (in the last few days), I have noticed that the system has rebooted for no apparent reason. On checking the syslog, I find the following suspicious entries:-

 Mar 24 14:28:32 malutipvr mdadm: DeviceDisappeared event detected on md device /dev/md0, component device Wrong-Level
Mar 24 14:28:32 malutipvr /etc/mysql/debian-start[5942]: WARNING: mysqlcheck has found corrupt tables
Mar 24 14:28:32 malutipvr /etc/mysql/debian-start[5942]: mythconverg.housekeeping
Mar 24 14:28:32 malutipvr /etc/mysql/debian-start[5942]: warning  : 1 client is using or hasn't closed the table properly
Mar 24 14:28:32 malutipvr /etc/mysql/debian-start[5942]: mythconverg.inuseprograms
Mar 24 14:28:32 malutipvr /etc/mysql/debian-start[5942]: warning  : 1 client is using or hasn't closed the table properly
Mar 24 14:28:32 malutipvr /etc/mysql/debian-start[5942]: mythconverg.mythlog
Mar 24 14:33:29 malutipvr audio[5889]: add_service_record: got record id 0x10001
Mar 24 14:33:29 malutipvr audio[5889]: Registered manager path:/org/bluez/audio
Mar 24 14:33:29 malutipvr mdadm: DeviceDisappeared event detected on md device /dev/md0, component device Wrong-Level
Mar 24 14:33:29 malutipvr ntpd[5938]: ntpd 4.2.4p0@1.1472-o Thu Oct  4 20:58:45 UTC 2007 (1)
Mar 24 14:33:29 malutipvr ntpd[5939]: precision = 1.000 usec
Mar 24 14:33:29 malutipvr ntpd[5939]: Listening on interface #0 wildcard, 0.0.0.0#123 Disabled
Mar 24 14:33:29 malutipvr ntpd[5939]: Listening on interface #1 wildcard, ::#123 Disabled
Mar 24 14:33:29 malutipvr ntpd[5939]: Listening on interface #2 eth0, fe80::211:9ff:fed4:5c7d#123 Enabled
Mar 24 14:33:29 malutipvr ntpd[5939]: Listening on interface #3 lo, ::1#123 Enabled
Mar 24 14:33:29 malutipvr ntpd[5939]: Listening on interface #4 lo, 127.0.0.1#123 Enabled
Mar 24 14:33:29 malutipvr ntpd[5939]: Listening on interface #5 eth0, 192.168.5.30#123 Enabled
Mar 24 14:33:29 malutipvr ntpd[5939]: kernel time sync status 0040
Mar 24 14:33:29 malutipvr ntpd[5939]: frequency initialized 39.614 PPM from /var/lib/ntp/ntp.drift
Mar 24 14:33:30 malutipvr lircd-0.8.2[5960]: lircd(userspace) ready
Mar 24 14:33:30 malutipvr anacron[5977]: Anacron 2.3 started on 2008-03-24
Mar 24 14:33:30 malutipvr anacron[5977]: Normal exit (0 jobs run)
Mar 24 14:33:30 malutipvr /usr/sbin/cron[6004]: (CRON) INFO (pidfile fd = 3)
Mar 24 14:33:30 malutipvr /usr/sbin/cron[6006]: (CRON) STARTUP (fork ok)
Mar 24 14:33:30 malutipvr /usr/sbin/cron[6006]: (CRON) INFO (Running @reboot jobs)
Mar 24 14:37:45 malutipvr syslogd 1.4.1#21ubuntu3: restart.
Mar 24 14:37:46 malutipvr kernel: Inspecting /boot/System.map-2.6.22-14-generic
Mar 24 14:37:46 malutipvr kernel: Loaded 25445 symbols from /boot/System.map-2.6.22-14-generic.
Mar 24 14:37:46 malutipvr kernel: Symbols match kernel version 2.6.22.
Mar 24 14:37:46 malutipvr kernel: No module symbols loaded - kernel modules not enabled.
Mar 24 14:37:46 malutipvr kernel: [    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)

Does this mean that 1 (or more) of my RAID drives are failing?

Here are my LVM settings:-
root@malutipvr:/etc/lvm# lvscan
  ACTIVE            '/dev/PVRFileServer/MMStore' [935.00 GB] inherit
root@malutipvr:/etc/lvm# vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "PVRFileServer" using metadata type lvm2
root@malutipvr:/etc/lvm# pvscan
  PV /dev/md0   VG PVRFileServer   lvm2 [467.51 GB / 0    free]
  PV /dev/md1   VG PVRFileServer   lvm2 [467.51 GB / 24.00 MB free]
  Total: 2 [935.02 GB] / in use: 2 [935.02 GB] / in no VG: 0 [0   ]
root@malutipvr:/etc/lvm#

here are my RAID settings:-
root@malutipvr:/etc/lvm# mdadm --misc --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Aug  9 16:06:49 2007
     Raid Level : raid0
     Array Size : 490223104 (467.51 GiB 501.99 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Aug  9 16:06:49 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 256K

           UUID : 56032f9c:ae53b39a:368bedc1:ebec24b4
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       3        1        0      active sync   /dev/hda1
       1      22        1        1      active sync   /dev/hdc1
root@malutipvr:/etc/lvm# mdadm --misc --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Mon Sep 10 00:11:55 2007
     Raid Level : raid0
     Array Size : 490223104 (467.51 GiB 501.99 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Sep 10 00:11:55 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 256K

           UUID : 5984cc76:12f4fb7b:b9ba66e9:357b7b42 (local to host malutipvr)
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       3       65        0      active sync   /dev/hdb1
       1      22       65        1      active sync   /dev/hdd1
root@malutipvr:/etc/lvm#

---

### Post by bigredradio on 2008-03-24
You might want to look at this:

[https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/104251](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/104251)

According to the bug it appears after a reboot. Why it is rebooting may be a different issue to investigate.

---

### Post by Gadgetman on 2008-03-26
In my situation, it does not happen immediately after a boot - but sometimes many hours later.

Now I am get a further error:-
Mar 26 20:10:55 malutipvr kernel: [55601.353221] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Mar 26 20:10:55 malutipvr kernel: [55601.353231] hdb: dma_intr: error=0x40 { UncorrectableError }, LBAsect=332526504, high=19, low=13759400, sector=332526487
Mar 26 20:10:55 malutipvr kernel: [55601.353247] ide: failed opcode was: unknown
Mar 26 20:10:55 malutipvr kernel: [55601.353253] end_request: I/O error, dev hdb, sector 332526487
M


Does this mean that a HD (hdb) is failing?
(sorry but I am not familiar with these messages)

Is it just bad sectors? Can they be re-assigned?

---

