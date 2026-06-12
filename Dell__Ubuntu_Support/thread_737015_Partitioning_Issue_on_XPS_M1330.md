---
title: "Partitioning Issue on XPS M1330"
date: 2008-03-27
forum: Dell  Ubuntu Support
---

### Post by antmenj on 2008-03-27
This is the situation I'm in (see picture).  As you can imagine Vi$ta has a few issues:twisted:.  How do I sort this one presuming I may want to use vista from time to time?

If I play around resizing partitions will the boot options thing still know where to find everything?

Should I just start again or can I fix this?

---

### Post by TonyLB on 2008-03-27
> **antmenj said:**
> This is the situation I'm in (see picture).  As you can imagine Vi$ta has a few issues:twisted:.  How do I sort this one presuming I may want to use vista from time to time?

If I play around resizing partitions will the boot options thing still know where to find everything?

Should I just start again or can I fix this?

Shrinking and growing partitions shouldn't be a problem, I've done this more than once on different machines.  The problem comes when you remove or add partitions.

I did this on one machine (with Suse) and it wouldn't boot because grub couldn't find the menu.lst file.  Not a problem.  Use a rescue disk, then the appropriate grub commands (find the root, set the root, see the grub howto).  Did it on a second machine, Dell Inspiron with 1 Windows partition and I removed the windows partition.  No matter what I did, I couldn't seem to get it to work.  Moral - try it, but back the data up first - wish I had!

I've read that the Vista NTFS is not quite the same as XP NTFS.  If that's true, then parted might have a problem with it.  With my new Dell, I used Vista to resize the vista partition, then parted to handle everything else.

Tony

---

