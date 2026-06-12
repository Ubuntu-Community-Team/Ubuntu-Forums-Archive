---
title: "NTFS on Linux vs Ext3 on Windows"
date: 2009-03-23
forum: General Help
---

### Post by shade5 on 2009-03-23
Hello,

I am working on XP and Ubuntu parallely and therefore I need a filesystem that works on both OS. I was working with fat32 until now but 1. it is not very secure and 2. you get no links. 

NTFS and Ext3 both fulfill my desires but I am not sure which one I should use. Can you tell me your opinion, rumours you heard on how stable both systems are working and so on. 

My favorite is Ext3. I am also primary working on linux.

Thanks.

---

### Post by SuperSonic4 on 2009-03-23
ext3 is journaled which virtually eliminates the need to defrag the drive and it also helps protect data in case of an unclean shutdown

---

### Post by john183 on 2009-03-23
There is a windows kernel level driver that allows windows to read and write ext3. [http://www.fs-driver.org/](http://www.fs-driver.org/) I used it without any problems when i was dual booting my computer.

---

### Post by mb_webguy on 2009-03-23
If you are primarily using Linux, go with ext3.

Both the Linux support for ntfs and the Windows support for ext3 through the ext2ifs driver are very stable, but have the same limitations.  Linux has no journaling support for ntfs, and the Windows ext2ifs driver has no journaling support for ext3 (and therefore treats it as ext2).  Likewise, Linux doesn't support Windows-style file permissions, and Windows doesn't support Linux-style file permissions.

Therefore, since there is equivalent support by each OS for the non-native filesystem, you should pick the one that is native to your primary OS so that you can use journaling and file permissions in that OS.

---

### Post by xiaosilent on 2009-03-23
How about EXT4?

---

### Post by mb_webguy on 2009-03-23
ext4 isn't quite ready for mainstream use at this point.  There are still a few bugs to work out, including a few that have been reported to result in massive data loss.

---

### Post by Yashiro on 2009-03-23
I use NTFS on shared drives. Linux NTFS functionality is better than Windows support for ext2/3/4.

In the event of a disaster it is also easier to boot into Linux and mount NTFS than to do it the other way around.

---

### Post by shade5 on 2009-03-23
>Linux NTFS functionality is better than Windows support for ext2/3/4.

Why is NTFS better? Are there fatal disadvantages with Extx?

---

### Post by joewski on 2009-03-23
Reading NTFS is ok for Linux however you may have problems with 64bit systems running Vista or above.

Trying to get windows systems to read linux partitions proved to be more difficult. 

After much trial and error, I settled on an external machine running a NAS (Samba systems). I use several types. 1. LanDrive, 2. FreeNAS, & Ubuntu Server with Samba enabled.

---

### Post by mb_webguy on 2009-03-23
> **shade5 said:**
> >Linux NTFS functionality is better than Windows support for ext2/3/4.

Why is NTFS better? Are there fatal disadvantages with Extx?

In my experience, once you get ext2ifs running on Windows, it works as well as ntfs support on Linux.  Some people have problems getting ext2ifs working, though.  Most of the problems I've seen reported involve Vista, and may involve UAC.

---

### Post by ChemShock on 2009-03-24
I have my set-up under Wubi and the windows defrag is showing ubuntu as a big defragmented mess. is this normal and safe?

---

