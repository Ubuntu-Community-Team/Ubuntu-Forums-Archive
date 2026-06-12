---
title: "What High Capacity External Hard Drives Work With Linux?"
date: 2009-06-20
forum: General Help
---

### Post by Groucho Marxist on 2009-06-20
I apologize in advance if this not the proper board to post this technological question. With that being said, I have a question regarding Ubuntu Linux and external high-capacity hard drives (i.e. 500GB to 1TB). Will Linux recognize Western Digital drives? I am currently doing research into this company and I'm still not sure if they are worth my money if I'm operating a Linux-based system.

---

### Post by ramjet_1953 on 2009-06-20
A Hard Drive is a hard drive.
Any should work OK.

I bought a regular Western Digital drive, put it in an external case that has both USB and FireWire interfaces and it worked straight-up with either interface.

I formatted the drive using the PartedMagic CD.
You can download the iso image of the CD from here:

[http://partedmagic.com/](http://partedmagic.com/)

Regards,
Roger :D

---

### Post by jimv on 2009-06-21
You cannot buy a hard drive that is too big for Linux (or Windows) to handle.  It's dependent on the file system that the OS uses, and EXT3/EXT4 in Linux can handle a drive/volume that's about 1 billion gigabytes in size.

See here for a comparison of various filesystems:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

BTW, Seagate and Western Digital are both excellent hard drive brands.

---

### Post by davidmigl on 2009-06-21
Ditto to what everyone else said. FWIW I have a Western Digital Elements 1 TB external hard drive that I purchased a few months ago and it has worked flawlessly. It has a very rugged and industrial hardware design too.

---

### Post by Bucky Ball on 2009-06-21
Not only will WD drives work fine (I have four, one external), but they are environmentally responsible and make some of the most energy efficient, environmentally friendly drives on the market. Highly recommended (WD GreenPower, 500Gb and up).

See my signature for details of building and open-source compatible, energy-efficient Ubuntu machine. :)

---

### Post by 3rdalbum on 2009-06-21
Western Digital make great drives that are reasonably priced. Well worth buying.

External hard drives and flash drives communicate with computers via the USB Mass Storage standard (UMS) and are all supported by all USB-capable operating systems.

If your computer has an eSATA port, you should look for an external HDD that also supports eSATA. You will get much superior performance because USB is much, much slower. Don't worry, most (probably all) eSATA drives have USB ports too.

---

### Post by Bucky Ball on 2009-06-21
eSATAII definitely, if you have the eSATAII port on your box. My external is USB and eSATA and using eSATA, the disk acts like it's in the box! The partitions come up almost instantaneously with switching the drive on. :)

---

### Post by blueridgedog on 2009-06-21
If the eSATA port or USB ports on your system are supported by your kernel, and you buy an external enclosure that is recognized, then any drive you use will be fine.  I have opted instead for hot swap SATA bays in my case.

---

### Post by Groucho Marxist on 2009-06-21
> **davidmigl said:**
> Ditto to what everyone else said. FWIW I have a Western Digital Elements 1 TB external hard drive that I purchased a few months ago and it has worked flawlessly. It has a very rugged and industrial hardware design too.

Thanks for the head's up on this product, davidmigl! I'm reviewing it prior to purchasing it. :D

Thank you, everyone, for the extremely helpful technological advice. I'm definitely enjoying my transition to Linux with the help of knowledgeable and courteous members like you. :)

---

### Post by blueridgedog on 2009-06-21
> **davidmigl said:**
> Ditto to what everyone else said. FWIW I have a Western Digital Elements 1 TB external hard drive that I purchased a few months ago and it has worked flawlessly. It has a very rugged and industrial hardware design too.

Do you have a link?...USB or eSATA?

---

### Post by Johnny B on 2009-06-21
i have used up to six 1.5 Tb drives (seagate and western digital) at one time without a problem.

---

### Post by KyllieKay80 on 2009-06-21
I have a Western Digital hard drive and have not had any problems

---

### Post by Groucho Marxist on 2009-06-24
My drive's arriving in the mail today and I had another question in relation to partitioning the drive. If I wanted to use this 1TB hard drive with both Windows XP and Linux, what file system would I use?

---

### Post by JohnMoore on 2009-06-24
More dittos from here.  I've used Fujitsu, WD, Seagate, and Hitachi/IBM drives with Linux, both enclosed and bare drives.  My box doesn't have an eSATA port, but USB 2.0 is fast enough for me.  My external drives are used for backups and taken off-site.  I haven't found one yet that wouldn't work, but the file system you use always has some internal size limits.

I tend to use JFS on my backup disks just because I've used it before on several OS platforms, and I've been pleased with it.  I don't use disk-spanning volumes because I don't really find that necessary, and I feel it imposes additional risks in a backup scenario.  YMMV, of course, and I know there are _many_ backup methods and schemes out there.  Mine is simple, doable, and seems reasonably robust to me.  I've never lost data or user settings in a crash since I set it up a few years ago, so please spare any flames.

Good luck!

---

### Post by 3rdalbum on 2009-06-24
> **Groucho Marxist said:**
> My drive's arriving in the mail today and I had another question in relation to partitioning the drive. If I wanted to use this 1TB hard drive with both Windows XP and Linux, what file system would I use?

Install the Ext3 driver in Windows, and you can use Ext3 as the filesystem.

Otherwise, Fat32 (vfat) is an accepted cross-platform filesystem with one gotcha: Maximum 4 gigabyte filesize limit.

Unfortunately there's not a modern cross-platform filesystem yet.

As regards eSATA, just one correction from someone else's post: eSATA is simply an extension of your computer's SATA ports, it doesn't require an extra controller. So, if your internal SATA ports work in Linux, you can use eSATA too.

---

### Post by michy99 on 2009-06-24
NTFS will get around the 4 gig file size, and is usable by linux and Windows.

---

### Post by doas777 on 2009-06-24
I have to assume that they all would be on a hardware level. the hdd has a standard bus, and so does the enclosure (usb/esata), so no, as long as the implementation of the standard is quality (don't ever buy really cheap hardware) you'll have no worries.

---

### Post by Bucky Ball on 2009-06-24
Install ntfs-3g from Synaptic Package Manager. It will be then be in one of your drop-down menus. That will deal with ntfs and that can be used by both, as mentioned.

---

### Post by blueridgedog on 2009-06-24
> **michy99 said:**
> NTFS will get around the 4 gig file size, and is usable by linux and Windows.

But..at the cost of performance.  I gave up on NTFS due to it's speed.

---

### Post by shreepads on 2010-01-13
> **blueridgedog said:**
> But..at the cost of performance.  I gave up on NTFS due to it's speed.

Also even with ntfs-3g you cannot run disk verification from within Ubuntu, need to boot into Windows and run chkdsk.

Have the same question as the original poster, although only looking for internal drives. 

Have narrowed down to two options
- Seagate Barracuda 7200.11, 1.5 TB, 3 Gbps SATA, 32 MB cache
- WD Caviar Green, 1.5 TB, 3 Gbps SATA, 64/ 32 MB cache

Which would be better? 
- Have read a posts re problems with Seagate Barracuda 7200.11, not sure if that is resolved in the latest production batches, don't want to mess around with firmware updates...
- Also read posts titled "Western Digital Does Not Support Linux" so confused...

EDIT: Using Hardy with Intel DG33FB board

---

### Post by ratcheer on 2010-01-13
I have used a 1.5 TB Seagate Freeagent Desk drive on my Linux system with no problems.

Tim

---

### Post by shreepads on 2010-01-13
> **ratcheer said:**
> I have used a 1.5 TB Seagate Freeagent Desk drive on my Linux system with no problems.

Tim

Thanks, but only interested in internal drives as mentioned!

---

### Post by Grenage on 2010-01-13
> - Have read a posts re problems with Seagate Barracuda 7200.11, not sure if that is resolved in the latest production batches, don't want to mess around with firmware updates...
- Also read posts titled "Western Digital Does Not Support Linux" so confused...

The Seagates are fine these days.  You will have no issues with either of those 1.5TB drives.

---

### Post by scouser73 on 2010-01-13
I use Maxtor External HDD's, now owned by Seagate and I've had no problem with them.  You wouldn't really encounter a problem with external drives on Linux anyway as you can format the filesystem to Ext3/Ext4 or keep it as NTFS.

---

### Post by shreepads on 2010-01-13
> **scouser73 said:**
> I use Maxtor External HDD's, now owned by Seagate and I've had no problem with them.  You wouldn't really encounter a problem with external drives on Linux anyway as you can format the filesystem to Ext3/Ext4 or keep it as NTFS.

Sorry I should have posted a new thread I guess, just noticed the title says '... External ...' while I'm only looking at the internal ones listed! :oops:

---

### Post by ratcheer on 2010-01-13
> **shreepads said:**
> Thanks, but only interested in internal drives as mentioned!

Sorry. I read the thread title and, for some reason, it says "External". I don't know why.

Tim

---

### Post by blueridgedog on 2010-01-13
> **shreepads said:**
> 
- Seagate Barracuda 7200.11, 1.5 TB, 3 Gbps SATA, 32 MB cache
- WD Caviar Green, 1.5 TB, 3 Gbps SATA, 64/ 32 MB cache


Each should work fine, as far as preference, I would look at the ratings on newegg.

---

### Post by ram2500 on 2010-01-13
I have, for the most part, done away with DVD backup methods--instead, using external HDDs for backups and using DVDs for full backups. I do know that some have software for backups on the drive--the software is for Windows and isn't really useful, which I simply deleted. I simply move my entire /home folder onto the drive, and in Windows, move my user folder onto the drive (C:\Users\username). 

Just be sure to have an optical backup, be it CDs or DVDs, or have a tape drive. Have more than one backup medium.

---

### Post by shreepads on 2010-01-14
> **ratcheer said:**
> Sorry. I read the thread title and, for some reason, it says "External". I don't know why.

Tim

Sorry my bad! Posted query on the wrong thread will make new one...

---

### Post by tobydeemer on 2010-01-21
> **blueridgedog said:**
> But..at the cost of performance.  I gave up on NTFS due to it's speed.

Oh indeed-

I have a 1 TB drive as NTFS, and one as EXT3, and the latter is worlds faster at file transfers. Both running USB, and in non-scientific "feels like" testing, EXT3 is about 25-50% faster on transfers (taking 3/4 to half as long as NTFS).

Just my .02

---

### Post by windycitybro on 2010-06-04
[SIZE=3]My first actual question here. I purchased a WD HD 250G, installed Ubuntu 9.10, but Ubuntu won't recognize HD, of course windows will. As I read the box, it said the HD was formatted for win 98, and xp. 

Q1. How can I get Ubuntu to recog. HD?
Q2. Is there a driver  I need to DL?
Q3. Is there a way to correct this from command line?[/SIZE]

***I tried to start this in new thread, sorry if this is the wrong place***

---

### Post by Bucky Ball on 2010-06-04
Take no notice of the box. They just don't put 'Linux compatible' on there but any hard drive is. It is a different prob, nothing to do with the hard drive. Wild guess? Your boot manager screwed and grub has been installed in the wrong place perhaps.

---

### Post by dcstar on 2010-06-05
> **windycitybro said:**
> My first actual question here. I purchased a WD HD 250G, installed Ubuntu 9.10, but Ubuntu won't recognize HD, of course windows will. As I read the box, it said the HD was formatted for win 98, and xp. 

Q1. How can I get Ubuntu to recog. HD?
Q2. Is there a driver  I need to DL?
Q3. Is there a way to correct this from command line?


[LIST=1]
[*]Do not post in larger fonts, you are not more important than anyone else so stop trying to attract attention.
[*]Some crappy Windows drives are configured with CD-ROM filesystems that autoload Windows software to access the drive, use gparted to write a fresh partition table to these things (wiping them totally) and then create a whole new partition on them.
[/LIST]

---

