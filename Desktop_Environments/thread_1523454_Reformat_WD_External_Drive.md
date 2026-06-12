---
title: "Reformat WD External Drive"
date: 2010-07-03
forum: Desktop Environments
---

### Post by shadowfax1 on 2010-07-03
Just bought a 'my passport essential' wd external drive.  Before putting anything on it I want to get rid
of the partition that holds a windows exe for backing up and some security features.

Not sure whether its a hidden partition but wondered whether the on-board disk utility could achieve the same as 'f' disc used to.

---

### Post by scrapmetal on 2010-07-03
If it is the same as my USB WD 500Gb Passport Drive.
No hidden anything, just a windose autostart that goes to a WD splash screen.
I made a folder of Windoze on the drive and placed the autostart and WD splash in it.
Kept the Fat32 format and left it at that for now.
Do not see why you could not use FDISK to format it as a ext3 or ext4 if you wished to.
But I am keeping the fat32 so it is usable with as many machines as possible.
Ubuntu, Kubuntu etc have no problems with it, or its twin, yes my partner has one for photographs only.
The only problem I have had with hidden machine code was on a USB 2 Gb stick.
Did not follow manufactures instructions to remove a virtual CD on it which was there for widows users. Tried reloading what I had removed from the manufactures web site and then - using there removal tool. Did not work, so am stuck with a virtual CD load called - "U3" every time i use it. Have not purchased a Toshiba USB since.
Hope this helps.
If not please supply some more information of what drive specs, files on drive, what you require to do with said drive after formating to your desired requirements.

---

### Post by shadowfax1 on 2010-07-03
So if I unmount the drive and choose ntfs that should do it.
Not interested in keeping the windows programs.

---

### Post by scrapmetal on 2010-07-03
I only recommend fat32 if you use smaller files, seems quicker to me.
But NTFS is working fine on both drives, so yes, not knowing just what files "???.exe" is on it.

Question: Are you formating this drive in Windows or Ubuntu?
You would need the drive mounted to use "Partition Editor" in System - Administration, once you installed it.
**WARNING: Learn how to use this program before playing around with it. It is possible to do damage if you use it unwisely.**

1. Mount drive.
2. Start "Partition Editor"
3. Select removable drive. Thats why it must be mounted to be seen.
4. Select desired format from drop down menu.
Format removable drive. - worked for me. -good luck.

---

