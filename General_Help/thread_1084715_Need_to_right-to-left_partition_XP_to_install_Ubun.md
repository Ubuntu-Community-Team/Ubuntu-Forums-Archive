---
title: "Need to right-to-left partition XP to install Ubuntu"
date: 2009-03-02
forum: General Help
---

### Post by porchrat on 2009-03-02
Hi all

I have backed up my data and need to now reduce the size of my XP partition to allow an Ubuntu install.  I'm also going to create a FAT32 partition as a common area to store music and other documents in as a sort of common area.

Any suggestions on what application I should use to safely reduce my XP partition in order to install Ubuntu? Preferably something Windows-based as I don't trust gparted to safely reduce the Windows partition without damaging something (had a bad experience before).

Also what is the best way to go about ensuring that both OSes can read and write to the FAT32 partition without problems?

If this has been answered before please don't hesitate to point it out to me, I tried a few searches and couldn't find something to answer my questions fully.

---

### Post by chriskin on 2009-03-02
the best idea, probably, is to do it using the gparted live cd 

doing it while windows is still running isn't a bit dangerous?

and i can say that you have nothing to be afraid of, my shrinking of vista worked perfectly (some icons were messed up but hell, it took something like 2 seconds to put them back :))


did you try the ubuntu version or the live cd last time?

also, why would they not be able to read and write fat-32?

---

### Post by detroit/zero on 2009-03-02
> **porchrat said:**
> Hi all

I have backed up my data and need to now reduce the size of my XP partition to allow an Ubuntu install.  I'm also going to create a FAT32 partition as a common area to store music and other documents in as a sort of common area.

Any suggestions on what application I should use to safely reduce my XP partition in order to install Ubuntu? Preferably something Windows-based as I don't trust gparted to safely reduce the Windows partition without damaging something (had a bad experience before).

Also what is the best way to go about ensuring that both OSes can read and write to the FAT32 partition without problems?

If this has been answered before please don't hesitate to point it out to me, I tried a few searches and couldn't find something to answer my questions fully.
I'd use a different format if I were you. FAT32 is fine and both OSes can read it, but a FAT32 partition will be a pain if you ever decide to enable file/folder sharing with samba or whatever.

I'd go with either NTFS (which both OSes can read out-of-the-box) or install ext2ifs in windows and this will give you the ability to read ext2 and ext3 partitions from inside windows.

---

### Post by porchrat on 2009-03-02
Thanks guys I'll give the gparted off the liveCD a try.

I would prefer NTFS, but I just thought FAT32 would be simpler and give less trouble.  As long as they can both read it I'll go for NTFS.

---

### Post by porchrat on 2009-03-02
OK I gave gparted a try and it worked. XP did a disk check but that was about it. Thanks for the help. Keep up the good work!

---

