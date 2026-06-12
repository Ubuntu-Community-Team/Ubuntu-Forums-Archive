---
title: "File system for external usb drive? fat32 vs ntfs"
date: 2009-01-25
forum: General Help
---

### Post by bailout on 2009-01-25
What is the best file system to use for drives or partitions that are shared between linux and windows? I have always used fat32 up to now but just tried a new usb drive that came formatted as ntfs and it seems to work ok under linux. Ntfs write support under linux was regarded as unreliable for a long time - has it improved enough to be trusted?

Also does ntfs affect permissions when accessed from linux? Getting full read write access was often tricky but I have got a line I add to fstab that seems to work now for fat32.

---

### Post by capitalistpiglet on 2009-01-25
ntfs is safe to write to now. Plus you have the advantages of using ntfs over fat32 such as increased file size. So its probably best to use ntfs. Im fairly sure linux will ignore ntfs permissions.

---

### Post by mb_webguy on 2009-01-25
It depends on your use of the drive.  NTFS has some distinct advantages over FAT32, most notably the greater maximum file size, and Linux no longer has any problem reading and writing to NTFS (though I believe that it can still not do journaling), but FAT32 is still more widely supported than NTFS.  For example, if you have a Playstation 3, you may want to format the external HD as FAT32, since the PS3 doesn't currently support NTFS.  If you want maximum portability, go with FAT32.  If you're pretty sure you won't be connecting the drive to a system that can't support NTFS (i.e. something other than a personal computer of some sort), go with NTFS.

On the other hand, if we're talking about a partition shared between Linux and Windows on a dual-boot system, and Linux is your primary OS, then you may want to format it as ext2 or ext3 and use [ext3ifs]("http://www.fs-driver.org/") to allow Windows to read and write to the partition.  This allows you to use full Linux file permissions while in Linux, and yet still read and write to the partition in Windows.

---

