---
title: "eeepc ssd i/o error"
date: 2009-06-22
forum: General Help
---

### Post by nkobel003 on 2009-06-22
About 5 months ago, my eeepc 1000 (with a 32G ssd and a 8G ssd drive) crashed while using banshee. When I booted it back up, it had errors and I told it to perform a disk scan and then, without thinking, told it to write changes to the disk. Long story short, the 32G disk became corrupted, which had my main OS on it. I eventually recovered most of the data that was on it using photorec/testdisk and switched to the 8G drive. However, I'm at the point where I have the time to reformat and switch back, but I don't know how. When I try a fresh install via ubuntu studio it says "Input/Output Error". I know it isn't a dead drive because I recovered almost the entire disk. Any ideas of what's going on or how to fix this? Any apps that will make this sucker work? ha.

As a note, when I attempted to mount the drive in the past, it would say I have a bad superblock, even when I tried an alternative superblock. I finally tried creating a new partition table in GParted, however, it ended in error and finally GParted will no longer recognize /dev/sdb (which is the 32G dead drive).

---

