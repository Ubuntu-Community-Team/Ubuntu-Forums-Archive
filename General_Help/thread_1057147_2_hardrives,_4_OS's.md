---
title: "2 hardrives, 4 OS's??"
date: 2009-02-01
forum: General Help
---

### Post by Wickd on 2009-02-01
Hi there

I have a couple of questions. I have recently acquired an aditional hd (250 GB). I need to boot the following four operating systems for testing purposes

1) Ubuntu Linux (Primary OS)
2) Windows 7 Beta
3) Windows XP
4) FreeBSD

We are piloting windows 7 automation in South Africa and I want to learn the OS ASAP.

I currently only use the one hd for Ubuntu only

I would like to setup it in the following way:

**hd0** (250GB):

Partition 1: Ubuntu Intrepid (ext3)
Size: 40 GB

Partition 2: Windows 7  (ntfs)
Size: 40 GB

Partition 3: Windows XP (ntfs)
Size: 40 GB

Partition 4: FreeBSD (not sure of file structure)
Size: 40 GB

Partition 5: Games
Size: 90 GB

**hd1:** (250GB):

ntfs partition that must be accessed by all 4 partitions

Will contain all development/music/Videos


I need to know whether this is in essence a good idea? How does Ubuntu handle a ntfs file structure ito of speed, etc

Thank You

---

### Post by khelben1979 on 2009-02-01
I see no problems with that, however.. make sure that the Linux partition have logical partitions within it.

[This guide]("http://www.linuxplanet.com/linuxplanet/tutorials/3174/5/") "might" be helpful to you. (But I suspect that you already know how it works)

---

### Post by mb_webguy on 2009-02-01
The Windows bootloader doesn't like for Windows to be on a logical partition, or for at least on version of Windows to be on the first primary partition, but since you'll be using GRUB, it shouldn't matter.

While I don't see any problem with your overall idea, I personally would change the size of those partitions.  Devoting 40GB to each OS is overkill, IMO, if you're storing your data on a separate partition.  

Ubuntu is perfectly happy to live on an 8 to 12GB partition, especially since you're keeping your data on the second drive.  The same should be true of FreeBSD.  Unix-derived operating systems and applications designed for those OSes are generally much smaller than their Windows counterparts.

As far as Windows, XP can comfortably be installed on a 15 to 20GB partition.  I don't know about Windows 7, but if it's anything like Vista, I wouldn't install it on anything less than a 25GB partition if you're planning on installing any significant amount of software.  30GB should be safe, however, especially if you're installing games to a separate partition.

And regarding Linux and ntfs, Linux has good support for ntfs.  I don't know specific benchmarks regarding access speeds, but I haven't really noticed much difference between ext3 and ntfs.  The biggest issue is that ntfs can't handle Unix-style file permissions, and so the entire partition must be mounted with the same user, group, and permissions.

---

### Post by Wickd on 2009-02-03
Thanks guys! One more problem though. I get an Error 13 message when I try and run windows 7...

Aah well its just windows, so I'll throw it on a VM if I have to

---

