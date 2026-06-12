---
title: "USB Drive"
date: 2007-03-12
forum: Desktop Environments
---

### Post by kensmith on 2007-03-12
I am usbuntu and have been for the last 4 months with no trouble. However I just got around to getting a usb external hard drive kit and putting my windows 2000 drive in it. I am wanting to save the data to my linux disk. The linux knows the drive is there but its a shda drive. I can't mount it or see anything on this drive.
Any suggestions.

---

### Post by ajgreeny on 2007-03-12
I don't quite know what your question is about, I'm afraid.  Do you mean you have windows 2000 formatted as ntfs on the usb drive, or is it a linux OS formatted as ext3?  Also is this a standard internal drive that you have placed in an external usb enclosure case?

I presume you know that you can't yet guarantee writing to an ntfs drive, though if mounted properly you should be able to read it.  Just to get the picture straight, what is the output of entering the following in a terminal?
sudo fdisk -l

If the usb disk is listed then at least you can rest assured that the system has found it and it just needs mounting.

---

### Post by kensmith on 2007-03-12
ken@ken-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2392    19213708+  83  Linux
/dev/hda2            2393        2498      851445    5  Extended
/dev/hda3            2499        9726    58058910   83  Linux
/dev/hda5            2393        2498      851413+  82  Linux swap / Solaris

Disk /dev/sda: 33.8 GB, 33820284416 bytes
255 heads, 63 sectors/track, 4111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1023     8217243   55  EZ-Drive
ken@ken-desktop:~$

I am wanting to remove data from a windows 2000 disk that is in a usb external drive.

---

### Post by ajgreeny on 2007-03-13
This is slightly wierd in that the output doesn't show the system type of the sda drive in a form that I know, just EZ-Drive, which means nothing to me.  Sorry I can't help more, but I'm sure somebody else will help out on this.

---

### Post by eggdeng on 2007-03-13
> **kensmith said:**
> The linux knows the drive is there but its a shda drive. I can't mount it or see anything on this drive.
How did you try to mount it?

---

### Post by Duggeek on 2007-03-13
Hrm... EZ-Drive. That's the RIdata device, isn't it? I'm surprised that Linux recognizes it as the file-system, rather than just the device. (like **lsusb**)

There's only one other "EZ-Drive" I know, but it's a hard-drive utility for IDE/UDMA and has little or nothing to do with USB devices.

I found a [product review]("http://www.livedigitally.com/2005/11/01/review-of-ridata-ezdrive-usb-20-flash-drive-pro/") online and it appears to come packaged with some data-security software. It's likely that the drive is *pre-encrypted* so it can't be read easily. 

When you first used this drive in Windows, it would have encouraged you (with the option to cancel, I'm sure) to install special security software for the drive. That's what you did, yes?

If this is in fact the case, then the data on the drive is *patently unreadable*. It's not Linux, though, it's the software in Windows that re-wrote the drive format. You could take that drive to another Linux box, a Mac, and even an unrelated Windows machine and I bet it wouldn't read properly *anywhere*.

Guess that security software works pretty well after all, yeah?

Restart your machine to Windows again, insert the drive and move all the files that you put on there to a folder on the desktop. When that's done, un-install the security software, (unless you want to wait for a Linux port) re-format the drive as regular FAT and put the files on again.

Shouldn't be any problem after that.

---

