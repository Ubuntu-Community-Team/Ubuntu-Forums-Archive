---
title: "windows strikes again (data recovary)"
date: 2009-03-10
forum: General Help
---

### Post by cyclobs on 2009-03-10
*sigh*

unfortunally windows has managed to delete my wonderful linux partition with all my important files and server set up and grr.

somehow windows decided to delete the partition during reinstall

so do any of you guys know some software (either linux or windows) that will read ext3 partitions and grab all the data off it. would really appreciate it guys :)

---

### Post by Wicca on 2009-03-10
Are you sure the partition is overwritten?

Maybe only your MBR is overwritten so your ext3 partition is not visible thus not accessible.

Try booting with the live CD and see if you can see the partition. If you can: don't worry, nothing is lost. Please post back.

---

### Post by sheleztt on 2009-03-10
> **cyclobs said:**
> *sigh*

unfortunally windows has managed to delete my wonderful linux partition with all my important files and server set up and grr.

somehow windows decided to delete the partition during reinstall

so do any of you guys know some software (either linux or windows) that will read ext3 partitions and grab all the data off it. would really appreciate it guys :)
Window$ installer couldn't delete your partition, just because he isn't able to see ext3 partitions. I think he has just overwritten your [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") sector.

Are you booting from usual windows loader now? (chainloader)

The easiest way i see to make your partition accessible again is to boot from LiveCD and try to rewrite your MBR.  This [HOWTO]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") suits you.

Feel free to post back.
Good luck.

---

### Post by leg on 2009-03-10
Sheleztt has the answer I think. This has happened to me before now. Installing Windows after Ubuntu will make it inaccessible until you fix the mbr.

---

### Post by kryptikos on 2009-03-10
Wicca is right. We'd have to confirm what cyclob did when re-installing Windows. Did he just redo the NT partition or grow it etc. If not, then I'm with you guys, quick Live CD in a resuce mode and just have grub read the partition table and write off to the MBR.

---

### Post by cyclobs on 2009-03-12
no it's deleted...

the fact that i couldn't find grub on a live cd and g-parted confirming that the partition is now 'free space' pretty much tells me it's deleted :P

sooooo... any good programs to get it back?

---

### Post by kernelCompile on 2009-03-12
> **cyclobs said:**
> no it's deleted...

the fact that i couldn't find grub on a live cd and g-parted confirming that the partition is now 'free space' pretty much tells me it's deleted :P

sooooo... any good programs to get it back?

If your Windows partition is the same size as it was before and the space that used to be your Ubuntu partitions is marked as free space, your ubuntu file system should still be intact. If this is the case, than the only thing that has actually been deleted is probably your partition table record, and all that you need to do is recreate the partition. The "gotcha"  here is that if you don't create the partition at the same starting location as it had before, you could still hose your data. If you are at all unsure of your previous setup, you should probably google "partition recovery". I haven't used any of these tools, so I can't really tell you which are the best, but I know they are out there -- some free, some proprietary.

If you had a single ext3 partition occupying the space now marked as free, then all you need to do is create a new ext3 partion. Don't format it, just create the partition and your file system will still be there. I would recommend using cfdisk for this, because it will create partition and allow you to set the type without wanting to format it, like gparted will. If you had a swap partition in between, or multiple linux partitins, it gets more complicated, especially if you have no record of the starting sector for the partitions. In this case, you will probably need to use some recovery software that will search you disk to find the starting sector of your partitions.

I'm now going to preach to you that you should always backup your data. It's usually the most valuable part of your computer, and you are just one hard drive failure away from losing it. You should especially back up before doing any kine of major surgery like reinstalling an OS (especially Windows, as its dumb installers tend to assume that it is going to be the only OS on your machine), resizing partitions, etc.  It is all too easy to lose your data in this situation, due to software bugs or bad design, or an error by you, or losing power in the middle of things. Backing up your data (and knowing how to restore it when you need to) can be the difference between an inconvenience and a disaster.

---

### Post by cyclobs on 2009-03-13
> **kernelCompile said:**
> If your Windows partition is the same size as it was before and the space that used to be your Ubuntu partitions is marked as free space, your ubuntu file system should still be intact. If this is the case, than the only thing that has actually been deleted is probably your partition table record, and all that you need to do is recreate the partition. The "gotcha"  here is that if you don't create the partition at the same starting location as it had before, you could still hose your data. If you are at all unsure of your previous setup, you should probably google "partition recovery". I haven't used any of these tools, so I can't really tell you which are the best, but I know they are out there -- some free, some proprietary.

If you had a single ext3 partition occupying the space now marked as free, then all you need to do is create a new ext3 partion. Don't format it, just create the partition and your file system will still be there. I would recommend using cfdisk for this, because it will create partition and allow you to set the type without wanting to format it, like gparted will. If you had a swap partition in between, or multiple linux partitins, it gets more complicated, especially if you have no record of the starting sector for the partitions. In this case, you will probably need to use some recovery software that will search you disk to find the starting sector of your partitions.

I'm now going to preach to you that you should always backup your data. It's usually the most valuable part of your computer, and you are just one hard drive failure away from losing it. You should especially back up before doing any kine of major surgery like reinstalling an OS (especially Windows, as its dumb installers tend to assume that it is going to be the only OS on your machine), resizing partitions, etc.  It is all too easy to lose your data in this situation, due to software bugs or bad design, or an error by you, or losing power in the middle of things. Backing up your data (and knowing how to restore it when you need to) can be the difference between an inconvenience and a disaster.

ahh yeah i get ya.

i did back up my data..... about 80GB worth of it XD

but it was only the windows stuff cause my nature you'd expect everything to be the same after you install an OS on a partition that was made for it.

i'll look into the thing and let you know how i go. thanks

---

### Post by madverb on 2009-03-13
Sounds like you are just jumping to conclusions. Even if it was possible for windows to delete your other partition without any user interaction... you could still recover it, unless you have overwritten it with the windows install files.

---

