---
title: "NTFS RAID0 Recovery"
date: 2009-05-09
forum: General Help
---

### Post by Xel07 on 2009-05-09
I have 3 harddrives:
Two 150Gb Raptors in a RAID0 Configuration that is hardware based created on the onboard motherboard controller (Motherboard is: EVGA 132-CK-NF78-A1 LGA 775 NVIDIA nForce 780i SLI ATX Intel Motherboard). These have Windows XP 64-bit on them.

The other harddrive is for Ubuntu.

Recently, my Windows stopped working. I cannot even enter safe mode, I blue screen the moment I select my boot option, apparently due to a messed up hal.dll.

What I want to do is at least salvage some of the files on the RAID array. Is there a way to do that via mounting to linux? If so, are there any simple step-by-step guides?

---

### Post by cariboo on 2009-05-09
The first thing to check, is to see if the drives show up in fdisk. Open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

This command will print out a list of your hard drives and partitions. Could you paste the output in your next post.

---

### Post by Xel07 on 2009-05-10
The output of sudo fdisk -l is:

```

Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca21ca21

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000101

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2085        4178    16809999+   0  Empty
Partition 1 does not end on cylinder boundary.
/dev/sdb2            2220        2220           0    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdb3               1          86      688768   1f  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdb4          122702      124742    16386185+  56  Golden Bow
Partition 4 does not end on cylinder boundary.

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00079db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris
```

---

### Post by DeMus on 2009-05-10
> **Xel07 said:**
> I have 3 harddrives:
Two 150Gb Raptors in a RAID0 Configuration that is hardware based created on the onboard motherboard controller (Motherboard is: EVGA 132-CK-NF78-A1 LGA 775 NVIDIA nForce 780i SLI ATX Intel Motherboard). These have Windows XP 64-bit on them.

The other harddrive is for Ubuntu.

Recently, my Windows stopped working. I cannot even enter safe mode, I blue screen the moment I select my boot option, apparently due to a messed up hal.dll.

What I want to do is at least salvage some of the files on the RAID array. Is there a way to do that via mounting to linux? If so, are there any simple step-by-step guides?

You have Ubuntu next to Windows, in a dual boot? Then use this:

Auto mount Windows disks
Fire up a terminal, to do this click Applications > Accessories > Terminal
Then type (or copy/paste) the following - 1 line at a time
Code:
sudo aptitude update
sudo aptitude install ntfs-config
Ok so when that returns you to user@pcname, that should be installed                 

Next, make sure you have NO drives mounted (they'll usually appear on your desktop). If you have disks mounted, right-click the icons (one by one) and choose unmount.
Then run the program from System > Administration > NTFS Configuration Tool

Enter your password when prompted - and choose the drives that you want to be automounted. Click Apply.

Now simply make sure that "Enable Write Support for Internal Drives" and click OK.

Success.

---

### Post by Xel07 on 2009-05-10
DeMus -

I followed your instructions exactly, but I cannot seem to find any difference. It appears as though nothing has happened after using the NTFS Configuration Tool.

---

### Post by DeMus on 2009-05-10
> **Xel07 said:**
> DeMus -

I followed your instructions exactly, but I cannot seem to find any difference. It appears as though nothing has happened after using the NTFS Configuration Tool.

Did you manage to add your windows disk(s) in the config tool?
Did you allow the disks to be written on?
You don't get an icon (or icons) on your desktop representing the Windows disk(s)?
That's strange, in my case and also others since I have written this text in other threads as well, it worked.
When you open Nautilus (Place - Home Folder) do you see in the left column of the screen your windows disk(s)?

---

### Post by Xel07 on 2009-05-10
This is the dialogue that I got when I followed your instructions. Is this what I'm supposed to be seeing? Because after clicking "OK", there is no noticeable change in my system or my home folder.

[CENTER][IMG]http://img149.imageshack.us/img149/5656/screenshotntfsconfig.png[/IMG]
[/CENTER]

---

### Post by Xel07 on 2009-05-14
Anyone else have suggestions?

---

### Post by Xel07 on 2009-05-15
I was able to finally mount it via these two commands:

sudo mkdir /winRaid
sudo mount -t ntfs /dev/mapper/nvidia_eebehjcb1 /winRaid

winRaid is just a folder that I made to mount the Windows partition to. nvidia_eebehjcb1 comes from the second thing returned when I entered:

sudo dmraid -ay

I was hoping that this would allow me to fix my busted hal.dll by doing some quick editing or copy/past, but it seems more complicated than that. I think I'm going to just end up reinstalling windows after copying all my files to an external hardrive.

---

