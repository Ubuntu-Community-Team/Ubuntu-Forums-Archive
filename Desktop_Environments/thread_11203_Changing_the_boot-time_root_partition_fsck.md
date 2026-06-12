---
title: "Changing the boot-time root partition fsck"
date: 2005-01-14
forum: Desktop Environments
---

### Post by offby1 on 2005-01-14
Right now, on startup the root partition is checked every 30 mounts.  While this makes sense on, for example, a server or even a rarely-rebooted desktop system, it does not make sense on a laptop, which is shut down and started up significantly more often.  I did some looking around in the rcfiles, but I was not able to pin down where this value is set.  How can I change this?

(Yes, I know that this is also a laptop question, but I want to do this on two systems, and it's not specifically a laptop issue, nor will the fix be limited to mobile platforms)

---

### Post by ape on 2005-01-15
I'm making an assumption that you are using the ext2 or ext3 filesystem on the disk in questions.  Take a look at the manpage for tune2fs.  This gives you the option of changing the mount count before an fsck is forced or even gives you the option of turning them off altogther (not recommended).

---

### Post by offby1 on 2005-01-15
[QUOTE=ape]I'm making an assumption that you are using the ext2 or ext3 filesystem on the disk in questions.  Take a look at the manpage for tune2fs.  This gives you the option of changing the mount count before an fsck is forced or even gives you the option of turning them off altogther (not recommended).[/QUOTE]

You are making a correct assumption.  I didn't realize that it was a filesystem option, I was poring over the rc scripts for hours :)

Thanks very much!

---

### Post by Tichondrius on 2005-01-25
To change the number of times a ext2/etx3 partition is mounted, after which a file system check (fsck) is performed use -c option followed by the number.

For example, the following command changes it to 100 (fsck will be triggered after filesystem is mounted for the 100th time):

$ sudo tune2fs -c 100  /dev/hda1

To check the value (called "Maximum mount count"), as well as other parameters:

$ tune2fs -l /dev/hda1

Replace /dev/hda1 with the ext2/ext3 partition your wish to set the value for.

---

