---
title: "Mac os x compatible"
date: 2005-09-19
forum: Desktop Environments
---

### Post by Conde on 2005-09-19
Ive got an iBook G4 and have been using OS X for a while and just installed ubuntu. I got them on the same hard disc but partitiond. can i read all the files from the mac partition throw ubuntu, if so how?
thanks
conde

---

### Post by cwaldbieser on 2005-09-19
[QUOTE=Conde]Ive got an iBook G4 and have been using OS X for a while and just installed ubuntu. I got them on the same hard disc but partitiond. can i read all the files from the mac partition throw ubuntu, if so how?
thanks
conde[/QUOTE]
You should be able to mount the mac partition.  I can't recall what the filesystem type for OS X is, but since it is based off of BSD, I would guess it is maybe ext2 or ext3 maybe.

Try this comand to get a list of what partition to try and mount:
```
$ sudo fdisk -l
```

---

### Post by wmcbrine on 2005-09-19
The standard filesystem for Mac OS X is called HFS+; it's actually based on the original HFS filesystem found on pre-OS X Macs, not anything from BSD, although Unix features have been incorporated. But it still works in Linux. :)

Incidentally, BSD doesn't use ext2/3, either; that's only for Linux. The standard BSD filesystem is UFS, I believe.

---

### Post by Conde on 2005-09-20
ill give it a try now, thanks alot

---

