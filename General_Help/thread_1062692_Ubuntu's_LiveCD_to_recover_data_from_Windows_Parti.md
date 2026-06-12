---
title: "Ubuntu's LiveCD to recover data from Windows Partition"
date: 2009-02-07
forum: General Help
---

### Post by Rorsch on 2009-02-07
Hello,

I was wondering if it's possible to recover files from a Windows partition which went bananas (can't boot it, files are all with strange names %?#, etc) using the Ubuntu's LiveCD. I tried using BartPE but it's a pain since I have the partition in a raid system (nvidia) and GetDataBack is not working as it should. 

Please help me, just trying to save some photos and past files.

---

### Post by 73ckn797 on 2009-02-07
I don't see why not. As long as it will read the Windows drive.

What happened to the drive that corrupted the filenames?

---

### Post by Rorsch on 2009-02-07
> **73ckn797 said:**
> I don't see why not. As long as it will read the Windows drive.

What happened to the drive that corrupted the filenames?

I think it was because of Windows 7 Beta, everytime I booted XP again I always needed to perform a chkdsk. One day my Nvidia raid drivers issued me a warning and the PC "froze", I tried fixing the boot/mbr, and nothing.

When I run Ubuntu's LiveCD I can see the disk, but the files have very strange names (and the partitition is all wrong - fat12). How can I salvage something?

---

### Post by x33a on 2009-02-07
That why it's called a beta. it's not for production pcs. i think our over enthusiasm gets us in trouble a lot of times :)

back on topic, boot ubuntu live disc, and plugin a pen-drive for backup.

then if your files aren't corrupt, you can simply copy and paste them on the pen-drive.

---

### Post by Rorsch on 2009-02-07
> **x33a said:**
> back on topic, boot ubuntu live disc, and plugin a pen-drive for backup.

then if your files aren't corrupt, you can simply copy and paste them on the pen-drive.

But if the files have strange names (and sizes), doesn't it mean they're corrupted?

---

### Post by Julius1988 on 2009-02-07
How about photorecStatic and TestDisk?

---

### Post by 73ckn797 on 2009-02-07
I had the same Windows 7 issue on another computer and had to wipe the partition where 7 was installed. Fortunate that the computer is used for messing around and not my primary system.

---

### Post by Rorsch on 2009-02-07
I'll try to run TestDisk :) Thanks.

(I'm trying to salvage files from the XP partition... Windows 7 had a small partition with few files inside)

---

### Post by Rorsch on 2009-02-07
TestDisk presents me with 2 disks instead of 1 (I'm using a raid system from nvidia). How can I make it recognize the raid? The system itself detects only 1 disk of 500gb instead of the 2 of 250gb

---

### Post by Rorsch on 2009-02-07
Nobodie? :( Help me please

---

### Post by TheLions on 2009-02-07
maybe you should run chkdisk from xp recovery mode (xp installer)...

---

### Post by Rorsch on 2009-02-07
> **TheLions said:**
> maybe you should run chkdisk from xp recovery mode (xp installer)...

My partitition is all messed up, doesn't show the "real" disk... I've installed dmraid in the LiveCD, but still, my raid isn't detected on testdisk :(

---

### Post by -kg- on 2009-02-07
> **Rorsch said:**
> But if the files have strange names (and sizes), doesn't it mean they're corrupted?

Not necessarily.  If, somehow, your partition was converted to FAT12, then FAT12 does not support long filenames.  If it finds a long filename it will do it's best to convert it and bring it down to the 8X3 filename format that it supports.  I've had that issue at times when I tried to create a CD-ROM with long filenames.

I certainly don't understand how that partition could have gotten reformatted to FAT12, though.  Even a BETA version of the newer 'doze OSes shouldn't reformat a partition, and *especially* not to FAT12!  That is about as antiquated of a filesystem as you can get.  They use that for floppy disks back in pre-1984 (when FAT16 was introduced) and probably since, though only for floppy disks.

If that partition was actually converted to FAT12 without destroying all the data on it, it might indeed be corrupted, since FAT12 will only support up to 32 MB (not GB...***MB***).  If the partition was any bigger than this (and nowadays it's most likely) the data would most likely be corrupted.

Then again, perhaps you were seeing a floppy disk inserted into your floppy drive?  That would be FAT12.

---

### Post by Rorsch on 2009-02-08
> **-kg- said:**
> Not necessarily.  If, somehow, your partition was converted to FAT12, then FAT12 does not support long filenames.  If it finds a long filename it will do it's best to convert it and bring it down to the 8X3 filename format that it supports.  I've had that issue at times when I tried to create a CD-ROM with long filenames.

I certainly don't understand how that partition could have gotten reformatted to FAT12, though.  Even a BETA version of the newer 'doze OSes shouldn't reformat a partition, and *especially* not to FAT12!  That is about as antiquated of a filesystem as you can get.  They use that for floppy disks back in pre-1984 (when FAT16 was introduced) and probably since, though only for floppy disks.

If that partition was actually converted to FAT12 without destroying all the data on it, it might indeed be corrupted, since FAT12 will only support up to 32 MB (not GB...***MB***).  If the partition was any bigger than this (and nowadays it's most likely) the data would most likely be corrupted.

Then again, perhaps you were seeing a floppy disk inserted into your floppy drive?  That would be FAT12.

I have no floopy on the floopy drive, also, the number of files doesn't correspond to the number of files I had on the root of the drive.

I just need to save some files and format the dam thing... While is Testdrive not working? :(

---

