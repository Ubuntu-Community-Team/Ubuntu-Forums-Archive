---
title: "dapper version of gparted BUGGY ?!?"
date: 2006-06-21
forum: Desktop Environments
---

### Post by kabanta on 2006-06-21
I've been having a lot of problems with an external usb drive formatted as fat32. In trying to track down these troubles and fix them, I have discovered a number of posts in these forums and the launchpad that suggest that the version of GPARTED (v 0.1) included in Dapper may have a serious bug. Comments on launchpad suggest that some of the problems I have had (and others seem to have had) were fixed with gparted v. 0.2 (released in january, but not in dapper).

Signs of this bug include: misreading file allocation tables, displaying fat32 and ntfs partitions in black (or with an exclamation point), treating the drive as read-only, and creating new problems (lost data) when trying to resize existing partitions.

Because of my troubles, I actually just bought a brand new external drive. And, yes, instantly encountered problems if I try to work with it via gparted. (But using parted, fsck and other command-lines tools seem to work  just fine.)

[As an update: using dapper's gparted by way of the LiveCD seems to be a bit better. If one unmounts the drive to be partioned, it *shouldn't* make a difference if a partitioner is used from the computer's version or from a LiveCD .... sigh.]

If I am wrong about this, it would be good to know. If not, might be good to publicize this problem a bit more.

---

### Post by x64Jimbo on 2006-06-21
I've never used gparted myself. Have you tried qtparted?

---

### Post by kabanta on 2006-06-21
[QUOTE=x64Jimbo]I've never used gparted myself. Have you tried qtparted?[/QUOTE]
Yes, but at this point I'm a bit nervous about any of the GUI-based versions :rolleyes:

---

