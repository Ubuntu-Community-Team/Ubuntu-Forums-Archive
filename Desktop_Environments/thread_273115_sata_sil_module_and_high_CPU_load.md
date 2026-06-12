---
title: "sata_sil module and high CPU load"
date: 2006-10-07
forum: Desktop Environments
---

### Post by emamoroz on 2006-10-07
Hello,

I have an ugly problem regarding my PC and Ubuntu Dapper.

My configuration is:

Athlon 2600+ Barton
1 GB Ram
Nvidia 7800 GS
MB with SATA controller onboard -> Silicon 3512
2 x Maxtor DiamondMax 10 - 200 GB HD S-ATA

The S.O. loads without any problem, but it gives me difficuties for file transfers; consequently also CD/DVD burning is affected.

Firts of all, some hdparm stats about my S-ATA

root@brutalizer:~$ hdparm -tT /dev/sda
/dev/sda:
 Timing cached reads:   1844 MB in  2.00 seconds = 921.94 MB/sec
 Timing buffered disk reads:  166 MB in  3.02 seconds =  54.96 MB/sec

root@brutalizer:~$ hdparm -tT /dev/sdb
/dev/sdb:
 Timing cached reads:   1796 MB in  2.00 seconds = 896.15 MB/sec
 Timing buffered disk reads:  186 MB in  3.02 seconds =  61.67 MB/sec

Since here, no problem, but difficulties are not related to the mere HD performance.
While testing with hdparm i notice that CPU load (seen with the applet inside gnome) goes to 100% and indicates that the CPU is waiting for I/O.
This is symptomatic, this appen also while transferring one file from sda to sdb.
Burning CDs does the same work.

I use the Ubuntu standard kernel image version 2.6.15-27-k7

The Kernel module for sata-controller is sata_sil, but I've noticed that also another module, called sata_sil24 is present inside
/lib/modules/2.6.15-27-k7/kernel/drivers/scsi/
using this module only (without sata_sil) perhaps I could solve the problem, but Ubuntu does not allow to load it and sata_sil is ever loaded.

If what I have said is true then I need some advice to solve the question and to have ubuntu working at 100% (without loading the CPU till 100%).

Using Gentoo (which now is not under control) and other distros (including a previous version of Ubuntu), there was not this problem.

I also use the standard initrd; perhaps I should modify it. Help me, Ubuntu users.

Qaplà

---

