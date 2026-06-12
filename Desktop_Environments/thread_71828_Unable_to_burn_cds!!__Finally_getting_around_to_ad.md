---
title: "Unable to burn cds?!?!  Finally getting around to addressing this..."
date: 2005-10-04
forum: Desktop Environments
---

### Post by Scythe on 2005-10-04
First of all, the problem that is my perverbial thorn in my side:  I used to be able to burn CDs, and now I cannot.

It was a few weekends back, I cracked off a couple of cds while looking at the in-laws' computer.  Later that weekend I did an update of my installed apps and afterwards I've never been able to burn a disc since.

The error log from K3B barfs back the following:

```
Devices
-----------------------
CDWRITER IDE2410 A.23 (/dev/sr0, ) at  [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
SAMSUNG DVD-ROM SD-616T F310 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

System
-----------------------
K3b Version: 0.11.24
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.10-5-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.31
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'CDWRITER'
Identifikation : 'IDE2410         '
Revision       : 'A.23'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1971200 = 1925 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data     9 MB        
Total size:       10 MB (01:01.77) = 4633 sectors
Lout start:       10 MB (01:03/58) = 4633 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 7
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11597 (97:27/28)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 20
Manufacturer: Princo Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 355216
Starting to write CD/DVD at speed 24 in dummy TAO mode for single session.
Last chance to quit, starting dummy write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Starting new track at sector: 0
Track 01:    0 of    9 MB written.
/usr/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 7C 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, deferred error, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 40s
/usr/bin/cdrecord: The current problem looks like a buffer underrun.
/usr/bin/cdrecord: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/cdrecord: Please report.
/usr/bin/cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 253952 bytes
Writing  time:    6.269s
Average write speed   9.9x.
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    0.006s
/usr/bin/cdrecord: fifo had 68 puts and 5 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 2 times full, min fill was 95%.
BURN-Free was never needed.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=0,0,0 speed=24 -tao -dummy driveropts=burnfree -eject -data /tmp/kde-papa/K3b data project.iso 

mkisofs
-----------------------
INFO: ISO-8859-1 character encoding detected by locale settings.
 Assuming ISO-8859-1 encoded filenames on source filesystem,
 use -input-charset to override.
 10.90% done, estimate finish Tue Oct  4 13:38:27 2005
 21.62% done, estimate finish Tue Oct  4 13:38:27 2005
 32.67% done, estimate finish Tue Oct  4 13:38:27 2005
 43.38% done, estimate finish Tue Oct  4 13:38:27 2005
 54.09% done, estimate finish Tue Oct  4 13:38:28 2005
 64.80% done, estimate finish Tue Oct  4 13:38:28 2005
 75.86% done, estimate finish Tue Oct  4 13:38:28 2005
 86.57% done, estimate finish Tue Oct  4 13:38:28 2005
Total translation table size: 0
Total rockridge attributes bytes: 264
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 1f000
4631 extents written (9 MB)

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR VERSION 0.11.24 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.24 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-papa/k3bUFYQNa.tmp -rational-rock -hide-list /tmp/kde-papa/k3b6iJnMb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-papa/k3bWFaZ3b.tmp /home/papa/.kde/share/apps/k3b/temp/dummydir0/ 

```

Now I've scoured the forums looking for a solution.  Tried running as sudo, tried re-installing cdrecord, k3b, and nautilus cd-burner, tried gnomebaker, tried pulling my hair out...all to no end (yes I know the output above is from an attempt to "simulate" a burn, the errors are the same and I'm not a money machine that likes to purchase 1000's of CDRs to debug a problem).

Assistance on this would be tremendously helpful.

That being said, I do like Ubuntu (been running it exclusively for a year now) but the following things irk me:
1 - Please standardize the repositories.  Re-naming them or losing them every 6 months or so is very frustrating.  If you're going to have them, make them permanent.
2 - Stop breaking things with updates/upgrades.  Warty to Hoary killed my USB scripts and I had to reconfigure my sound to work again (thanks to the forum posters for their solutions).  Now since another update my ability to burn cds is broken!  Not to mention a broken Firefox after a recent update (fixed as well).

If the Ubuntu team intends Ubuntu to be an OS for the people, keep in mind that the people for the most part don't want to deal with problems like this.  They want an OS that just works, that's how Windows stuck around for so long.  Average Joes don't want to sift through tonnes of forums and try a hundred different dead-ends to solve the problem - if it was working before, it should work now.

I look forward to any solutions to my cd burning problem.  If I can't get it resolved I'll be putting Ubuntu behind me (as I'll apparently have to reinstall Windows in order to burn other ISOs anyways...)

-Scythe

---

### Post by KingBahamut on 2005-10-04
use cdrdao instead of cdrecord. 
I assume your running under KDE rather than gnome, correct?

---

### Post by KingBahamut on 2005-10-04
as far as to the remainder of your post....Elaborate please. I fail to see how saying you want something to change without explaining in a less aggressive manner can be helpful.

---

### Post by tktreload on 2005-10-04
[QUOTE=Scythe]
If the Ubuntu team intends Ubuntu to be an OS for the people, keep in mind that the people for the most part don't want to deal with problems like this.  They want an OS that just works, that's how Windows stuck around for so long.  Average Joes don't want to sift through tonnes of forums and try a hundred different dead-ends to solve the problem - if it was working before, it should work now.
I look forward to any solutions to my cd burning problem.  If I can't get it resolved I'll be putting Ubuntu behind me (as I'll apparently have to reinstall Windows in order to burn other ISOs anyways...)[/QUOTE]

a big part of running linux is getting down to it and fixing all the small things...Actually most of the fun is finding and fixin all the small things. You really learn a lot by setting up things, and solving problems
so if you dont like it. leave it

---

### Post by Scythe on 2005-10-04
cdrdao fails as well...

```
Devices
-----------------------
CDWRITER IDE2410 A.23 (/dev/sr0, ) at  [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
SAMSUNG DVD-ROM SD-616T F310 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

System
-----------------------
K3b Version: 0.11.24
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

cdrdao
-----------------------
Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty
Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.
Using libscg version 'schily-0.8'
1,0,0: CDWRITER IDE2410 Rev: A.23
Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0010)
Burning entire 79 mins disc.
Starting write simulation at speed 24...
Process can be aborted with QUIT signal (usually CTRL-\).
WARNING: No super user permission to setup real time scheduling.
Turning BURN-Proof on
/usr/bin/cdrdao: Input/output error.  : scsi sendcmd: no error
CDB:  2A 00 FF FF FF D2 00 00 1A 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 02 00 00 00 00 0A 00 00 00 00 04 07 00 00
Sense Key: 0x2 Not Ready, Segment 0
Sense Code: 0x04 Qual 0x07 (logical unit not ready, operation in progress) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 53248
cmd finished after 0.030s timeout 180s
ERROR: Write data failed.
ERROR: Simulation failed.
ERROR: Cannot prevent/allow medium removal.

cdrdao comand:
-----------------------
/usr/bin/cdrdao write --device 1,0,0 --driver generic-mmc:0x00000010 --speed 24 --simulate --overburn -n -v 2 --force --eject --remote 20 /tmp/kde-papa/k3b0qRIcatoc 

mkisofs
-----------------------
INFO: ISO-8859-1 character encoding detected by locale settings.
 Assuming ISO-8859-1 encoded filenames on source filesystem,
 use -input-charset to override.
 10.90% done, estimate finish Tue Oct  4 16:10:29 2005
 21.62% done, estimate finish Tue Oct  4 16:10:29 2005
 32.67% done, estimate finish Tue Oct  4 16:10:29 2005
 43.38% done, estimate finish Tue Oct  4 16:10:29 2005
 54.09% done, estimate finish Tue Oct  4 16:10:29 2005
 64.80% done, estimate finish Tue Oct  4 16:10:29 2005
 75.86% done, estimate finish Tue Oct  4 16:10:29 2005
 86.57% done, estimate finish Tue Oct  4 16:10:30 2005
Total translation table size: 0
Total rockridge attributes bytes: 264
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 1f000
4631 extents written (9 MB)

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR VERSION 0.11.24 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.24 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-papa/k3bXAXEhb.tmp -rational-rock -hide-list /tmp/kde-papa/k3bPQ2Myb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-papa/k3bygKmeb.tmp /home/papa/.kde/share/apps/k3b/temp/dummydir0/ 

```

---

### Post by Scythe on 2005-10-04
[QUOTE=tktreload]a big part of running linux is getting down to it and fixing all the small things...Actually most of the fun is finding and fixin all the small things. You really learn a lot by setting up things, and solving problems
so if you dont like it. leave it[/QUOTE]

Hey, I'm for that if it's something *new* I'm trying to do.  But if my computer was working fine and I do an update it is not a far fetched idea that I should *expect* (note: not *prefer*, but *expect*) that it shall keep functioning fine.

I've heard all the linux chatter before of you have to dig through the trenches like everyone else to keep your computer working.  It's that mindset that keeps linux from being a *real* contender.  I shouldn't have to spend a week after an update giving myself a headache trying to keep my machine functioning properly.  Make it work, and make it simple, and they will come.

-Scythe

---

### Post by tktreload on 2005-10-04
if things get messed up by updating, try only installing critical updates, that way the problems should be minimized

---

### Post by jworr on 2005-10-05
I would reduce your apt sources to just the offical ubuntu ones remove all your cd burning software then reinstalling it.  From reading the debug info it looks like you have a non-standard version of cdrecord.  Or I could have no idea what I am talking about:)

---

### Post by tjabri on 2005-10-18
> **Scythe]First of all, the problem that is my perverbial thorn in my side:  I used to be able to burn CDs, and now I cannot.

It was a few weekends back, I cracked off a couple of cds while looking at the in-laws' computer.  Later that weekend I did an update of my installed apps and afterwards I've never been able to burn a disc since.

The error log from K3B barfs back the following:

```
Devices
-----------------------
CDWRITER IDE2410 A.23 (/dev/sr0, ) at  [CD-R said:**
>  [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R16; RAW/R96P; RAW/R96R]
SAMSUNG DVD-ROM SD-616T F310 (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

System
-----------------------
K3b Version: 0.11.24
KDE Version: 3.4.0
QT Version:  3.3.3
Kernel:      2.6.10-5-386

cdrecord
-----------------------
/usr/bin/cdrecord: Warning: Running on Linux-2.6.10-5-386
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '0,0,0'
scsibus: 0 target: 0 lun: 0
Linux sg driver version: 3.5.31
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 1
Vendor_info    : 'CDWRITER'
Identifikation : 'IDE2410         '
Revision       : 'A.23'
Device seems to be: Generic mmc CD-RW.
Current: 0x0009
Profile: 0x000A 
Profile: 0x0009 (current)
Profile: 0x0008 
Profile: 0x0002 (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1971200 = 1925 KB
FIFO size      : 4194304 = 4096 KB
/usr/bin/cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
/usr/bin/cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
/usr/bin/cdrecord: WARNING: This causes a high risk for buffer underruns.
Track 01: data     9 MB        
Total size:       10 MB (01:01.77) = 4633 sectors
Lout start:       10 MB (01:03/58) = 4633 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 7
  Is not unrestricted
  Is not erasable
  ATIP start of lead in:  -11597 (97:27/28)
  ATIP start of lead out: 359849 (79:59/74)
Disk type:    Short strategy type (Phthalocyanine or similar)
Manuf. index: 20
Manufacturer: Princo Corporation
Blocks total: 359849 Blocks current: 359849 Blocks remaining: 355216
Starting to write CD/DVD at speed 24 in dummy TAO mode for single session.
Last chance to quit, starting dummy write in 2 seconds.
   1 seconds.
   0 seconds.
 Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
BURN-Free is OFF.
Turning BURN-Free on
Starting new track at sector: 0
Track 01:    0 of    9 MB written.
/usr/bin/cdrecord: Input/output error. write_g1: scsi sendcmd: no error
CDB:  2A 00 00 00 00 7C 00 00 1F 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 71 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00
Sense Key: 0x5 Illegal Request, deferred error, Segment 0
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0
Sense flags: Blk 0 (not valid) 
resid: 63488
cmd finished after 0.003s timeout 40s
/usr/bin/cdrecord: The current problem looks like a buffer underrun.
/usr/bin/cdrecord: It looks like 'driveropts=burnfree' does not work for this drive.
/usr/bin/cdrecord: Please report.
/usr/bin/cdrecord: Make sure that you are root, enable DMA and check your HW/OS set up.
write track data: error after 253952 bytes
Writing  time:    6.269s
Average write speed   9.9x.
Fixating...
WARNING: Some drives don't like fixation in dummy mode.
Fixating time:    0.006s
/usr/bin/cdrecord: fifo had 68 puts and 5 gets.
/usr/bin/cdrecord: fifo was 0 times empty and 2 times full, min fill was 95%.
BURN-Free was never needed.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=0,0,0 speed=24 -tao -dummy driveropts=burnfree -eject -data /tmp/kde-papa/K3b data project.iso 

mkisofs
-----------------------
INFO: ISO-8859-1 character encoding detected by locale settings.
 Assuming ISO-8859-1 encoded filenames on source filesystem,
 use -input-charset to override.
 10.90% done, estimate finish Tue Oct  4 13:38:27 2005
 21.62% done, estimate finish Tue Oct  4 13:38:27 2005
 32.67% done, estimate finish Tue Oct  4 13:38:27 2005
 43.38% done, estimate finish Tue Oct  4 13:38:27 2005
 54.09% done, estimate finish Tue Oct  4 13:38:28 2005
 64.80% done, estimate finish Tue Oct  4 13:38:28 2005
 75.86% done, estimate finish Tue Oct  4 13:38:28 2005
 86.57% done, estimate finish Tue Oct  4 13:38:28 2005
Total translation table size: 0
Total rockridge attributes bytes: 264
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 1f000
4631 extents written (9 MB)

mkisofs comand:
-----------------------
/usr/bin/mkisofs -gui -graft-points -volid K3b data project -volset  -appid K3B THE CD KREATOR VERSION 0.11.24 (C) 2003 SEBASTIAN TRUEG AND THE K3B TEAM -publisher  -preparer K3b - Version 0.11.24 -sysid LINUX -volset-size 1 -volset-seqno 1 -sort /tmp/kde-papa/k3bUFYQNa.tmp -rational-rock -hide-list /tmp/kde-papa/k3b6iJnMb.tmp -full-iso9660-filenames -iso-level 2 -path-list /tmp/kde-papa/k3bWFaZ3b.tmp /home/papa/.kde/share/apps/k3b/temp/dummydir0/ 

```

Now I've scoured the forums looking for a solution.  Tried running as sudo, tried re-installing cdrecord, k3b, and nautilus cd-burner, tried gnomebaker, tried pulling my hair out...all to no end (yes I know the output above is from an attempt to "simulate" a burn, the errors are the same and I'm not a money machine that likes to purchase 1000's of CDRs to debug a problem).

Assistance on this would be tremendously helpful.

That being said, I do like Ubuntu (been running it exclusively for a year now) but the following things irk me:
1 - Please standardize the repositories.  Re-naming them or losing them every 6 months or so is very frustrating.  If you're going to have them, make them permanent.
2 - Stop breaking things with updates/upgrades.  Warty to Hoary killed my USB scripts and I had to reconfigure my sound to work again (thanks to the forum posters for their solutions).  Now since another update my ability to burn cds is broken!  Not to mention a broken Firefox after a recent update (fixed as well).

If the Ubuntu team intends Ubuntu to be an OS for the people, keep in mind that the people for the most part don't want to deal with problems like this.  They want an OS that just works, that's how Windows stuck around for so long.  Average Joes don't want to sift through tonnes of forums and try a hundred different dead-ends to solve the problem - if it was working before, it should work now.

I look forward to any solutions to my cd burning problem.  If I can't get it resolved I'll be putting Ubuntu behind me (as I'll apparently have to reinstall Windows in order to burn other ISOs anyways...)

-Scythe


I'm having the same problem as above. I actually discovered this problem in Debian Sarge running on my desktop, so I figured I'd try to blank a disk on my laptop running Ubuntu 5.04 and after the recent update, I get the same problem on Ubuntu as well. I tried to load scsi drivers for the burner and disabled ide-cd from the modprobe, and it will scan the burner but when you try to burn, even from commandline with cdrecord, it segfaults. Any ideas?

EDIT:

So just to detail the exact steps I've tried to troubleshoot this so far.
Running cdrecord -scanbus yields about the same error message as quoted.
So I load the SCSI driver:
modprobe -r ide-cd (since if this is loaded it won't allow ide-scsi to take control of the drive)
modprobe ide-scsi
Then cdrecord -scanbus works. I see my drive. So then I try to blank my CDRW:
cdrecord dev=0,0,0 -blank=fast
everything seems to be going ok, but then after the burn seems complete, I get:
.....
cdrecord: No such device or address. Cannot send SCSI cmd via ioctl
cdrecord: No such device or address. Cannot send SCSI cmd via ioctl
cdrecord: No such device or address. Cannot send SCSI cmd via ioctl
cdrecord: No such device or address. Cannot send SCSI cmd via ioctl
Segmentation fault

The drive does not eject or anything. Even when I try to eject via command-line it won't come out. Any ideas?

---

### Post by the_tiger on 2005-10-19
I've been using gnomebaker for burning. It seems to work fine but will never import a dvd session (and possibly cd, I haven't tried.) It gives me a similar looking error message to those earlier in the post citing the newer kernel version.

Does anybody know what the problem is, if so is there a fix.

Thank you

P.s. I am using ubuntu breezy and gnome.

---

### Post by paulvandenberg on 2005-10-19
I hate it when people say, 'Why can't Linux just work like Windows'. We need to remember that all hardware vendors test to make sure their stuff works with Windows. They don't necessarily do the same for Linux.

Paul

---

### Post by greyhound4334 on 2005-10-19
Back on topic...

I'm having the same problem. 

cdrecord -scanbus produces the same error listed by the OP.

I looked at cdrdao, as someone suggested, but it's not obvious how to translate my simple cdrecord command (e.g.)
```

cdrecord -v -pad speed=1 dev=0,0,0 kubuntu-5.10-install-i386.iso

```
into cdrdao.  I'll go off and figure that out, but I'm hoping there's some solution to getting cdrecord working again.

Is *anyone* having luck with cdrecord on breezy with KDE?

cheers,
john

---

### Post by greyhound4334 on 2005-10-19
By the way, here's a related thread.  Might help some people, but I run KDE, so not a good solution for me.

[http://ubuntuforums.org/showthread.php?t=73855&highlight=cdrecord](http://ubuntuforums.org/showthread.php?t=73855&highlight=cdrecord)

---

### Post by greyhound4334 on 2005-10-20
Here's another clue:

I found this on another thread and it *almost* worked.

I added the line hdc=ide-scsi on the kernel line of my /boot/grub/menu.lst file.  After rebooting, I did modprobe ide-scsi. Then cdrecord -scanbus worked again, and showed me the right device parameters for cdrecord.

cdrecord appeared to work normally until the end when it failed with a bunch of 
"cdrecord: No such device or address. Cannot send SCSI cmd via ioctl" messages, and finally a Segmentation fault.

Oh well, so close.  Maybe this will work for someone else.

---

### Post by TRant on 2005-10-20
Do have the same problem:
CD-Writer used to work in Hoary.
After a new install (breezy) I am not able to burn cds.

Also, my CD/DVD RW is recognized as CD RW only...

Problems are pretty much the same as Scythe describes at the beginning of the thread.

What's the problem on this? What has changed? Which packages are essentially needet ...?

Greets
TRant

---

### Post by greyhound4334 on 2005-10-20
> I added the line hdc=ide-scsi on the kernel line of my /boot/grub/menu.lst file. After rebooting, I did modprobe ide-scsi. Then cdrecord -scanbus worked again, and showed me the right device parameters for cdrecord.


Turns out this DOES appear to work.  Even though the cdrecord terminated with a bunch of errors, the CD I burned worked fine.  It was a Kubuntu Breezy installation CD, which I used successfully, so I think it was a pretty good test.  So this appears to be a workaround for the problem until cdrecord gets fixed.

---

### Post by AllenGG on 2005-10-20
Same problem, different setting.: elaborate  
1. Breezy 5.10 , GnomeBaker works fine on P4 machine. (cdrecord)
2. On my AMD64,(5.10) it "crashes" (disappears) has 'cdrecord' installed.

**workaround, [COLOR=Red]tried "Graveman" very fast and simple[/COLOR].
was trying to solve by re-installing, no luck.
Allen:cool:

---

### Post by jvictor on 2005-11-02
For me too GnomeBaker segfaults on AMD64, are we seeing a common bug in GB's AMD 64 build ? Graveman works fine

---

### Post by speckman on 2006-02-11
i too can't get my usb cd/dvd burner to burn after upgrading to hoary.  and yeah, after upgrading, some stuff broke.  some stuff got fixed though (like my dsl).  i'd like to agree with the original poster that this is really maddening.  

i spent all day yesterday trying to get Freedos to work on an old laptop.  I finally gave up and just installed MSDOS.  worked like a charm.  I guess that's why one uses commercial software.  

But I hate windows, so I hope ubuntu really does become the desktop user-orientated OS it aims to be.  just so long as i'll never have to scour these forums in 2 years trying to get my external cd burner to actually burn a cd.  (it reads them fine)  :)

thanks though, for having it work as well as it does.

---

