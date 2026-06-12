---
title: "Basic XFS lost Superblock"
date: 2008-12-26
forum: General Help
---

### Post by notquitehere188 on 2008-12-26
I am using XFS as the file system for my server.  Yesterday it stopped working suddenly, saying that it was read only.  Somehow I seem to have completely lost my superblock.

the computer still boots fine, I just can't write anything, and a lot of programs error.  but things like samba and ssh still work perfectly.

Is there any way to fix this error short of a reformat?

Is there any way that I can reformat using the files which are readable from the drive, supposing I copy them to another drive?

When I ran xfs_repair it said it could not find the primary superblock, went .............................. for a long time, and then said no secondary superblocks were found.

--- Edit ---

Another strange thing.  I can write files using samba.

---

