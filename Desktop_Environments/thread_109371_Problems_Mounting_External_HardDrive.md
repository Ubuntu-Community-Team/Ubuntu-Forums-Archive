---
title: "Problems Mounting External HardDrive"
date: 2005-12-28
forum: Desktop Environments
---

### Post by diffuser78 on 2005-12-28
I recently bought an internal 160GB Seagate HDD. I use USB connector to make it an external one. I have formatted it using FAT32. When I plug the USB into my Ubuntu desktop it doesn't recognize it and doesn't show up anything. For all other mountings my Ubuntu Desktop shows right away. My Laptop Ubuntu does recognize this Hard drive.

Whats wrong with my Desktop. Can somebody suggest something ?

Thanks guys for your time

---

### Post by art on 2005-12-28
But can you mount it manually? I was having a similar issue, with no automount, but was able to manually mount it.

---

### Post by diffuser78 on 2005-12-28
[QUOTE=art]But can you mount it manually? I was having a similar issue, with no automount, but was able to manually mount it.[/QUOTE]

Since I am connecting using my hard drive using the USB, can somebody throw some pointers how to mount it manually.

Automount works like a charm for my Ubuntu lapto but it doesn't work here for this hard drive ( though it works for other ones). Is there any specific reason or I am missing something.

thanks

---

### Post by art on 2005-12-28
when you do 

sudo fdisk -l

what do you get?

---

### Post by diffuser78 on 2005-12-28
[QUOTE=art]when you do 

sudo fdisk -l

what do you get?[/QUOTE]


   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       13900     105083968+   7  HPFS/NTFS
/dev/hda2           13901       20673    51203849    f  W95 Ext'd (LBA)
/dev/hda5           13901       14039     1050808+   6  FAT16
/dev/hda6           14040       14177     1043248+  82  Linux swap / Solaris
/dev/hda7   *       14178       20673    49109728+  83  Linux

---

### Post by art on 2005-12-28
This is with external HDD plugged to the computer in and powered on? Try doing 

sudo mkdir /media/USB
sudo mount /dev/sda1 /media/USB
See if that works...

---

### Post by Krash1201 on 2005-12-28
i am having this same problem, and followed the specified possible fixes, but the out put was the following:

mount: special device /dev/sda1 does not exist

does it make any difference if the usb drive is a sata drive?  any other possible fixes?  thanks.

---

### Post by art on 2005-12-28
When you have the HDD plugged in and powered up, do a

sudo fdisk -l 

what does that say? Also just to see what you have under /dev do 

ls /dev/sd followed by a double TAB key, just to see what options you have there, maybe it's a /dev/sdb or something

---

### Post by dcstar on 2005-12-28
[QUOTE=diffuser78]I recently bought an internal 160GB Seagate HDD. I use USB connector to make it an external one. I have formatted it using FAT32. When I plug the USB into my Ubuntu desktop it doesn't recognize it and doesn't show up anything. For all other mountings my Ubuntu Desktop shows right away. My Laptop Ubuntu does recognize this Hard drive.

Whats wrong with my Desktop. Can somebody suggest something ?

Thanks guys for your time[/QUOTE]
Is usbmount installed?

Is pmount installed?

---

### Post by firenurse4 on 2005-12-29
I have had problems with automounting before and found the problem to be with a daemon called gnome-volume-manager.  My fix was to remove that package and then reinstall it.  I have reported that before as a bug and it seems others have as well.

---

### Post by draconas on 2006-01-06
Where do I find the usbuntils console to use?

---

