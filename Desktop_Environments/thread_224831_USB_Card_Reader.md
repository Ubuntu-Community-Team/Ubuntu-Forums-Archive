---
title: "USB Card Reader"
date: 2006-07-28
forum: Desktop Environments
---

### Post by zudduz on 2006-07-28
I have a flash card reader.
When I put in  a flash card only the current user can access it and I am unable to change the permissions.
This is problematic because it does not necessarily mount to the account currently in use on screen but any account that is logged in my grab it before the other accounts do.

How can I make it so that everyone had full permission to my card reader?

---

### Post by Paerez on 2006-07-28
can you please post your /etc/fstab file?

---

### Post by zudduz on 2006-07-28
I wasn't aware this was associated.
Is there a gui for managing these configurations?
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/md0        /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /boot           ext3    defaults        0       2
/dev/sdb1       /extra          ext3    defaults        0       2
/dev/md1        none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by Paerez on 2006-07-28
hmm you're right, its not an fstab its an automount thing. I don't know how to do that....

---

### Post by zudduz on 2006-07-28
Thanks for the attempt.  Does anyone else have any Ideas?  I mean this is annoying to the point of switching back to windows.

---

### Post by keithjr on 2006-08-02
clarification request...I'm having trouble figuring out what you want and what's going on

It mounts right now and is visible to the current user only and nobody else can see it?  And you want to make anybody who is logged in capable of seeing it?

---

### Post by zudduz on 2006-08-02
It is not mounting to the current user.  Both my and my wife's accounts will be logged in.  My wife will be using the computer on her account.  When she places the card into the reader it mounts to my account sometimes.

Since her account does not mount it she cannot see the data, eject the drive, or write to it.

---

