---
title: "how should I format my USB drive?"
date: 2009-04-14
forum: General Help
---

### Post by gatorbrit on 2009-04-14
I have an external USB drive that I use on both windows and ubuntu.  It is currently formatted as FAT32, but this causes all sorts of permission issues when I try to rsync etc.   

If I reformat the drive, what would be the best format to use for both win and linux and how do I go about it?

Thanks

---

### Post by mb_webguy on 2009-04-14
FAT32 really is the best format for maximum portability.  Next up would be ntfs, but it has a bit more overhead, which can be an issue with smaller USB flash drives.  You could also use ext3 with the [ext2ifs]("http://www.fs-driver.org/") driver for Windows.

Keep in mind, though, that Windows doesn't recognize Linux-style file permissions, and Linux doesn't recognize Windows-style file permissions.  So if you're having problems on Linux with FAT32 due to permission problems, ntfs won't help any.  But if you go with ext3, the only Windows systems that will be able to use the drive are those on which the ext2ifs driver are installed.

Since FAT32 and ntfs filesystems are mounted with a certain set of permissions which is applied to all files and directories on the filesystem, you can probably resolve your problems with the FAT32 drive by simply changing how the drive is being mounted.

---

### Post by gatorbrit on 2009-04-14
Thanks for clearing that up.  It is FAT 32.   I was having problems with it becoming read only, but it turns out that these are often due to an error on the disk (i.e. if unplugged).
This page helped me fix the disk errors 
[https://help.ubuntu.com/community/TestingStorageMedia](https://help.ubuntu.com/community/TestingStorageMedia)
After I fixed them all is well!
Thanks

---

