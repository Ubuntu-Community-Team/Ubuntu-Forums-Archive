---
title: "I Love ubuntu but..."
date: 2009-06-07
forum: General Help
---

### Post by Zaba5 on 2009-06-07
..i want windows back. I love Ubuntu and everything but windows supports more. So i tried putting in my windows XP disk and rebooting but nothing happend. Even when i go to the cd drive there is nothing in there. What should i do?

---

### Post by brotherlen on 2009-06-07
is it a legit copy of XP? As in, it couldn't accidentally get erased? Also, did you go into the BIOS of your computer before the OS boots up and select boot from CD/DVD before HDD?

---

### Post by Locutus_of_Borg on 2009-06-07
windows supports more yet the install cd doesnt work...

---

### Post by Tipped OuT on 2009-06-07
> **Locutus_of_Borg said:**
> windows supports more yet the install cd doesnt work...

It has nothing to do with Windows. Either he's not doing something right, or the installation disk is not legit. If so, it could've been burnt wrong, or the ISO is not bootable.

---

### Post by Therion on 2009-06-07
Is this a Windows XP install disk?  Does it have Service Pack 1 on it (it will say it has SP-1 on the CD itself if it does)?  

If it does NOT have SP1, *and* you are trying to install to a SATA hard drive, the problem is that Windows XP, pre-Service Pack 1, does not have native SATA drivers.  This makes installing it to a SATA drive a tad tricky.

Before plunging into the gory details of how, exactly, to modify your BIOS settings in order to get around this, can you first tell me if this is indeed your situation?

---

### Post by pastalavista on 2009-06-07
Boot to the Ubuntu Live CD and open [System > Administration > Partition Editor] then unmount and delete your Ubuntu partition. Then reformat the drive to NTFS or FAT32. Windows can't read or do anything with a Linux filesystem. It thinks you have no hard drive.

And I apologize for a previous comment you may have gotten that has since been removed by the forum admns. I was very impolite.

EDIT: > So i tried putting in my windows XP disk and rebooting but nothing happend. Even when i go to the cd drive there is nothing in there.

how do you "go to the cd drive"?

---

### Post by jerome1232 on 2009-06-07
> **Tipped OuT said:**
> It has nothing to do with Windows. Either he's not doing something right, or the installation disk is not legit. If so, it could've been burnt wrong, or the ISO is not bootable.

^
This, it's a bad cd, or your bios isn't set up to boot from cd.

Having unknown partitions won't cause Windows to not see the hard drive, having no hard drive (xp and sata controllers often don't get along) will still let you start the setup process and then complain about not finding a drive.

---

