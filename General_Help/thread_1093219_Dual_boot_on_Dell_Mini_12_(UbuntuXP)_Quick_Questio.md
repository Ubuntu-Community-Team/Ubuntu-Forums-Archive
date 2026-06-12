---
title: "Dual boot on Dell Mini 12 (Ubuntu/XP) Quick Question"
date: 2009-03-11
forum: General Help
---

### Post by Dontgetit on 2009-03-11
Hello,

I have XP installed on my Dell Mini 12.  The disk was formatted NFTS and the entire disk was one partition comprised of the XP installation.

I subsequently used partition magic to shrink the primary partition and formatted the 10G of unallocated space to FAT32 to use for Ubuntu.

However, when I run the Ubuntu Live disk from an external DVD rom and I get to Step 4 of 7 (partition editor), no partitions at all are recognized.  The screen is blank.

Can anyone please help me with this?  I cannot install Ubuntu otherwise.

Thank you.

P.S. I have tried booting into the live cd and unmounting my hard drive, but my hard drive is not mounted!  So that doesn't appear to work.

---

### Post by Rallg on 2009-03-11
Boot to the live CD. When it loads, run Ubuntu live (do not install).

Ensure that the hard drive is not mounted (or un-mount it). Then, open System > Administration > Partition Editor. This program scans your drives and reveals the partitions.

If the hard drive is not the displayed device when you open the program, then look in the window's upper right corner and choose another device, until you locate the hard drive.

What does it show for the hard drive? That is, how many partitions, which type, are they primary or extended, is any one marked as boot?

If the partition editor successfully reveals the info that you think it should, that is good news. If it cannot locate the hard drive, that is bad news. Let us know.

Incidentally, when you get it together, Ubuntu ought to be installed to a Linux-type partition rather than fat32 (in your case, probably ext3 would be best) and you should also create a linux-swap partition. It is helpful (but not mandatory) to have a small fat or fat32 partition somewhere, for certain purposes. I believe your Dell already has one or two such partitions - leave them there.

Understand that the live CD (or live USB) does not actually have Ubuntu "installed" there. Instead, it uses a packed file system with an emulator-type wrapper that unpacks whatever is needed, when you need it. But when you install Ubuntu to the hard drive, the installer unpacks the files are creates a regular Linux file system.

---

