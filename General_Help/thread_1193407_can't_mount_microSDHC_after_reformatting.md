---
title: "can't mount microSDHC after reformatting?"
date: 2009-06-21
forum: General Help
---

### Post by kaatuck on 2009-06-21
Okay, so some backstory. I recently had a problem with one of my microSDHC cards where, after mounting, it only recognized it as having ~1 GB (it's supposed to have 4).  I reformatted with fdisk (where it recognizes it as having 4 GB), setting it to FAT 32 (like the working card), and thought all was well.  Unfortunately, now it won't mount.  It's not just that it won't automount, I think it might be something more than that, some other setting that I've overlooked and need to fix or something?  

Here's what I get when I plug in the SD card I'm having trouble with:
```
boo@deepthought:~$ dmesg|tail
[  622.580538] FAT: bogus logical sector size 65535
[  622.580542] VFS: Can't find a valid FAT filesystem on dev sdb1.
[  622.590052] hfs: unable to find HFS+ superblock
[  622.594754] hfs: can't find a HFS filesystem on dev sdb1.
[  622.601174] VFS: Can't find ext3 filesystem on dev sdb1.
[  622.605407] VFS: Can't find an ext2 filesystem on dev sdb1.
[  622.610383] ReiserFS: sdb1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sdb1
[  622.635457] XFS: bad magic number
[  622.635460] XFS: SB validate failed
[  961.540483] usb 6-3: USB disconnect, address 7

Here's what I get when I plug in the good SD card, if that helps any:
boo@deepthought:~$ dmesg|tail
[ 1005.678003] sd 7:0:0:0: [sdb] Write Protect is off
[ 1005.678008] sd 7:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1005.678012] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1005.680498] sd 7:0:0:0: [sdb] 7741440 512-byte hardware sectors (3964 MB)
[ 1005.681370] sd 7:0:0:0: [sdb] Write Protect is off
[ 1005.681375] sd 7:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1005.681378] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 1005.681383]  sdb: sdb1
[ 1005.694855] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 1005.694910] sd 7:0:0:0: Attached scsi generic sg2 type 0

```Also, when I plug in the bad SD, Ubuntu still automatically recognizes the USB dongle it's plugged into, even though it doesn't recognize the SD card itself (outside of fdisk, apparently).

Please tell me this is fixable, I'd hate to have a broken card when it's so new!  I would really appreciate any help!  Thanks!

---

### Post by blueridgedog on 2009-06-21
You imply that you formated the disk, but fdisk only makes partitions.  Did you use mkfs.vfat on the partition you made or format it with gpartd?

---

### Post by kaatuck on 2009-06-22
Oh wow, mkfs.vfat did the trick.  I can't believe it was something as simple as that, and I thought I'd been trying everything.  I'm still kind of new to Linux, guess I'm at that stage where I know just enough to get myself in trouble haha.
 
 Thanks, blueridgedog!

---

