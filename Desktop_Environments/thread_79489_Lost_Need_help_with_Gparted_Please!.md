---
title: "Lost Need help with Gparted Please!"
date: 2005-10-20
forum: Desktop Environments
---

### Post by karuptdata on 2005-10-20
I have a 120gb HD and right now 59gb ubuntu 1.2gb Swap and 58gb ext3 filesystem mounted in /home. What i need to do is reformat the 58 gb ext 3 partition to say 20 gb for window$ install that i need and the rest for FAT32 format to share media between linux and ubuntu..Gparted will not let me edit the 58gb ext3 partition to get this going does anyone have nay idea how to get this accomplished or if theres a howto could you guys point me there i have searched this to no avail! Thanks in Advance..

---

### Post by matthew on 2005-10-20
I don't think it will let you edit the partition. If memory serves you will have to delete the 58gb partition and then create new ones in the now-empty space.

---

### Post by jackmacokc on 2005-10-20
[QUOTE=karuptdata]I have a 120gb HD and right now 59gb ubuntu 1.2gb Swap and 58gb ext3 filesystem mounted in /home. What i need to do is reformat the 58 gb ext 3 partition to say 20 gb for window$ install that i need and the rest for FAT32 format to share media between linux and ubuntu..Gparted will not let me edit the 58gb ext3 partition to get this going does anyone have nay idea how to get this accomplished or if theres a howto could you guys point me there i have searched this to no avail! Thanks in Advance..[/QUOTE]

I would recommend you not use Gparted for this, but rather QTParted. I've found it works much better for what you're trying to do.

---

### Post by matthew on 2005-10-20
[quote=jackmacokc]I would recommend you not use Gparted for this, but rather QTParted. I've found it works much better for what you're trying to do.[/quote]
That's more about preference than functionality. Both QTParted and gparted are graphical frontends for the same program: parted. Use whichever one you are most comfortable with. QTParted is nice as well.

---

### Post by jackmacokc on 2005-10-20
[QUOTE=matthew]That's more about preference than functionality. Both QTParted and gparted are graphical frontends for the same program: parted. Use whichever one you are most comfortable with. QTParted is nice as well.[/QUOTE]


Right, but I could figure it out much easier in QTParted - which was my point. Sorry if I was unclear.

---

### Post by SickTwist on 2005-10-20
Honestly, the safest way to do all of this is to wipe the hard drive, install Windows first then install Ubuntu second. How much data is stored in your /home partition? If you can back this up on CD or something then you will have all of your preferences saved.

If that is what you do, here is how I would partition the drive:
Primary Partition - ntfs (Windows installation)
*  *  Extended Partition  *  *
Logical Partition - ext3/reiserfs ( Ubuntu / ) - Ubuntu will use < 2 GB so 6 GB is more than enough unless you plan on installing lots of extras
Logical Partition - ext3/reiserfs ( /home ) - all user data is stored here
Logical Partition - fat32 - files shared between Windows and Linux
Logical Partition - Linux swap

1. Install Windows first, making the Windows partition large enough to accomodate Windows + programs. During the Windows install, just create the primary partition.

2. Install Ubuntu, using the partitioning tool during the installation to create all of the other partitions. The bootloader (grub) portion of the installer should detect Windows. (It will list it as being detected). If it does detect Windows, it is safe to write the bootloader to the MBR of the hard drive.

Grub will give you a menu that allows you to select Linux or Windows when you boot.

---

