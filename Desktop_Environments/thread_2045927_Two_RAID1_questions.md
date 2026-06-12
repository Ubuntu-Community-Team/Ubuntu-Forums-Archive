---
title: "Two RAID1 questions"
date: 2012-08-22
forum: Desktop Environments
---

### Post by leo_m on 2012-08-22
1.  How is RAID1 different from a backup copy updated constantly?  I am asking this in the context of various comments I encountered in different forums by people saying that RAID is not backup and you must have a backup in place even if you choose to have RAID.  For a home user, and ignoring physically separate DR location etc., for a home user, how is RAID1 any different (I can understand why RAID0, RAID5 etc. are different, but RAID1 is just another copy, or is it not?)

2.  If I rsync some data from a source to some destination regularly (for backup purposes), I have total control over what gets deleted from source (if at all), what gets deleted from destination (if at all), what gets updated in source and what gets updated in destination etc.  But if I use RAID1, how do I determine beforehand what is going to happen?  As an example, I want to use a removable SSD as my primary source which I keep updating and this is master copy.  If I keep updating it externally, so as to remove and add data from it, when I put it into the computer where it is part of a RAID1 array, what would happen assuming the destination had the latest copy of data before I swapped out the removable ssd, i.e., will the deletions and additions I made in ssd be made in the other RAID1 members as well, or will the deletions I made in ssd get resurrected in ssd?  Of course, in case of updates, I expect the updated copies to overwrite the stale copies of data-items and in case of additions, those will get added to the other RAID1 members too.

---

### Post by SlugSlug on 2012-08-22
RAID1 is for redundancy if one drive goes down you'll still have a working server.

If some how the OS or files became corrupt then you'd need to restore from a backup


RAID1 is not a backup but is there for redundancy

---

### Post by leo_m on 2012-08-22
> If some how the OS or files became corrupt then you'd need to restore from a backup

Okay, thanks; understood (so if one copy gets 'corrupted', the other will too and that's why the need to have a known working backup)

I am hoping someone will throw light on the 2nd query as well...

---

### Post by SlugSlug on 2012-08-22
Not sure I understand question 2

RAID1 is a mirror so every disk in the array is identical - you can't remove a file from 1 disk and not the other

Once a disk is in a RAID array you leave it in. If you want to have an off site backup of your disk look into disk cloning or full system backups.

I quite like 'Back In Time; for my backup solution but I just backup to a dedicated hard drive

---

### Post by mcduck on 2012-08-22
> **leo_m said:**
> Okay, thanks; understood (so if one copy gets 'corrupted', the other will too and that's why the need to have a known working backup)

I am hoping someone will throw light on the 2nd query as well...

As far as I understood you were talking about moving one of the disks around and into different machines? That's not something you'd do with RAID array, all the disks of the array must be present all the time. Also the discs used in the array should be identical and partitoned to exactly the same size. (all remaining space will just be ignored).

...and that's why RAID doesn't count as a proper backup (and neiter does any other method of copying data to a drive that's always conencted to the machine); there are many ways how a computer can fail and destroy all the connected hard drives and devices with it. Any power source or motherboard's power cirquitry failure would have a high change of destroying both the original and the "vackup" data drives. So if you want a decent actual backup, use a removable drive which you only connect to the computer when you are making a backup. (RAID only protects you against physical failure of one of the hard drives connected to the RAID array).

---

