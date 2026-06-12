---
title: "FAT32 Permissions Issue; Persistent Reversion"
date: 2009-04-25
forum: General Help
---

### Post by Kaidona on 2009-04-25
Man, I am just having all kinds of trouble with various things Windows. I just made a fresh installation of Jaunty early today (haven't gone to bed yet) after some trouble upgrading directly from Intrepid (choked bandwidth). Before the fresh install, I could mount, see, access, and write files in one of the FAT32 partitions of my secondary harddrive. Suddenly, I have no permissions at all, even to change the permissions as root. I tried making a fresh FAT32 partition to see if perhaps the fresh install did something, and still no luck.

After a couple of hours hunting around on the internet, I finally found my way to the Jaunty wiki, and the instructions there seemed to be just what I needed. I could mount the partition, change the ownership, open all permissions. I decided to test and see if Windows could see it. I could, added a few files and returned to Linux. The permissions have been reverted to read-only, and no amount of sudo commanding has changed permissions or ownership back to what I wanted.

I've removed the fstab entry, put it back in, run both chown and chmod commands, have even tried to change it using Nautilus. I have not managed to keep a single modification, and I am starting to get a bit frustrated; the partition is supposed to be my shared and backup folder for most of my art and writing. 

I know there have been other threads like this. I apologize for the repeat, but none of the others I have found have solved the problem for me. I would greatly appreciate any help anyone would deign to bounce my way.

---

### Post by dcstar on 2009-04-25
> **Kaidona said:**
> Man, I am just having all kinds of trouble with various things Windows. I just made a fresh installation of Jaunty early today (haven't gone to bed yet) after some trouble upgrading directly from Intrepid (choked bandwidth). Before the fresh install, I could mount, see, access, and write files in one of the FAT32 partitions of my secondary harddrive. Suddenly, I have no permissions at all, even to change the permissions as root. I tried making a fresh FAT32 partition to see if perhaps the fresh install did something, and still no luck.

After a couple of hours hunting around on the internet, I finally found my way to the Jaunty wiki, and the instructions there seemed to be just what I needed. I could mount the partition, change the ownership, open all permissions. I decided to test and see if Windows could see it. I could, added a few files and returned to Linux. The permissions have been reverted to read-only, and no amount of sudo commanding has changed permissions or ownership back to what I wanted.

I've removed the fstab entry, put it back in, run both chown and chmod commands, have even tried to change it using Nautilus. I have not managed to keep a single modification, and I am starting to get a bit frustrated; the partition is supposed to be my shared and backup folder for most of my art and writing. 

I know there have been other threads like this. I apologize for the repeat, but none of the others I have found have solved the problem for me. I would greatly appreciate any help anyone would deign to bounce my way.

Try unmounting the partition and doing a fsck on it (use the facility in the Partition Manager to check the drive/partition).

---

### Post by mikewhatever on 2009-04-25
The first time you mount an internal partition, it's supposed to ask you for authorisation, with an option to remember the setting. If you click remember, it's not going to ask again.

---

### Post by Kaidona on 2009-04-25
> **mikewhatever said:**
> The first time you mount an internal partition, it's supposed to ask you for authorisation, with an option to remember the setting. If you click remember, it's not going to ask again.

I had the drive set up to automatically mount when Ubuntu boots. It did ask each time I mounted it before adding its directory to the fstab, but even then I had no permissions to modify anything in it.

> **dcstar said:**
> Try unmounting the partition and doing a fsck on it (use the facility in the Partition Manager to check the drive/partition).

Just ran it, tried mounting the partition and checked the permissions. It is still greyed to root. I again tried changing ownership and permission to read/write/executable, and it still wouldn't take.

---

### Post by Dgurion on 2009-04-25
Maybe you can use NTFS? And just use ntfs-config to set it up to auto-mount?

---

### Post by Kaidona on 2009-04-25
Unfortunately, I've only run Windows 2000 with FAT32, I imagine due to the age of the harddrives I'm using, and the fact that originally I dual-booted it with Windows 98. Admittedly, I am pretty behind in the Windows scene, but I was never a fan of XP, which I recall being where the major switch from FAT to NTFS really started happening (of course, my mind could also just be a giant gas-bag at the moment). But I digress, I don't know if an NTFS would be writable with Win2000; I found a lot of complaints about NTFS being read-only while hunting for how to keep my FAT32 readable and writable after the problem suddenly sprung up.

---

### Post by myddewji13 on 2009-04-25
I had this problem too. Solved it using "Storage Device Manager" (psydm) from add/remove. Select your partition and then hit assistant. Check off mount on boot AND check off "umask for file and directory permissions in octal" AND make sure umask = 000 ...

---

### Post by Kaidona on 2009-04-25
I'm giving the device manager a try; started just with the two options specified and still had no write permissions. I just tried also specifying the owner user and group, and so far I now own the drive instead of root, but seem to have no file access permissions. I will continue to experiment with the other options and see what I can accomplish with them.

EDIT: Either changing owners to me and my user groups, or adding full permissions in the "umask for file permissions in octal" option with the system device manager seems to have made the files acessible and writable. I just tried adding a line to a Word document in Wine and it not only loaded with no problem, but saved, and the data and settings were retained after reboot. While I would have liked to have had a solution that did not use additional software, this is a major improvement, and will suit just fine unless the drive suddenly reverts again to spite me.

Thanks a bunch everyone.

---

