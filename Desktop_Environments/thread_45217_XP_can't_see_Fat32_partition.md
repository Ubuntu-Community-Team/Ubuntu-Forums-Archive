---
title: "XP can't see Fat32 partition"
date: 2005-06-29
forum: Desktop Environments
---

### Post by jcooper on 2005-06-29
Hi all, got a bit of a weird problem.

I have Hoary dual booted with XP on a PC. I added a SATA drive and booted into Hoary. Then, using gParted, I created a Fat32 partition and mounted it as /mnt/datadrive/. The idea here was to ensure all data was accessible by both Hoary and XP.

Now, booting into XP, it shows the drive in My Computer > Manage but doesn't recognise the Fat32 partition - showing only an "unknown partition".

Could Grub be hiding the partition from XP, or does XP have to create the partition itself to recognise it?

---

### Post by Granden on 2005-06-29
OnT: Sorry I cant help

OT: Just borrow your thread a bit, does linux have full write and read support to FAT32 but not NTFS? If so I hate myself for converting my external HDD from FAT32 to NTFS need to revese it now if so :P

---

### Post by nocturn on 2005-06-29
[QUOTE=Granden]does linux have full write and read support to FAT32 but not NTFS?:P[/QUOTE]

Linux has full support for fat32.

---

### Post by Granden on 2005-06-29
Okej thanks I hate myself now. But its worth it to change to fat32.

OnT: Have you put anything on that FAT32 partition or is it clean?
If its clean why not just remove it and make it under windows and mount it in linux just.

---

### Post by foxy123 on 2005-06-29
[QUOTE=jcooper]Hi all, got a bit of a weird problem.

I have Hoary dual booted with XP on a PC. I added a SATA drive and booted into Hoary. Then, using gParted, I created a Fat32 partition and mounted it as /mnt/datadrive/. The idea here was to ensure all data was accessible by both Hoary and XP.

Now, booting into XP, it shows the drive in My Computer > Manage but doesn't recognise the Fat32 partition - showing only an "unknown partition".

Could Grub be hiding the partition from XP, or does XP have to create the partition itself to recognise it?[/QUOTE]
make sure that you not only created but also formatted the partition. As I remember it's two different things...

---

### Post by Granden on 2005-06-29
[QUOTE=foxy123]make sure that you not only created but also formatted the partition. As I remember it's two different things...[/QUOTE]

If he have created a partition its not any file system but he have created a fat32 partition then it must have beened formated. And he said he created a FAT32 partition so he have prolly formated it :P

---

### Post by Akoluth of Nandus on 2005-06-29
[QUOTE=jcooper]
Now, booting into XP, it shows the drive in My Computer > Manage but doesn't recognise the Fat32 partition - showing only an "unknown partition".[/QUOTE]

This is a bug in gparted. It sets the wrong filesystem type. You can correct this by using cfdisk (cfdisk [devicename]).

Select the fat32 partiton with the up/down keys then go to "Type" in the menu below with the left/right keys and open this function by pressing enter. It displays now a list of known parition types. The one you need is 0B. Press any key and type "0B" for the filesystem type.
When you are in the main screen again write the new partiton table to the hard disk (with the "Write" menu-item).

Windows should now properly detect the partition

---

### Post by shakin on 2005-06-29
[QUOTE=Granden]OnT: Sorry I cant help

OT: Just borrow your thread a bit, does linux have full write and read support to FAT32 but not NTFS? If so I hate myself for converting my external HDD from FAT32 to NTFS need to revese it now if so :P[/QUOTE]

Look into using Captive NTFS. Full R/W support for NTFS filesystems under Linux.

---

### Post by Granden on 2005-06-29
[QUOTE=shakin]Look into using Captive NTFS. Full R/W support for NTFS filesystems under Linux.[/QUOTE]

Im lazy Im going to convert :P
but I have to read on that later but not right now I dont feel for it.

---

### Post by Ak37 on 2005-06-29
[QUOTE=shakin]Look into using Captive NTFS. Full R/W support for NTFS filesystems under Linux.[/QUOTE]

But the problem is setting Captive NTFS under Ubuntu isn't a simple thing. I don't see anyone doing it right the first time.

---

### Post by Demosthenes on 2005-06-29
[QUOTE=Akoluth of Nandus]This is a bug in gparted. It sets the wrong filesystem type. You can correct this by using cfdisk (cfdisk [devicename]).

Select the fat32 partiton with the up/down keys then go to "Type" in the menu below with the left/right keys and open this function by pressing enter. It displays now a list of known parition types. The one you need is 0B. Press any key and type "0B" for the filesystem type.
When you are in the main screen again write the new partiton table to the hard disk (with the "Write" menu-item).

Windows should now properly detect the partition[/QUOTE]

Does doing this mean losing the data on the disk, because I have the same problem but have too much data on the disk to be worth me backing up just to use in windows, since I hardly ever use windows any more.

---

### Post by Akoluth of Nandus on 2005-06-29
[QUOTE=Demosthenes]Does doing this mean losing the data on the disk, because I have the same problem but have too much data on the disk to be worth me backing up just to use in windows, since I hardly ever use windows any more.[/QUOTE]

It preserves the data on the partition as only one byte in the partition table is altered. The filesystem itself is not touched.

---

### Post by jcooper on 2005-06-30
Excellent - I'll try the cfdisk route tonight.

I have ~40Gb of data on the partition (shows how often I use XP these days!).

Thanks for your help :)

---

