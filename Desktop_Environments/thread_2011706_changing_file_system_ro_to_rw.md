---
title: "changing file system ro to rw"
date: 2012-06-27
forum: Desktop Environments
---

### Post by bencouve on 2012-06-27
Sorry if this has been answered somewhere before, did have look for it.
I have a files system that is read only and I want to set it to rw. How do I do that?
 
Here is what I see with the mount command - or is there something I am missing here ...

/dev/sda3 on /u01 type ext3 (rw,errors=remount-ro)


Thanks in advance for your help.

---

### Post by mcduck on 2012-06-27
Based on the mount options you already have, the drive should already be mounted as rw. If it isn't, that would be because there is some filesystem (or other) problem with the drive, and it's mounted as read-only to prevent any further damage to the filesystem.

...and in that case the way to solve the problem is to first make sure you have a recent backup of all the important files on the drive (which everybody should always have anyway ;)), and then try running fsck on the drive to fix any filesystem issues.

If fsck isn't able to solve the problems, check the drive's SMART status to see if the drive itself is fine.

edit: and of course since it's an Ext3 drive and thus supports ownerships and permissions, make sure it's not just a case of you not having the ownership or write permission instead of the filesystem actually being read-only. :)

---

### Post by bencouve on 2012-06-27
mcduck, thanks for your response. This particular partition has oracle installed on it. If I try to write and save a file as root it is ok, but I cannot with the oracle user.

I did the oracle install as root. Should be able to write as oracle user too.

---

### Post by steeldriver on 2012-06-27
if root can write then it sounds like a permission / groups / users issue - not a ro filesystem

---

### Post by bencouve on 2012-06-27
Ye, fair point. Looks like a re-install ...

---

