---
title: "partitioning"
date: 2009-04-03
forum: General Help
---

### Post by accooper on 2009-04-03
I have read that if you dual boot to windows and Ubuntu that you should partition any new hard drive a Fat32.  Ok I just got a new external drive and when I went to partition it windows XP would only let me partition it as NTFS.  Is there any real benifit to partitioning it as FAT32? except for FAT32's lack of security?  What does this do to Ubuntu?

:guitar:

Thanks Andrew

---

### Post by SunnyRabbiera on 2009-04-03
Nah I would keep it NTFS, as long as you have a windows drive somewhere NTFS will be fine for externals.
Just take caution in mounting/unmounting.

---

### Post by logos34 on 2009-04-03
You must have been reading an old article.  Ubuntu comes with out-of-the-box read+write support for NTFS (NTFS-3G driver).

If you want to access ext3 partition from windows side, get fs-driver

---

### Post by Meow27 on 2009-04-03
well, the two above posts are true, but you should know that fat32 has a limit of 4gb per file, ntfs is less limited

---

### Post by 3Miro on 2009-04-03
No one should be using Fat32 anymore. NTFS is much better (still sux compared to ext*, but better). I have met a lot of people that have fat32 problems on both Linux and Windows. It is outdated.

---

### Post by leonardo_neo on 2009-04-03
OK, it seems I am not updated for a while.... :)

I have a question. I already have NTFS-3G package installed, and I can access my windows partition files. But I can't delete them ( I guess that is a deliberate feature to keep windows file safe). I formatted my common partition as FAT32, so that I can access that from both the OS (Ubuntu + Xp)

So do you guys recommend to format that 'common' partition too as NTFS, or  this recommendation is only for external disks?

Moreover, if I format my common partition as NTFS, will I be able to edit files there ( I mean create a new file or delete a file)?? Because presently as I have already said, in Windows partition I can only read files, but I can't delete/create new files?

Thanks. :)

P.S.: OK, so after posting my question, I did some research upon this topic. From Ubuntu official guide for installation, I found that they recommend the common partition to be formatted as FAT32. Here is the link for the guide......

> [https://help.ubuntu.com/8.04/switching/dualboot-concepts.html#dualboot-concepts-partitions](https://help.ubuntu.com/8.04/switching/dualboot-concepts.html#dualboot-concepts-partitions)

But this guide is for 8.04. I am not sure if it is applicable for 8.10 as well. So I guess still the common partition has to be formatted as FAT32. For external disks, NTFS is fine. If someone has some different information, then please enlighten me/others.

Thank you all :)

---

