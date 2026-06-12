---
title: "mkdosfs failing"
date: 2009-05-01
forum: General Help
---

### Post by Auraomega on 2009-05-01
I'm trying to format a drive to FAT12. My normal port of call would be to use mkdosfs -F 12 /media/disk and be done with it, but either Ubuntu or my flash drive is being a pain and won't play nice. I can't remember the exact error, and I just spent the past hour or so trying to get it working so my laptop died which means I can't check.

My knowledge of FAT12 is pretty basic, so what I'm trying to do might not even be possible, but basically I have a 32mb flash drive that I'm trying to use to emulate a floppy disk for a project.

Any help much appreciated.
-Aura

EDIT:
Found the error, should have been using /dev/sdb not /media/disk. Still, however, not formatting to FAT12 though

---

### Post by lensman3 on 2009-05-01
I don't think a Fat 12 will go to 32 Megabytes.  I think you need at least a Fat 16.  Try formatting without specifying a size and see what the program chooses for you.  Fat 12 was used for floppies.

I may be completely wrong about this.

---

