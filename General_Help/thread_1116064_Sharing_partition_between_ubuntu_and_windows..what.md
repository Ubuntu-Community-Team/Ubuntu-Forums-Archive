---
title: "Sharing partition between ubuntu and windows..what format?"
date: 2009-04-04
forum: General Help
---

### Post by boyofford on 2009-04-04
Hi all,
My computer is a bit of a mess, got various partitions with various versions of Ubuntu and a windows vista partition, so time for a spring clean!

Want to create a partition separate to my /home partition to use for music, videos etc. and use it for both windows and ubuntu.

Question is, which format should I use for this partition?
Ubuntu can use ntfs as vista already uses this, so is this best?
I've read that fat32 only supports upto 4GB file size, which i may go over.

Bit of a novice so sorry if these questions seem daft, just after the pros and cons.

Cheers
Rich

---

### Post by 3Miro on 2009-04-04
Do not use fat32, it is outdated and very slow and unsecured.

The easy way is to use NTFS, both windows and Ubuntu will read them just fine without any fancy settings. That's what I am doing.

The more complicated way is to set it up as ext3/4 (the Linux format) and then install a program on windows that will let you read it.

---

### Post by mb_webguy on 2009-04-04
If Ubuntu is going to be your primary OS, then I'd go with ext3, and install the [ext2ifs]("http://www.fs-driver.org/") driver in Windows.

If Windows is going to be your primary OS, you might as well go with ntfs.  Ubuntu can use ntfs without any additional work on your part.

Both OSes have the same limitations in using the non-native filesystem.  Neither OS can use journaling on the non-native filesystem, and neither non-native filesystem supports the file permissions used by the OS.  In that respect, using ext3 actually has is the better choice, since file permissions really aren't used much in Windows other than making a file hidden.  On the other hand, ntfs is easier to set up, since you don't have to do anything special in Ubuntu.

---

### Post by boyofford on 2009-04-04
Thanks guys,
have decided to go with ntfs,
I use ubuntu a hell of a lot more than vista,
but as its easier to set up, I'm a bit of a novice and will probably only be putting music and vids on there I think it will do fine.

plus if i screw up one OS, should be able to get to these files from the other until get in the mood for fixing 	:smile:

---

