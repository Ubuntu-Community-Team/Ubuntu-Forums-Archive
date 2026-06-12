---
title: "root directory inode = bad block"
date: 2009-04-27
forum: General Help
---

### Post by hdd.slayer on 2009-04-27
Hi

For all my years using computers I've been plagued by HDD failures. I've lost 8 of 15 HDDs (or partitions on said HDDs) within 2 years, and often had data loss with the others.

My current problem is, while waiting for my replacement 1T HDD to come so I could copy my backup files to it, my backup HDD (WD 500GB) has lost the 280GB ext3 backup partition.

This happened after ubuntu (8.10) asked if I wanted to delete my trash on my backup partition before shutdown (I can't remember the exact wording), which I said yes to, although I had just had problems copying files to it. When I next booted up I couldn't mount the partition, it couldn't detect the partiton type. (My ubuntu partition on the same disk still works).

I've now managed to get a dd image (280GB) of the partition on my replacement HDD which came today, so most of the data is readable.
NOTE: I'm using the 9.04 (jaunty) CD so that I can keep the whole problem drive unmounted.

I used testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) to find a backup superblock, and ran e2fsck on the bad partition using -b 98304 (the 1st backup superblock). e2fsck found a number of bad blocks in use:
Block 4 in the primary group descriptors is on the bad block list

If the block is really bad, the filesystem can not be fixed.
You can clear the this block from the bad block list and hope that block is really OK, but there are no guarantees.
(copied from searched site since terminal is closed)
[http://lkml.org/lkml/1997/7/9/54](http://lkml.org/lkml/1997/7/9/54)

I'm guessing my root inode is dead, wiped out as a bad block.

What I want to know is, shouldn't it be possible to do something like:
Search all the inodes on the drive to find user-specified directories by name, or by the names of their subdirectories, and then place those in a recovery root directory so that the user can copy out the files.

Does anyone know or have experience with recovery of this type (dead inodes).
Can anyone recommend recovery software for this type of problem?




ALSO: I suppose I should also be asking if anyone might have an idea as to why I'm so lethal to HDDs and partitions.

Here's a not-too-brief (sorry) overview of me & HDDs.

I build my systems myself, usually using stock standard components (usually gigabyte mobos, intel or AMD, usually NVidia gfx, usually nothing else). I've been building my own PCs since 1998. I'd consider myself very familiar with the process.

The HDDs have all been Seagate, Western Digital, Samsung and Maxtor, and I've had complete failures with each. Mostly I've been OK data-wise with backups.

I switched from primarily Windows to primarily Ubuntu around 2006, with no change to the crash rate. I've used (and had crashes with) Fat32, NTFS, ext2 and ext3. 

Current setup (fairly typical) - same setup during the recent lost HDD and partition:
HDDs: 2xSATA (1TB Seagate that died, 500G WD with bad partition, new 1G WD)
Video: GeForce 9600
Mobo: Gigabyte GA-EP35-DS3
CPU: Intel Core2 Duo E8200
Stock SATA DVD-RW, can't remember or see brand.
PSU: 420W Thermal Master TM-420-PMSR (came with the case).
Everything else is USB and either low-power or self-powered.
OS: Intrepid Ibex 8.10.
Bootloader: GRUB (from ibex install, untouched by me).

HDDs are usually warmish to touch when in use, I'm guessing around 40 degrees. Never cooking. They're always horizontal and right-way-up.
I don't overclock, CPU + GFX usually run very cool with stock coolers.
Usually a few case fans. I do seem to run it side-less quite often tho, as I'm always having to juggle live and dead HDDs to copy to keep (and use) backups.

Typically I have 3-6 partitions on a drive - different OSes, music, movies, coding and projects, software and misc, swap, boot, etc.

I tend to do a lot of file transfers (10s-100s of Gigs / month), mainly due to backups. 10000s of files too since I build lots from source code and keep extra (3-4) backups of my code directories. There's also lots of file-exchanges with flatmates, eg playing music or movies over the network.

My PC's turned off most nights, but occasionally gets left on.



Is it likely that power is an issue? I'm in NZ, not in an apartment. 
Any other ideas?
Or does it sound like I've just been hideously unlucky, perhaps due to my far-higher-than-average usage level.
Or perhaps I'm just energistically posessed :) (peter.f.hamilton ref)


Anyway, thanks for all tips and advice.
Sorry for being so wordy but it often saves time on the responses.

---

### Post by hdd.slayer on 2009-04-27
Using forensic software I was able to recover many files, without their filenames or directory structure.

This isn't really that helpful to me, but it proves the data is still there, intact.
All I need is access to the outermost directory nodes since the root node is dead.

Anyone have any ideas?
Thanks for all help.

---

