---
title: "Resizing NTFS with bad sectors"
date: 2009-02-14
forum: General Help
---

### Post by SlalomMan on 2009-02-14
I'm trying to resize a Windows XP NTFS partition on my brother's laptop; I eagerly started up the Ubuntu LiveCD and ran GParted. However, I was discouraged to find out that GParted simply would not touch the partition because it has bad sectors. I'm not sure how these got there, but they're stopping GParted from doing what it does best. I booted the XP cd and ran chkdsk /r multiple times; Windows says it fixed the errors or found none. But GParted is still complaining about the bad sectors. If there was a way to make GParted ignore these, it would be great.

My next step was to try ntfsresize. I realize this is a bit more risky than using something like GParted, but I consider myself at least kind of handy with linux so I figured I'd give it a shot. First I ran a dry test of the resize.
```
$ sudo ntfsresize --bad-sectors --no-action  --size 65000M /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 113607528960 bytes (113608 MB)
Current device size: 113607535104 bytes (113608 MB)
New volume size    : 64999993856 bytes (65000 MB)
WARNING: This software has detected that the disk has at least 8 bad sectors.
WARNING: Bad sectors can cause reliability problems and massive data loss!!!
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 42059 MB (37.0%)
Collecting resizing constraints ...
Needed relocations : 4527988 (18547 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.
```

I figured since that worked, maybe I could get around the bad sectors because they shouldn't hurt if they're just avoided, or so I've read, right?

Then I tried a real resize.
```
$ sudo ntfsresize -bfvs 65000M /dev/sda1
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/sda1
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 113607528960 bytes (113608 MB)
Current device size: 113607535104 bytes (113608 MB)
New volume size    : 64999993856 bytes (65000 MB)
Checking for bad sectors ...
Bad cluster: 0x129eb38 - 0x129eb38    (1)
Bad cluster: 0x129f67b - 0x129f67b    (1)
Bad cluster: 0x129f73a - 0x129f73a    (1)
Bad cluster: 0x129f799 - 0x129f799    (1)
Bad cluster: 0x129f857 - 0x129f857    (1)
Bad cluster: 0x12a012d - 0x12a012d    (1)
Bad cluster: 0x12a0166 - 0x12a0166    (1)
Bad cluster: 0x12a0a3c - 0x12a0a3c    (1)
WARNING: This software has detected that the disk has at least 8 bad sectors.
WARNING: Bad sectors can cause reliability problems and massive data loss!!!
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 42059 MB (37.0%)
Collecting resizing constraints ...
Needed relocations : 4527988 (18547 MB)
WARNING: Every sanity check passed and only the dangerous operations left.
Make sure that important data has been backed up! Power outage or computer
crash may result major data loss!
Are you sure you want to proceed (y/[n])? y
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Relocate record   15305:0x80:00000016:0x00000000:0x013b75de --> 0x0000d470
Relocate record   15305:0x80:00000032:0x00000010:0x013b709b --> 0x0000d480
Relocate record   15305:0x80:00000065:0x00000030:0x013c3042 --> 0x0000d4a0
Relocate record   15305:0x80:00000153:0x00000071:0x01468965 --> 0x0000d4e1
Relocate record   15305:0x80:00000260:0x000001f0:0x012b750b --> 0x0000d57a
Relocate record   15305:0x80:00000118:0x000003fd:0x0129f605 --> 0x0000d67e
Relocate record   15305:0x80:00000001:0x00000473:0x0129f860 --> 0x0000d6f4
Relocate record   15305:0x80:00000124:0x00000474:0x0129f67c --> 0x0000d6f5
ERROR(5): Failed to read from the disk: Input/output error
****************************************************************************
* WARNING: The disk has bad sector. This means physical damage on the disk *
* surface caused by deterioration, manufacturing faults or other reason.   *
* The reliability of the disk may stay stable or degrade fast. We suggest  *
* making a full backup urgently by running 'ntfsclone --rescue ...' then   *
* run 'chkdsk /f /r' on Windows and rebooot it TWICE! Then you can resize  *
* NTFS safely by additionally using the --bad-sectors option of ntfsresize.*
****************************************************************************
```

That's the same error I get in GParted. I've ran chkdsk multiple times, but I can't reboot into windows twice, like it says, unless I boot into safe mode. I'm not sure if that changes anything.

So is there any way to either make NTFSResize or Gparted resize this partition? Or am I stuck with how it is right now?

Thanks in advance.

EDIT: I ended up backing his data up on a DVD, CD, and putting a few files on his Ubuntu partition, then deleting the old NTFS and splitting it into the two XP and Windows 7 partitions. I guess I'll mark it as solved.

---

### Post by black drongo on 2009-03-02
have u tried testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) or ultimate boot cd?

---

