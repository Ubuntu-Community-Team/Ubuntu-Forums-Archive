---
title: "Empty folders after transfer to external hard drive"
date: 2008-12-21
forum: General Help
---

### Post by tulpaner on 2008-12-21
After a transfer of folders with content from the computers hard drive to an external hard drive, the folders turns always out to be empty on the external hard drive. Doesn't matter of I copy the folders or if I move them. Any ideas?

---

### Post by northern lights on 2008-12-21
How are you copying the folders? Drag&Drop in nautilus?
Does a progress bar appear?

If it wouldn't work at all, I'd say you don't have the right permissions set for the external drive, but you can create folders, right? Can you copy/move single files?

---

### Post by tulpaner on 2008-12-29
I have tried both to drag & drop and copy & paste the folders. Straight from desktop and also through Nautilus. Progress bar appears all the time. I can create folders on the external drive and do whatever I want with all the other old folders/files on the drive.

I could actually move single small files (mp3) without any problems from the computer to the external drive. But not folders with the mp3's in them, then the folder is empty. 

Larger files (movies) gets transfered if I transfer them like single files but then they can't play ("An error occured. Could not read from resource" is the error message in totem, vlc won't play them at all). When I transfer them in a folder the folder is empty after the transfer is completed.

I also have a computer with Windows XP and there is no problem like this on that computer. I can also add that I can move files from the external drive to the Ubuntu computer without any problems. It's only problems when moving files from the Ubuntu computer to the external drive. Can it be the permission settings for folders (and larger files?) on the ubuntu computer? If so, where can I make such a change valid in general and what should the setting be?

Thanks for the help!

---

### Post by northern lights on 2008-12-29
> **tulpaner said:**
> Can it be the permission settings for folders (and larger files?) on the ubuntu computer? If so, where can I make such a change valid in general and what should the setting be?
No it can't be missing permissions for folders and large files only.

With the external drive connected, can you post the output of ```
sudo fdisk -l
```I'll point out what device it is and you should subsequently run *fschk* on it.

Have you tried reformatting?
(either ntfs or FAT32 - Ubuntu should handle ntfs out of the box, but FAT32 even less likely to fail, plus it needs not be safe removed from Windows, as do ntfs drives)

---

### Post by tulpaner on 2008-12-30
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x868b868b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11784    94654948+  83  Linux
/dev/sda2           11785       12161     3028252+   5  Extended
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12088156

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976768033+   c  W95 FAT32 (LBA)

Haven't tried reformating. That will be the last way out, thus I have much files on the drive that needs to be saved on another drive first (if so).

---

### Post by northern lights on 2009-01-01
Run```
dosfsck -a /dev/sdb1/
```to check the external drives filesystem and repair errors

---

### Post by tulpaner on 2009-01-02
This is what I receive:

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/sdb1:Permission denied

---

### Post by northern lights on 2009-01-02
Run it as root, i.e. ```
sudo dosfsck -a /dev/sdb1/
```

Sorry, figured you'd do that if you don't have permissions.

---

### Post by tulpaner on 2009-01-04
Then I get:

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
open /dev/sdb1/:Not a directory

---

### Post by northern lights on 2009-01-04
Man, my bad. Sincere apologies.

I had put an obsolete / in the end making it a directory rather than a device.

It should be run as such```
sudo dosfsck -a /dev/sdb1
```

If it merely reports the clusters and cluster size and fixes no filesystem errors, reformatting would be indeed your only option.

---

### Post by tulpaner on 2009-01-07
No probs.:) 

I get this after "sudo dosfsck -a /dev/sdb1":

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: ( offset: original/backup)
65:03/00
Not automatically fixing this.

So reformatting is the only solution?

I thought about the info I got after "sudo fdisk -l"

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12088156

My guess is that the quoted part above is information on the external disk. If so there is an error in the size, the disk is actually 1 TB not 500 GB. And the containing data on the disk is 496,4 GB. Can the problem lie there?

Like I said the disk works fine accept this litle problem. And the problem is only a problem when running Ubuntu. I'm not an expert but I would guess that the problem would be in my Ubuntu-system. And it has worked fine until recently. I just want to be sure that reformatting the disk is the only solution before I proceed.

---

### Post by northern lights on 2009-01-07
I'd run *dosfsck* once more with the -r option. It interactively repairs the file system. The user is asked for advice whenever there is more than one approach to fix an inconsistency.

If```
sudo dosfsck -ar /dev/sdb1
```does not fix the error, then reformat.

---

