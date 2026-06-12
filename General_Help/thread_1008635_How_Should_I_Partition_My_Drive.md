---
title: "How Should I Partition My Drive?"
date: 2008-12-11
forum: General Help
---

### Post by Maheriano on 2008-12-11
I'm currently running off a 80 gigabyte IDE drive and a 40 gigabyte IDE drive so over Christmas I'm going to be upgrading to a 1 terabyte SATA drive. I'm just wondering how I should partition it accordingly. Here are the things I would like to do:

- run Windows XP for troubleshooting RoadRunner installs (I run RoadRunner in my car and would like to be able to get everything running on my desktop before porting it out).
- maybe run Windows Vista but not really important since I run it on my laptop already
- run Ubuntu as my main environment for daily use (doing this now)
- use Ubuntu with a media centre (MythTV or Linux MCE) to run all my media daily (MythTV needs a 64 bit operating system from what I read on the FAQ on their website)
- run ZoneMinder for home security (needs a server I think?)
- stream all my media from anywhere in the world (server?)
- be able to wipe an operating system and reinstall it in case it gets corrupted without having to first backup my personal data.

So what I see is that I need XP installed on its own partition, formatted for NTFS and Ubuntu on its own partition formatted as EXT3. But Ubuntu would have to be 64 bit to run MythTV (unless I go with LinuxMCE). But then I'd need Ubuntu Server running on its own partition as well in order to power my media streaming and ZoneMinder stuff. Plus I want to have the operaiting systems completely independent of my personal data so I'd need all my data on its own partition. AHHHHHHH! I'm freaking out! What do I do?

My other question (I've seen the thread) is whether I should even think about installing Ubuntu 64 because of lack of support (so I've heard) for it?

Hardware:
AMD Athlon 64 single core 3500+ CPU
ASUS A8N motherboard
nVidia GeForce 8400 GS video card with 256 megabyte dedicated GPU
2 gigabytes Kingston DDR400 RAM
490 watt power supply
Optoma 1690 1080i projector (no monitor at all)
80 gigabyte and 40 gigabyte IDE hard drives that I can use for whatever I want after getting the 1 terabyte drive.

---

### Post by geirha on 2008-12-11
You don't need to partition it all at once. Install one system at a time, and partition, say 20GB for each install, and leave the rest unpartitioned. Whenever you need more space for one of the OSes, make a new partition for it.

Keep in mind that a hard drive can have a maximum of 4 (primary) partitions, so after making the third partition, make the fourth an extended partition. Inside the extended partition you can have many more (logical) partitions.

Put Windows(es) on primary partitions as that will give you less problems later.

---

### Post by Maheriano on 2008-12-11
How do I partition after installing the operating system? Can that ruin any of my data?

---

### Post by Reiger on 2008-12-11
Using a partitioner [of course]. For Ubuntu there is gparted (probably among others). Windows has its own diskpart but... that's a bit of a fight.

---

### Post by M4rotku on 2008-12-11
I'm partitioning my hard drive right now.  I'm typing this from the live cd.  I've never had an error in which data was lost, but it's very important to back up just in case.

You can easily partition from the Ubuntu live cd (also the install cd) or any other live cd that has a partition editor included.

---

### Post by Maheriano on 2008-12-12
Okay so any ideas about installing 64 bit? Or if I need a server edition as well as Desktop edition? How should I eventually be partitioning it to run all this stuff?

---

### Post by geirha on 2008-12-12
The installers for each operating system will typically guide you through the partitioning. 

I doubt you'll need both the Desktop and server edition of Ubuntu btw. They use the same package repositories, and anything you can run on the server, you can run on the desktop edition. The biggest difference between the two is that the Desktop edition installs a GUI (gnome), while the server does not.

---

### Post by Maheriano on 2008-12-12
So I can host websites in the desktop edition? I forgot to mention I want to try that also, and run ZoneMinder, plus stream media like I said.

And which filesystem should I use on the data partition so I can access it via Windows or Ubuntu?

---

### Post by geirha on 2008-12-12
> **Maheriano said:**
> So I can host websites in the desktop edition? I forgot to mention I want to try that also, and run ZoneMinder, plus stream media like I said.
You can host web sites with the desktop edition, yes. Don't know what ZoneMinder is, but it should work equally well on both editions.

> **Maheriano said:**
> 
And which filesystem should I use on the data partition so I can access it via Windows or Ubuntu?

FAT32 and NTFS are supported by both systems "out of the box", but they don't support linux's ownership and permissions. In addition, only windows can fix filesystem errors on NTFS.

ext3, the default filesystem for Ubuntu, is not natively supported by Windows, but you can install a driver for it. 

I'd go for FAT32 or ext3.

---

### Post by redilyn on 2008-12-12
ext3

Windows can read ext3 after installing a driver.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Maheriano on 2008-12-12
Cool, we're getting somewhere!
So, install Ubuntu Desktop onto its own partition....about 5-10 gigs? Then install XP onto its own 10 gig partition, then copy all my data onto the larger partition after formatting it for ext3. Then look into how to set up the web service from Ubuntu Desktop as well as ZoneMinder (home security)? And then set up all my media/AC3 passthrough again as well as my Wiimote drivers, NXClient and everything else I had set up.

---

### Post by redilyn on 2008-12-12
sounds about right. 

you should create a separate home partition when you install ubuntu.

I see your talking about a terabyte drive. I would go with larger partitions for ubuntu.

15gb for / partition

20gb+ for /home partition

---

### Post by seeker5528 on 2008-12-12
I have generally done 10-12 GB for XP.

Originally during the public beta I had Vista on a 16 Gb partition, seemed like plenty if you are not installing a bunch of stuff. Did 65 Gb for the final release of Vista so I could play around with the media center stuff, turned out to be more than I needed, but I use that space from my Linux distributions too so it's not a loss.

Genrally I figure 8 to 12 Gb for my Linux distributions, but for Debian since that is where I do most of my gaming from I expanded it to 20 Gb or so.

Have 80 Gb in 2 partitions for my music, may have to do more soon since Last FM keeps recommending this good download-able stuff to me. :p

I don't keep a lot of recordings so I only have a 45 Gb partition for my Myth TV recordings. I have an HDHomerun and a WinTV PVR 250, with the settings I use on the PVR 250 it's about 4.7 Gb per hour, the unencrypted HD stuff from Comcast is somewhere right around 7 Gb per hour. 

Any disk space that is not used in the above ways is split into a couple of ext3 partition for the majority of the downloads, documents and things that I only care about having available while I'm in Linux.

Then I have a couple of partitions that are NTFS for things I want available from all my OSes.

Ran MythTV it in Debian 32 bit in the past, been running Debian 64 for a while, for the stuff that I do, I can't really tell that it makes all that much difference. But there is a benchmark [here](http://www.phoronix.com/scan.php?page=article&item=ubuntu_macosx&num=1) that pits Ubuntu against OS X and includes 32 and 64 bit results that suggest that you would probably benefit from 64 bit. If you get into the high definition thats mpeg4/h264 and/or you are transcoding the stuff you may see more benefit from it than I do.

Later, Seeker

---

### Post by Maheriano on 2009-01-02
Okay, I ordered the drive and am hoping to start this venture next weekend. Here's what I'm getting from various people I talk to including this forum:

Partition 1 for Ubuntu which will be my main operating system installed fresh from a 8.1 Live CD at about 10 gigs. I read the post about separate partitions for / and for /home but not sure why. Explain? And I also will be running a webserver on this space....I think....as I currently do from my current hard drive. Is that a good idea or should I put that on the third partition below?

Partition 2 for Windows XP at about 10 gigs. The only thing I'll be using this for is playing Day Of Defeat and testing new application builds for my carputer which runs XP.

Partition 3 will be the majority of the disk and will hold everything outside the operating system and applications for Ubuntu. It'll be mostly media and.......I can't think of anything else that'll be on it. But it'll be about 900 gigs or whatever's left over.

My last question is regarding a 60 gig IDE drive I got from my dad's 10 year old computer, should I use that for anything? Plus of course the 80 gig and 40 gig drives that are currently in my computer, both IDE. Use them?

---

### Post by Maheriano on 2009-01-14
So tell me if this is right, I installed 64 bit 8.1 last night with the following partitions:

/ = 15 gigs (ext3)
SWAP = 4 gigs
/WINDOWS = 12 gigs (FAT32)
/home = 960 gigs (ext3)

---

### Post by redilyn on 2009-01-14
Hey,

Looks good to me.

The reason you want to have a separate /home partition is so you can reinstall ubuntu or another linux distribution while keeping all your files and settings intact.

---

