---
title: "Crash problems -- help!"
date: 2005-11-30
forum: Desktop Environments
---

### Post by QuantumCaffeine on 2005-11-30
Hi all,

(The following is likely to be a bit of a long story: please bear with me!)

Last Friday, out of the blue, my computer crashed. I'd just logged in, opened up Evolution and was in the middle of reading my mail when all the windows started disappearing and the computer reset. When it started up again, it wouldn't boot fully: it got as far as trying to mount the root partition (I think: I'm still a bit of a newbie) and bombed out, eventually telling me "Target filesystem doesn't have /sbin/init". 

The preceding messages suggested I run fsck, so I booted from a live cd and tried it (or rather reiserfsck, since the partition used ReiserFS). First, I tried mounting the partition as it was, and found that quite a lot had disappeared, including my home directory. Reiserfsck told me that I had to rebuild the tree, so I did; that got everything back, though I had to search in lost+found to get it all. The disk, however, was still in too much of a mess to actually boot.

After that, I backed everything up onto an external drive, gritted my teeth and reinstalled. By early Sunday, everything was back to normal, and I relaxed. Until yesterday morning, when it happened again! This time, the windows disappeared, but left me with my desktop background and mouse pointer. Trying to shut it down, I got it as far as "Sending all active processes the TERM signal" and then it hung completely, so I wound up cutting the power. Now, if I try to boot I just get:

GRUB loading stage1.5

GRUB loading, please wait...
Error 16

...and nothing more. On the upside, however, everything else still seems to be in order: looking with the help of the live cd, with inexpert eyes, it all seems to be present and correct, so I'm assuming it's the MBR that's been affected this time.

That's how things stand: I can't boot, and don't have the skills to fix the problem (a lot of googling and head-banging yesterday has convinced me of that!). Can anybody here help?

As well as the immediate problem, having two serious crashes only days apart is a bit worrying, and I don't want to sort this out only to have another crash next week! As I said, though, I'm a bit of a newbie, so I don't really know where to start with diagnosing the problem. Is it a hardware failure, or a software problem? Where should I look?

My system is as follows:
CPU: Athlon 2100+
Memory: 512Mb
Graphics: Radeon 9600 Pro
Setup: Maxtor 160Gb ATA133 and IBM Deskstar 80Gb. Main disk has 40Gb Windows XP partition, 120Gb for Ubuntu. Second disk has 40Gb FAT32 backup area, 40Gb for an old installation of Mandrake.
Kernel:2.6.12-10-k7

Cheers, and thanks for reading this,

Peter

---

### Post by red_Marvin on 2005-11-30
Try running a live cd of some sort for a while to see if the problem is hardware
related or if the file system gets corrupted "by itself". That's all the help i can
give in this case.

---

### Post by QuantumCaffeine on 2005-11-30
[QUOTE=red_Marvin]Try running a live cd of some sort for a while to see if the problem is hardware
related or if the file system gets corrupted "by itself". That's all the help i can
give in this case.[/QUOTE]

Thanks for the tip, but I've already tried that. With the live CD, everything seems to be fine, even after a few hours' use. The other thing I don't understand is that, after the recent reinstall, everything ran fine for a couple of days before there was another crash. During those two days, I didn't install or uninstall any more software, and didn't run anything very unusual (just Evolution, Firefox and Bluefish, I think, with Folding@home plugging away in the background). 

If it was a software problem, wouldn't that show up when I installed the offending package, or soon after? On the other hand, if there's a problem with the hard disk, wouldn't it have corrupted the data as well as just the mbr? If it's neither of those, what else could it be, given that I can run perfectly happily with a Live CD?

Confused,

Peter

---

### Post by red_Marvin on 2005-11-30
1. Do you have an ATI graphics card? If yes have you run any 3d stuff?, I ask this
because I myself have had some problems with ATI+3d freezings corrupting
a) grub b) the winXP ntfs partition which wasn't even mounted. (At least I think it's
the gfx stuff, no other likely solution.)

2. Have you burned the install cd yourself? It is possible that it's some corrupted data
that keeps messing with the install. If possible, try to burn the cd again at a lower speed.
Also check the md5sum of the iso (I think it's "md5sum isofilename")

---

### Post by QuantumCaffeine on 2005-11-30
[QUOTE=red_Marvin]1. Do you have an ATI graphics card? If yes have you run any 3d stuff?, I ask this
because I myself have had some problems with ATI+3d freezings corrupting
a) grub b) the winXP ntfs partition which wasn't even mounted. (At least I think it's
the gfx stuff, no other likely solution.)

I do have an ATI card (a Radeon 9600 Pro), and am using the fglrx driver. However, I've been running Breezy since it came out with no problems, even in the Doom 3 demo (despite the fact that the Windows client used to freeze regularly). Also, I wasn't doing anything special when the crashes happened, just reading mail! That doesn't rule it out, though, so -- if I can face another reinstall -- I might stick with the plain 2D drivers for a bit and see what happens.

2. Have you burned the install cd yourself? It is possible that it's some corru'pted data
that keeps messing with the install. If possible, try to burn the cd again at a lower speed.
Also check the md5sum of the iso (I think it's "md5sum isofilename")[/QUOTE]

I did burn the install CD, but the installation that crashed last Friday dates back to the time that Breezy came out, and the new one (using the same install disk) ran fine for a couple of days before crashing. I've just checked the md5sum, and it comes out right, so I don't think there's anything wrong with the disk either.

The other thing I've been wondering about is the kernel: I only upgraded to 2.6.12-10 from 2.6.12-9 quite recently, and my processor is 3-4 years old; is it possible that the upgrade introduced some instability? If so, it must be quite an odd bug, if it allows the system to go for days before crashing badly!

I'm beginning to think that my best plan would be to reinstall (again -- gah!) and stick with the old kernel and 2D drivers. In fact, maybe it would even be worth staying with a plain vanilla out-of-the box install for a bit. If it still keels over, would it be fair to say that we can pretty much rule out software problems? (At this point, I don't really think it's a software problem, but at the same time I'd like it to be: an intermittent hardware problem on a four-year-old computer sounds like a real pain in the bank balance!)

Thanks for all your help,

Peter

---

