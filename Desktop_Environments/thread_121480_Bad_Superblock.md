---
title: "Bad Superblock"
date: 2006-01-25
forum: Desktop Environments
---

### Post by Who on 2006-01-25
Hi,
I recently replaced and old Windows NTFS/Fat32 disk on /dev/hdd with a DVDRom drive - after giving up on using some fo the Windows files to make Wine run better :P

While doing this I had created a simlink from ~/windows to a fat32 partition /dev/hdd5 with some of the Dlls from /dev/hdd1 on it. 

Sooo, anyway.... Since I took that disk out I have been getting messages on startup complaining that /hde/hdb8 (my /home partition) has a bad superblock. However, it mounts fine. I have deleted the symlink, but the probelm remains

What can I do - it _is_ possible there are some more links hidden somewhere I don't know about (hwo do I find them?), What _is_ a superblock, really (does it wear it's underpands on the outside of it's tights?), and how _do_ I tell fsck that it is all ok (if it is all ok)...?

Help would be greatly appreciated

Who

---

### Post by Who on 2006-01-26
I fixed this by using parted to resize the partition. No data loss

---

