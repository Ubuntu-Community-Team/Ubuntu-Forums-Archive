---
title: "fsck not working...?"
date: 2009-01-15
forum: General Help
---

### Post by eks on 2009-01-15
Hello,

Recently, while Ubuntu was doing a file system check, it ended up saying I should run fsck manually. After some googling I ended up booting from a Live CD and doing a fsck. The problem is, every time I run it, I get the same mistakes, even if I answer YES to the "Fix it?" questions. What gives?

This is fsck's result, which is the same every time I run it:

```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda4
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Error reading block 12875777 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes

Force rewrite<y>? yes

Directory inode 6422539, block 0, offset 0: directory corrupted
Salvage<y>? yes

Missing '.' in directory inode 6422539.
Fix<y>? yes

Setting filetype for entry '.' in ??? (6422539) to 2.
Missing '..' in directory inode 6422539.
Fix<y>? yes

Setting filetype for entry '..' in ??? (6422539) to 2.
Error reading block 12875778 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes

Force rewrite<y>? yes

Directory inode 6422541, block 0, offset 0: directory corrupted
Salvage<y>? yes

Missing '.' in directory inode 6422541.
Fix<y>? yes

Setting filetype for entry '.' in ??? (6422541) to 2.
Missing '..' in directory inode 6422541.
Fix<y>? yes

Setting filetype for entry '..' in ??? (6422541) to 2.
Error reading block 12875779 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? yes

Force rewrite<y>? yes

Directory inode 6422543, block 0, offset 0: directory corrupted
Salvage<y>? yes

Missing '.' in directory inode 6422543.
Fix<y>? yes

Setting filetype for entry '.' in ??? (6422543) to 2.
Missing '..' in directory inode 6422543.
Fix<y>? yes

Setting filetype for entry '..' in ??? (6422543) to 2.
Pass 3: Checking directory connectivity
'..' in /lely/.gconf/system/gstreamer (6422539) is <The NULL inode> (0), should be /lely/.gconf/system (6422536).
Fix<y>? yes

'..' in /lost+found/#6422541 (6422541) is <The NULL inode> (0), should be /lost+found (11).
Fix<y>? yes

'..' in /lost+found/#6422543 (6422543) is <The NULL inode> (0), should be /lost+found (11).
Fix<y>? yes

Pass 4: Checking reference counts
Inode 2 ref count is 12, should be 15.  Fix<y>? yes

Inode 11 ref count is 6, should be 4.  Fix<y>? yes

Inode 6422536 ref count is 4, should be 3.  Fix<y>? yes

Pass 5: Checking group summary information

UbuntuHome: ***** FILE SYSTEM WAS MODIFIED *****
UbuntuHome: 151571/17301504 files (13.7% non-contiguous), 21051108/34571880 blocks

```

Shouldn't fsck fix the problems and, you know, don't show them anymore? Or is this the correct procedure when you use -f?

And also, why isn't there the [-f option]("http://linux.die.net/man/8/fsck.ext3") listed on the fsck's man page?

---

### Post by Titan8990 on 2009-01-15
Try not saying "no" to "ignoring the first error?"

---

### Post by eks on 2009-01-15
> **Titan8990 said:**
> Try not saying "no" to "ignoring the first error?"

It doesn't change much:

```

ubuntu@ubuntu:~$ sudo fsck -f /dev/sda4
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Error reading block 12875777 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? no

Error reading directory block 12875777 (inode 6422539): Attempt to read block from filesystem resulted in short read
Continue<y>? yes

Directory inode 6422539, block 0, offset 0: directory corrupted
Salvage<y>? yes

Missing '.' in directory inode 6422539.
Fix<y>? yes

Setting filetype for entry '.' in Error reading block 12875777 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? no

??? (6422539) to 2.
Missing '..' in directory inode 6422539.
Fix<y>? yes

Setting filetype for entry '..' in Error reading block 12875777 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? no

??? (6422539) to 2.
Error reading block 12875778 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? no

Error reading directory block 12875778 (inode 6422541): Attempt to read block from filesystem resulted in short read
Continue<y>? yes

Directory inode 6422541, block 0, offset 0: directory corrupted
Salvage<y>? yes

Missing '.' in directory inode 6422541.
Fix<y>? yes

Setting filetype for entry '.' in Error reading block 12875778 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? no

??? (6422541) to 2.
Missing '..' in directory inode 6422541.
Fix<y>? yes

Setting filetype for entry '..' in Error reading block 12875778 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? no

??? (6422541) to 2.
Error reading block 12875779 (Attempt to read block from filesystem resulted in short read) while reading directory block.  Ignore error<y>? no

Error reading directory block 12875779 (inode 6422543): Attempt to read block from filesystem resulted in short read
Continue<y>? yes

Directory inode 6422543, block 0, offset 0: directory corrupted
Salvage<y>? yes

Missing '.' in directory inode 6422543.
Fix<y>? yes

Setting filetype for entry '.' in Error reading block 12875779 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? no

??? (6422543) to 2.
Missing '..' in directory inode 6422543.
Fix<y>? yes

Setting filetype for entry '..' in Error reading block 12875779 (Attempt to read block from filesystem resulted in short read).  Ignore error<y>? no

??? (6422543) to 2.
Pass 3: Checking directory connectivity
'..' in /lely/.gconf/system/gstreamer (6422539) is <The NULL inode> (0), should be /lely/.gconf/system (6422536).
Fix<y>? yes

'..' in /lost+found/#6422541 (6422541) is <The NULL inode> (0), should be /lost+found (11).
Fix<y>? yes

'..' in /lost+found/#6422543 (6422543) is <The NULL inode> (0), should be /lost+found (11).
Fix<y>? yes

Pass 4: Checking reference counts
Inode 2 ref count is 12, should be 15.  Fix<y>? yes

Inode 11 ref count is 6, should be 4.  Fix<y>? yes

Inode 6422536 ref count is 4, should be 3.  Fix<y>? yes

Pass 5: Checking group summary information

UbuntuHome: ***** FILE SYSTEM WAS MODIFIED *****
UbuntuHome: 151571/17301504 files (13.7% non-contiguous), 21051108/34571880 blocks
ubuntu@ubuntu:~$ 


```

---

### Post by eks on 2009-01-15
Googling for "Attempt to read block from filesystem resulted in short read" is a bit scary... But I can boot into Ubuntu... Should I worry or not...? :|

[SIZE="1"](I have to work this saturday, so I may have some free time to learn an entire new file system again only on sunday... The last one I studied was only FAT16 and 32 so many years ago.......)[/SIZE]

:(

---

### Post by Titan8990 on 2009-01-15
Personally, if you have files on there that you need, I would back them up immediately. 

Run a HDD testing tool specific to your HDD type to check if the drive is bad. If it looks good, I would reformat, reinstall, restore backups.

---

### Post by dcstar on 2009-01-15
> **Titan8990 said:**
> Personally, if you have files on there that you need, I would back them up immediately. 

Run a HDD testing tool specific to your HDD type to check if the drive is bad. If it looks good, I would reformat, reinstall, restore backups.

Agreed, it looks like a disk problem.

Installing the **smartmontools** package will allow examination of the drive to see if it has been trying to tell someone of an error.....

---

### Post by eks on 2009-01-19
Argh.... Thanks for the answers...

Well, I've installed smartmontools and am running smartctl -t long now, as suggested the man page. Will be also running Ubuntu with smartd and smart-notifier, to try to delay the reformat until 9.04 is out...

But I don't get it, what's the difference between smartctl and fsck?

```

DESCRIPTION
       fsck is used to check and optionally repair one or more Linux file systems.  filesys can be a device name (e.g.
       /dev/hdc1, /dev/sdb2), a mount point (e.g.  /,  /usr,  /home),  or  an  ext2  label  or  UUID  specifier  (e.g.
       UUID=8868abf6-88c5-4a83-98b8-bfc24057f7bd  or  LABEL=root).   Normally,  the  fsck  program  will try to handle
       filesystems on different physical disk drives in parallel to reduce the total amount of time  needed  to  check
       all of the filesystems.

```

```

DESCRIPTION
       smartctl  controls  the Self-Monitoring, Analysis and Reporting Technology (SMART) system built into many ATA-3
       and later ATA, IDE and SCSI-3 hard drives. The purpose of SMART is to monitor the reliability of the hard drive
       and  predict drive failures, and to carry out different types of drive self-tests.  This version of smartctl is
       compatible with ATA/ATAPI-7 and earlier standards (see REFERENCES below)

```

I understand what's written there, and what SMART is. But why didn't running fsck from a Live CD marked the bad blocks as bad?

I've read somewhere, and on the [fsck man page]("http://linux.die.net/man/8/fsck"), I should run it at run-level 1 (single user mode), but how I do that with a Live CD??

---

### Post by albinootje on 2009-01-19
> **eks said:**
> 
But I don't get it, what's the difference between smartctl and fsck?

fsck is only about doing a file system check (software), while smartctl can test the physical state of your hard disk.
> 
But why didn't running fsck from a Live CD marked the bad blocks as bad?

Who talked about bad blocks ?
Use the command badblocks to check for bad blocks
```

man badblocks

```
> 
I've read somewhere, and on the [fsck man page]("http://linux.die.net/man/8/fsck"), I should run it at run-level 1 (single user mode), but how I do that with a Live CD??

With a Live CD you will have the same effect basically, no worries.

P.s. I don't see any reason to come to the immediate conclusion that your hard disk is broken, it is still possible that only the file system is messed up.
Smartmontools and the badblocks tool can tell you more.

---

### Post by eks on 2009-01-19
> **albinootje said:**
> 
```

man badblocks

```

Thanks! I think that's what I was looking for.

Anyway, smartctl -d result was:

```

~$ sudo smartctl -l selftest /dev/sdb4
smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is http://smartmontools.sourceforge.net/

=== START OF READ SMART DATA SECTION ===
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: read failure       90%      6956         139007906

```

Let's see what I can do with badblocks.

---

### Post by Titan8990 on 2009-01-19
That last log shows a failed SMART test. While SMART is not perfect, it is typically a red flag that your drive is bad.

---

### Post by eks on 2009-01-19
I think **e2fsck -c** is what I was looking for since the begging, but I was reading only fsck man page. ](*,)

I will be running it tomorrow, after backing up.

> **Titan8990 said:**
> That last log shows a failed SMART test. While SMART is not perfect, it is typically a red flag that your drive is bad.

Indeed. I just checked on Western Digital website and the hard disk warranty expires on March 2010... I may as well try to replace it...

---

### Post by albinootje on 2009-01-19
> **eks said:**
> I think **e2fsck -c** is what I was looking for since the begging, but I was reading only fsck man page. ](*,)

I will be running it tomorrow, after backing up.


How are you gonna do the backup ? dd or partimage or .. ?
> 
Indeed. I just checked on Western Digital website and the hard disk warranty expires on March 2010... I may as well try to replace it...

You ran the smartctl test on /dev/sdb4 ?
Why not the whole disk ?

And I don't know the selftest command of smartctl, I normally use smartctl like this :
```

sudo smartctl -s on --test=long /dev/sdb

```
and when the test is ready after the estimated amount of time :
```

sudo smartctl -H /dev/sdb

```

---

### Post by albinootje on 2009-01-19
And there's also a GUI for smartmontools :)
[http://gsmartcontrol.berlios.de/home/index.php/en/Screenshots](http://gsmartcontrol.berlios.de/home/index.php/en/Screenshots)

---

### Post by sempronius on 2009-01-23
eks, did you (recently or anytime before) make an image of your linux partition with Norton Ghost and restored it?

This "setting filetype for entry..." is a message I so far only got when I restored a Norton Ghost image of my linux system.


Just an idea
sempronius

---

### Post by eks on 2009-01-24
> **albinootje said:**
> How are you gonna do the backup ? dd or partimage or .. ?
I just copied some files I was working on to an external hard disk. I wouldn't bother much losing my /home because I'm almost monthly changing themes and desktop looks. That's why I'm trying to just mark the blocks as bad and keep using this disk until 9.04 gets out.

[quote=sempronius]eks, did you (recently or anytime before) make an image of your linux partition with Norton Ghost and restored it?[/quote]
No, it wasn't, never used Norton Ghost. According to my wife, it was probably "cat related", he accidently (or not...) turned off the power source when she was downloading videos. Or the disk is "just bad".

Either way, I've used e2fsck -c more than 4 times already, and also with -c and -k, and it always seems to be marking the same blocks again. Also fsck during boot time fails, saying I should run it manually to correct (and mark?) the bad blocks.

The -c option runs the badblocks command before normal e2fsck, so it add to inodes the blocks that are bad. The -k option just jumps the blocks that are already bad. So it **SEEMS** the bad blocks are not being added to the inodes.

What am I doing wrong?

---

### Post by albinootje on 2009-01-24
> **eks said:**
>  So it **SEEMS** the bad blocks are not being added to the inodes.

Perhaps the comments on this webpage are useful :
[http://brainstorm.ubuntu.com/idea/6972/](http://brainstorm.ubuntu.com/idea/6972/)

---

### Post by gjoellee on 2009-01-24
You should take a look at what options you have with fsck. ```
man fsck
``` it might solve your problem

---

### Post by eks on 2009-01-25
> **gjoellee said:**
> You should take a look at what options you have with fsck. ```
man fsck
``` it might solve your problem
It was actually one of my problems to look at, and *post a quote of*, the man page of fsck, instead of the man page of e2fsck. fsck does not say anything about -c, which adds badblocks check to the file system check.

But since I had nothing to loose, I've tried to do a read-write non-destructive test, with the **-cc option**, and it seems to have finally marked down the badblocks on the inodes. Dunno why the read test seemed to be showing up errors but not marking them on the inodes. The problem is that the -cc option is "hidden" in one phrase of the e2fsck man page. It could have been easier to find that...

Anyway, thanks for all the help!!

---

### Post by eks on 2009-01-25
Btw, albinootje, the GUI for smartmontools, gsmartcontrols, is really great!!

It's still giving errors, so I will try to change the hard disk with Western Digital. But now I can do that without rushing. :)

Thanks again!

---

### Post by dcstar on 2009-01-25
> **eks said:**
> 
........ Dunno why the read test seemed to be showing up errors but not marking them on the inodes. The problem is that the -cc option is "hidden" in one phrase of the e2fsck man page. **It could have been easier to find that**...


A lot of these things can only temporally mask the symptoms of an underlying problem - like the bad blocks on the disk which will likely increase - so they aren't advertised as any sort of effective cure which running fsck normally on good hardware is.

Having them used in "normal" circumstances can give people a false sense of security that their problem is cured, when in fact it probably isn't (as the smarttools has showed you).

---

