---
title: "&quot;Ghost&quot; partition showing up in new Ubuntu install"
date: 2014-09-12
forum: Desktop Environments
---

### Post by brendonwp on 2014-09-12
I've just installed Ubuntu 14 in dual boot with Win8.  The two OSs share an SSD, and there are two HDDs as well for data.  The one HDD is for Ubuntu and is ext4.  The other HDD for Windows is NTFS, and the two partitions there show up automatically in Ubuntu and I can share data there.  I set up Ubuntu at installation so that one of the NTFS data partitions is mounted below /media for convenience.

Now /media/myusername shows two entries, one of which is the NTFS partition that was not hard-mounted, and the other one is an empty "ghost" partition - the UUID appears in the fstab but not when I run blkid. And when booting Ubuntu I get "the disk drive is not ready yet or not present", and a reference to UUID for the "ghost" partition???

---

### Post by brendonwp on 2014-09-12
I changed the label of the hard-mounted drive in Windows 8 yesterday, and it seems that this can leave fstab confused:
[http://askubuntu.com/questions/410460/disk-drive-is-not-ready-yet-or-not-present-after-renaming-partition](http://askubuntu.com/questions/410460/disk-drive-is-not-ready-yet-or-not-present-after-renaming-partition)

The solution seems to be to delete the invalid entry from fstab (after backing the file up for safety!)

---

