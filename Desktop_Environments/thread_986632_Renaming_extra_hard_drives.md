---
title: "Renaming extra hard drives"
date: 2008-11-18
forum: Desktop Environments
---

### Post by amacleod on 2008-11-18
I would like to share a problem I recently encountered and the solution thereto.  The problem was that my old hard drives, with ext2 and ext3 filesystems on them, were showing up as, e.g. "16.0GB Media", rather than having useful names as their volume labels.  I got help from the following sources:

[http://ubuntuforums.org/showthread.php?t=958779](http://ubuntuforums.org/showthread.php?t=958779) - renaming mounted drives

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Anyway, my process was pretty much the same as the forum post I linked above, with one addition:

```

sudo e2label /dev/sdb1 OldRoot
sudo /etc/init.d/hal restart
killall -HUP nautilus

```

Hope this helps anyone else who might have had the same issue.  I believe that tune2fs can also be used to change the volume label instead of e2label.

---

