---
title: "DVD and CD burning problem!"
date: 2005-04-07
forum: Desktop Environments
---

### Post by ak70 on 2005-04-07
It semms that on my system, all burning software can not use cache when I burn DVDs!!! It is extremely slow! And I can not burn CDs du to this problem!


cdrecord
-----------------------
Cdrecord-Clone 2.01a38 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
Driveropts: 'burnfree'
/usr/bin/cdrecord: Warning: Running on Linux-2.6.11-mm4
/usr/bin/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdc'
devname: '/dev/hdc'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
/usr/bin/cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c 1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
/usr/bin/cdrecord: Cannot allocate memory. Cannot get SCSI I/O buffer.

cdrecord comand:
-----------------------
/usr/bin/cdrecord.mmap -v gracetime=2 dev=/dev/hdc speed=4 -tao driveropts=burnfree -eject -data /other/ak70/Matlab_R14_Mac.Linux.Unix_CD1.iso

---

### Post by Bob D. on 2005-04-07
Well, you're not alone here with this issue.

I've filed bug #12377 ([http://savannah.nongnu.org/bugs/?func=detailitem&item_id=12377](http://savannah.nongnu.org/bugs/?func=detailitem&item_id=12377)) against graveman! (which uses cdrecord) for this exact problem. Graveman only detects ~64k of buffer when my Pioneer DVR-109 has 2MB. Graveman will also only allow my DVD burner to burn a CD-R at 4x speed, not the 40x speed it is capable of doing.

It's not a DMA issue as you can see in the bug I filed that DMA is active for this drive.

I also have a copy of NeroLINUX and it has no problems burning CD-R's at 40x speed and properly detects my buffer cache as 2MB.

Don't know where this problem lies, but hopefully some more knowledgeable users will jump in and give us some ideas.

Bob

---

### Post by kassetra on 2005-09-01
cdrecord is only used for creating a CD - creating a dvd happens with growisofs, usually.

bob d.: The Pioneer DVR-109 has a firmware incompatibility with growisofs that prevents it from burning certain DVD media correctly - most likely, this same firmware issue causes cdrecord to have difficulties as well.  

You *can* upgrade the firmware of a pioneer drive - but it doesn't completely fix the problem. After upgrading the firmware (which is a very ugly process) - it still might not be fixed completely (for me, I can burn dvds only from the command line, but at least I can burn them. cds... that's hit or miss... sometimes it's fine, othertimes it doesn't work.)

ak70: cdrecord can be somewhat tempermental on systems with a kernel greater than 2.4. For some people, it works flawlessly - for other people, it has huge issues (depending on the exact kernel, cd drive, libraries, etc.)

---

### Post by Bob D. on 2005-09-02
kassetra, you rock!  Thanks for clearing up this weird problem. Really nice of you to post back to this stale thread.

Sucks the DVR-109 has a firmware problem with cdrecord/growisofs. I was just about to try K3B, but since it uses the same cli tools I expected the same results.

And yes, NEROLinux does work just fine [I've been using it instead of a GNU tool :-|   ]; it's what I've been using since I made my post back in April.

Cheers!

Bob

---

### Post by kassetra on 2005-09-02
[QUOTE=Bob D.]kassetra, you rock! Thanks for clearing up this weird problem. Really nice of you to post back to this stale thread.

Sucks the DVR-109 has a firmware problem with cdrecord/growisofs. I was just about to try K3B, but since it uses the same cli tools I expected the same results.

And yes, NEROLinux does work just fine [I've been using it instead of a GNU tool :-|   ]; it's what I've been using since I made my post back in April.

Cheers!

Bob[/QUOTE]

LOL I rock somedays.  Other days, I roll.  ;)  Yeah, NEROLinux would most likely not have any issues burning because it uses it's own proprietary tools to burn with.

Firmware upgrade 1.58 to the dvr-109 was *supposed* to fix this issue with growisofs, but it still has issues in most of the guis available to burn with.  I'm going to be talking with a dvd/cd burning application's author to see if we can work around this issue, or at least, allow for some more "advanced" options in the gui - so that if this happens with other drives, we'll still be able to use the burner and a gui.

---

### Post by trash on 2005-09-02
[QUOTE=kassetra]cdrecord is only used for creating a CD - creating a dvd happens with growisofs, usually.

bob d.: The Pioneer DVR-109 has a firmware incompatibility with growisofs that prevents it from burning certain DVD media correctly - most likely, this same firmware issue causes cdrecord to have difficulties as well.  

You *can* upgrade the firmware of a pioneer drive - but it doesn't completely fix the problem. After upgrading the firmware (which is a very ugly process) - it still might not be fixed completely (for me, I can burn dvds only from the command line, but at least I can burn them. cds... that's hit or miss... sometimes it's fine, othertimes it doesn't work.)

ak70: cdrecord can be somewhat tempermental on systems with a kernel greater than 2.4. For some people, it works flawlessly - for other people, it has huge issues (depending on the exact kernel, cd drive, libraries, etc.)[/QUOTE]

I'm assuming yes but can you confirm if it's the same firmware issue as DVR-105?
I read your other post on firmware upgrade and I ain't going there thats for sure! scary stuff lol.

thanks.

---

### Post by kassetra on 2005-09-02
[QUOTE=trash]I'm assuming yes but can you confirm if it's the same firmware issue as DVR-105?
I read your other post on firmware upgrade and I ain't going there thats for sure! scary stuff lol.

thanks.[/QUOTE]

hmmm.  let me look some more into the 105 - but here's a key flag: if, when you burn a DVD+R - you get something very close to the following error - 
```
:-[ CLOSE SESSION failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
``` it most likely is the same issue.  You can even double check to see if the disc still is waiting for a "close" command by typing:
 ```
dvd+rw-mediainfo /dev/hdX
``` (where X is your drive specification)

Firmware upgrades are for 1. expert users (and even then it's not guaranteed) or 2. people with about $50 to burn... or both.  I've successfully flashed this drive, but, it's a heart-stopping process.

---

### Post by trash on 2005-09-02
[QUOTE=kassetra]hmmm.  let me look some more into the 105 - but here's a key flag: if, when you burn a DVD+R - you get something very close to the following error - 
```
:-[ CLOSE SESSION failed with SK=2h/ASC=04h/ACQ=07h]: Resource temporarily unavailable
``` it most likely is the same issue.  You can even double check to see if the disc still is waiting for a "close" command by typing:
 ```
dvd+rw-mediainfo /dev/hdX
``` (where X is your drive specification)

Firmware upgrades are for 1. expert users (and even then it's not guaranteed) or 2. people with about $50 to burn... or both.  I've successfully flashed this drive, but, it's a heart-stopping process.[/QUOTE]


Well first off thanks for your help! no need to look any further , it's NOT A PROBLEM IN BREEZY :), using Gnomebaker!

Executing 'mkisofs -V movies -p ken -iso-level 3 -l -R -hide-rr-moved -J -joliet-long -gui -graft-points...
... builtin_dd of=/dev/sr0 obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
/dev/sr0: engaging DVD-RW DAO upon user request...
/dev/sr0: reserving 1850320 blocks
/dev/sr0: "Current Write Speed" is 2.0x1385KBps.
  0.03% done, estimate finish Fri Sep  2 23:47:02 2005
  0.05% done, estimate finish Sat Sep  3 18:43:44 2005
...
99.93% done, estimate finish Fri Sep  2 20:08:31 2005
 99.96% done, estimate finish Fri Sep  2 20:08:32 2005
 99.98% done, estimate finish Fri Sep  2 20:08:32 2005
Total translation table size: 0
Total rockridge attributes bytes: 906
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
1850311 extents written (3613 MB)
/dev/sr0: flushing cache
Completed

EDIT:
just want to add that i'm using breezy on my g4 but probably will be same for x86'rs... also that my setup is exactly the same as was in Hoary where i could not burn dvd... YAY for breezy! :)

---

### Post by kassetra on 2005-09-02
[QUOTE=trash]
Total translation table size: 0
Total rockridge attributes bytes: 906
Total directory bytes: 0
Path table size(bytes): 10
Max brk space used 21000
1850311 extents written (3613 MB)
/dev/sr0: flushing cache
Completed

EDIT:
just want to add that i'm using breezy on my g4 but probably will be same for x86'rs... also that my setup is exactly the same as was in Hoary where i could not burn dvd... YAY for breezy! :)[/QUOTE]

Ahhhhh good.  There was a somewhat klunky patch written for growisofs - and I see it made it into the dvd+rw-tools for breezy - which means that dvr-109 sufferers will be fine in breezy (if the tools stay as-is.)

---

