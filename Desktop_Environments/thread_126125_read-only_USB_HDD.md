---
title: "read-only USB HDD"
date: 2006-02-05
forum: Desktop Environments
---

### Post by robfindlay on 2006-02-05
Hey, I just picked up a HDD enclousure from compusa and threw one of my extra 80gig drives in it and breezy saw it and mounted it no problem, cept for one thing, it's read only. 

I tried 

sudo chmod 777 /media/meh/ 

and got the following.

chmod: changing permissions of `meh/': Read-only file system

Any thoughts?  This drive was previously working fine in an XP machine.


Rob

---

### Post by frodon on 2006-02-06
i guess your drive is use NTFS file system and there's no write support under linux for NTFS, in addition NTFS don't support unix rights and ownership so chmod, chown , ... commands will not work.
So if your drive use NTFS, no solution :(

---

### Post by Ocxic on 2006-02-06
there is one solution, reformat to ext3 or other linux filesystem. unfortunatly it will erase all the data on the drive.

---

### Post by alamba on 2006-02-06
Another solution might be to convert to FAT32. I know there are fat-->ntfs converters that keep your data intact. Not sure of the other way around though. Once you're on FAT32 you will be able to read and write to the disk from both the platforms (ie win and linux).

Akshay

---

### Post by frodon on 2006-02-06
FAT32 could be a good way to use your partition but if converting a FAT32 partition to NTFS works it's not the case for NTFS to FAT32 convertions, so in all the cases you will need to re-format your partition.
I give you a link to a post i made which explain advantages and disadvantages of the 3 most used file systems : [http://www.ubuntuforums.org/showpost.php?p=697500&postcount=4](http://www.ubuntuforums.org/showpost.php?p=697500&postcount=4)

---

### Post by robfindlay on 2006-02-06
[QUOTE=alamba]Another solution might be to convert to FAT32. I know there are fat-->ntfs converters that keep your data intact. Not sure of the other way around though. Once you're on FAT32 you will be able to read and write to the disk from both the platforms (ie win and linux).

Akshay[/QUOTE]

I mainly use this drive for ripping DVD's and if i remember correctly i've had problems making 4 gig ISO's on fat32 systems. 

Anyway, If i opt to convert it to fat32 can someone post up the cmdline to do that?  The data on the drive is non-critical. 


Rob

---

### Post by frodon on 2006-02-06
To format your drive a advice you gparted it's really easy to use.

You're right, you can't write files > 4Go on FAT32, maybe you should use ext3 file system you will have full support for linux and for windows you can install some drivers to get read support and also write support even if the write support isn't fully reliable.

---

