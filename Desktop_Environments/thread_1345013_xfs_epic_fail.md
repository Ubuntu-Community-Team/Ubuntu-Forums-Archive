---
title: "xfs epic fail"
date: 2009-12-03
forum: Desktop Environments
---

### Post by stefansjs on 2009-12-03
I am running a mythbuntu desktop with several hard drives nearly full in it.  Last night, my computer was running perfectly fine, but this morning it was making suspicious mechanical noises and beeps from the pizo-electric speaker.  I didn't actually do anything to it last night (not even shut it down), so I don't know what caused the change.  I think I've determined that it's one of my hard drives that's the problem.  When I unmount /dev/sdc1 the beeping stops.  When I try mounting again, I get this error:
```
mount: /dev/sdc1: can't read superblock
```
Naturally I assumed that something had happened, so I tried to fsck.  Fsck tells me to try to use xfs_check or xfs_repair, which I assume is because the HD is formatted to XFS.  Naturally I try to run xfs_check on the HD.  Here's what I get:
```
~$ sudo xfs_check /dev/sdc1
can't read block 0 for directory inode 133
no . entry for directory 133
no .. entry for directory 133
Segmentation fault
```

What the hell?  I just got a seg fault on xfs_check.  What do I do?  Is my HD irreparably damaged mechanically?  Is there any way for me to save the data on it?  Please help, this is a 500GB hard drive packed to the gills with data.

---

### Post by stefansjs on 2009-12-03
I just ran xfs_check again, and this is what I got:
```
~$ sudo xfs_check /dev/sdc1
xfs_check: /dev/sdc1 is invalid (cannot read first 512 bytes)
```

---

