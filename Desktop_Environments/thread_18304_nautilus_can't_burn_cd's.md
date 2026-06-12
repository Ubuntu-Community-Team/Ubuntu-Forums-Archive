---
title: "nautilus can't burn cd's"
date: 2005-03-05
forum: Desktop Environments
---

### Post by arbeck on 2005-03-05
Nautilus doesn't seem to have the ability to burn cd's for me.  cdrecord, cdrdao, and gnomebaker all work just fine.  But nautilus prompts me to insert a blank cd and will not record.  Any ideas?

---

### Post by kassetra on 2005-03-06
[QUOTE=arbeck]Nautilus doesn't seem to have the ability to burn cd's for me. cdrecord, cdrdao, and gnomebaker all work just fine. But nautilus prompts me to insert a blank cd and will not record. Any ideas?[/QUOTE]

I have some ideas, so let's try some easy suggestions first:
1. Go to Applications->System Tools->Configuration Editor.
 2. In the tree listing on the left, go to apps->nautilus-cd-burner.
3. Click on the little square to the right of "Burnproof" to turn it on.
 4. You might want to change default_speed to 4 (I know it's a low number, but it's a good test.)  
5. Click somewhere else to "set" your changes.
6. Close the editor (no need to save, it saves when you "set" the changes).
7. Try to burn with nautilus again.

---

### Post by LongTooth on 2005-03-06
Kessetra, I gave you suggestion a try. No go. I still get the error message to insert a CD just like arbeck. Any more tip? I'm hurting with some kind of CD burner. I did have XCDRoast on my Warty system. But I found it too cumbersom to use. I heard Graveman and GnomeToast is in the works. Hope to see one of those on Hoary when it's finalized. Thanks.

---

### Post by bored2k on 2005-03-06
[QUOTE=LongTooth]Kessetra, I gave you suggestion a try. No go. I still get the error message to insert a CD just like arbeck. Any more tip? I'm hurting with some kind of CD burner. I did have XCDRoast on my Warty system. But I found it too cumbersom to use. I heard Graveman and GnomeToast is in the works. Hope to see one of those on Hoary when it's finalized. Thanks.[/QUOTE]
 what is wrong with gnome baker ?? if ur a non gnome purist [not like me] u can try k3b

---

### Post by lordofkhemenu on 2005-03-06
[QUOTE=bored2k]what is wrong with gnome baker ?? if ur a non gnome purist [not like me] u can try k3b[/QUOTE]
Install [graveman](http://graveman.tuxfamily.org/index-e.php). The repositories just got updated with the latest version. Has as much functionality as k3b and is easy to use.

---

### Post by LongTooth on 2005-03-06
Well, some 30 mins after I posted my remarks I came across GnomeBaker. I've installed it. This just might be what I"m looking for. So far I've been able to blank a CDRW but I can't seem to burn an ISO. More digging to do. I'll check out Graveman too. Thanks.

---

### Post by burlap on 2005-03-06
I have this problem with cd-rw only. Cd-rs work fine with nautilus. Gnomebaker did write cd-rw, but did not erase. Xcdroast (which is cdrecord) and command line (cdrdao to blank) work without problems. 

I am tired of new burning software, so I am probably not going to try graveman...

---

### Post by poofyhairguy on 2005-03-06
[QUOTE=burlap]
I am tired of new burning software, so I am probably not going to try graveman...[/QUOTE]

I don't get it. Why not just use K3B? Its like the best burining program EVER. I made a howto in the WIKI.

Quit hurting yourself!

---

### Post by lordofkhemenu on 2005-03-06
[QUOTE=burlap]I have this problem with cd-rw only. Cd-rs work fine with nautilus. Gnomebaker did write cd-rw, but did not erase. Xcdroast (which is cdrecord) and command line (cdrdao to blank) work without problems. 

I am tired of new burning software, so I am probably not going to try graveman...[/QUOTE]
That's a shame, because graveman has the option to erase cdrw...

---

### Post by burlap on 2005-03-06
So I feel it is necessary to explain why I do not want to try new software:

1. New repository. 
2. Dependencies. 
(3. Compilation.)
4. Lack of desired functionality. 

As for graveman:

I got 0.2 (I added grawert repository for Ubuntu Warty). I knew that if there is 0.3.8, 0.2 is probably useless. And so it was.  It didn't even find my cd-recorder (even if it is the only cd drive I have). No option to erase cd-rw at all. 

Just to be sure I have tried graveman for Hoary - results as expected: lots of unmet dependencies. 

Why not to compile? 
I want to retain control over my packages via apt and reduce to absolute minimum the number of packages that are installed "locally". 

(However I've finally compiled and installed 0.3.8. Cd-rw erasing does not work either. It seems that it's cdrecord problem. Cdrdao used from command line works.)

Why not to use k3b?
KDE-free desktop (I didn't like k3b anyway when I used non-kde-free desktop).

---

### Post by LongTooth on 2005-03-06
Well, I did it. I burned a downloaded ISO file using GnomeBaker. Sometime ago I purchased a five pack of CD-RW disks because I got tired of making coaster out of the CD disks. And is it possible to blank CD-RW using GnomeBaker. I've done it several times and I just installed GnomeBaker last night. Haven't tried audio coping yet but if I can burn ISO files on to a CD-RW disk - that I blanked using this program - copying of music shouldn't be a problem Via! GnomeBaker.

---

### Post by burlap on 2005-03-06
This is what I get whatever cdrecord-based program I use to erase cd-rw (also gnomebaker and graveman). Minimal doesn't work, it suggests to use full mode. Output for the full mode (in this case it is gnomebaker):
```
cdrecord: Operation not permitted. WARNING: Cannot set RR-scheduler
cdrecord: Permission denied. WARNING: Cannot set priority using setpriority().
cdrecord: WARNING: This causes a high risk for buffer underruns.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
cdrecord: Warning: using unofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c	1.90 04/01/14 Copyright 1988,1995,2000-2004 J. Schilling').
SCSI buffer size: 64512
Cdrecord-Clone 2.01a29 (i686-pc-linux-gnu) Copyright (C) 1995-2004 J rg Schilling
NOTE: this version of cdrecord is an unofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
Using libscg version 'ubuntu-0.8ubuntu1'.
atapi: 1
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'QSI     '
Identifikation : 'CDRW/DVD SBW-241'
Revision       : 'VX09'
Device seems to be: Generic mmc2 DVD-ROM.
Current: 0x000A
Profile: 0x0010 
Profile: 0x0008 
Profile: 0x0009 
Profile: 0x000A (current)
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-2 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 2
  Reference speed: 6
  Is not unrestricted
  Is erasable
  Disk sub type: High speed Rewritable (CAV) media (1)
  ATIP start of lead in:  -12900 (97:10/00)
  ATIP start of lead out: 359849 (79:59/74)
  1T speed low:  4 1T speed high: 10
  2T speed low:  4 2T speed high:  0 (reserved val  6)
  power mult factor: 1 5
  recommended erase/write power: 5
  A1 values: 24 1A D8
  A2 values: 26 B2 48
Disk type:    unknown dye (reserved id code)
Manuf. index: -1
Manufacturer: unknown (not in table)
Manufacturer is unknown because of the orange forum embargo.
As the orange forum likes to get money for recent information,
it may be that this media does not use illegal manufacturer coding.
Starting to write CD/DVD at speed 10 in real BLANK mode for single session.
Last chance to quit, starting real write in 2 seconds.   1 seconds. 0 seconds. Operation starts.
Performing OPC...
Blanking entire disk
cdrecord: Success. blank unit: scsi sendcmd: no error
CDB:  A1 00 00 00 00 00 00 00 00 00 00 00
status: 0x2 (CHECK CONDITION)
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 24 00 00 00
Sense Key: 0x5 Illegal Request, Segment 0
Sense Code: 0x24 Qual 0x00 (invalid field in cdb) Fru 0x0
Sense flags: Blk 0 (not valid) 
cmd finished after 0.000s timeout 9600s
cdrecord: Cannot blank disk, aborting.

```

---

### Post by William the Conquerer on 2005-03-09
burlap, I am having this EXACT same problem...  I hope someone has a solution to this issue...

---

### Post by burlap on 2005-03-10
> burlap, I am having this EXACT same problem... I hope someone has a solution to this issue... 

I have filed it as bugs #169040 at Gnome and #7382 at Ubuntu. At Gnome I got an answer that it is a cdrecord problem, not nautilus (sounds reasonable). Take a look at the bugs (especially the Ubuntu one) and check if there is anything you can add. I hope the solution won't be "switch to Hoary" (well, I'm going to do it anyway when it gets "stable").

---

