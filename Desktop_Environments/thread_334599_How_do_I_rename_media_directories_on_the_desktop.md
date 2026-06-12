---
title: "How do I rename media directories on the desktop?"
date: 2007-01-09
forum: Desktop Environments
---

### Post by Quillz on 2007-01-09
I have two external hard drives that are connected to my desktop, and two icons on the desktop connect to them. The two hard drives are called "usbdisk" and "External 2" all throughout the OS (including the desktop icons,) and would like to rename them to something more sensible. But I can't figure out how to do this. I've tried sudo, and I still got an error message that wouldn't let me rename them.

---

### Post by M_the_C on 2007-01-09
I'm not certain when it comes to USB devices, but when a CD is mounted it takes the CDs Label that is made when burning the disc.

I think it might be something like that and you have to change it when formating the drive.

Or you might be able to do it by unmounting the drive and remounting it to a folder you create.

---

### Post by Quillz on 2007-01-09
Yes, I know about renaming CDs, but I thought when you were in root, you could do anything?

On a similar note, can I rename "Filesystem" to something else? I'd prefer to call it "Hard Drive," if possible.

---

### Post by M_the_C on 2007-01-09
I might have found it.  Are the drives connected all of the time?  If so:

unmount the drive, then make a folder in /media called whatever you want.

Then just remount the drive.  You need to find where it is located so just use fdisk -l.

---

### Post by Quillz on 2007-01-09
> **M_the_C said:**
> I might have found it.  Are the drives connected all of the time?  If so:

unmount the drive, then make a folder in /media called whatever you want.

Then just remount the drive.  You need to find where it is located so just use fdisk -l.
The drives are always connected, but I could merely turn them off and on again to remount them.

---

### Post by M_the_C on 2007-01-09
This is how I did it with a USB pen drive.

First I unmounted it.
```
sudo umount /media/usbdisk
```
Then I did
```
fdisk -l
```
to find the location.
In my case it was
```
Disk /dev/sda: 128 MB, 128188416 bytes
50 heads, 32 sectors/track, 156 cylinders
Units = cylinders of 1600 * 512 = 819200 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         157      125136    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(838, 49, 32) logical=(156, 21, 32)

```
Then I created a new folder
```
sudo mkdir /media/myusb
```
and finished by mounting it to the new folder
```
sudo mount -t vfat /dev/sda1 /media/myusb
```

If you leave the drives connected most of the time, you could just add a line in the fstab.

---

### Post by Rhubarb on 2007-01-09
Yes this can be done (I've done it and it works fine here)
The info can be obtained from:
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

Have a good read of the relevant parts of the article then you should be able to rename it yourself.
Make sure you backup any data that's on your USB driver before attempting anything.

The relevant lines that allow you to name (and format - not sure if it has to be formatted to allow you to rename) a partition:
```
sudo mkfs.vfat -F 32 -n dapper /dev/sda1
sudo mkfs.ext2 -b 4096 -L casper-rw /dev/sda2
```
The 1st partition on the USB drive will be formatted as FAT32 with a label "Dapper".
The 2nd partition on the USB drive will be formatted as EXT2 with a label "casper-rw".

When such a USB drive is plugged into my system, the new mounts "Dapper" and "casper-rw" come up on my Desktop.

**EDIT: Unlike M_the_C's post above, the USB disk's label will correctly appear on ANY pc you plug it into.
And make sure you do a "fdisk -l" to check if it's sda1 / sda2.
Please be sure to read the link, it contains important info like unmounting and formatting the USB disk. - There's no need to set it as Bootable though!


... Now that I can make an Edgy bootable install USB disk, I might try to install Edgy on a USB disk - a portable Operating System!  Wow!  Much cheaper than a laptop!

---

### Post by Quillz on 2007-01-09
> **M_the_C said:**
> This is how I did it with a USB pen drive.

First I unmounted it.
```
sudo umount /media/usbdisk
```
Then I did
```
fdisk -l
```
to find the location.
In my case it was
```
Disk /dev/sda: 128 MB, 128188416 bytes
50 heads, 32 sectors/track, 156 cylinders
Units = cylinders of 1600 * 512 = 819200 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         157      125136    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(838, 49, 32) logical=(156, 21, 32)

```
Then I created a new folder
```
sudo mkdir /media/myusb
```
and finished by mounting it to the new folder
```
sudo mount -t vfat /dev/sda1 /media/myusb
```

If you leave the drives connected most of the time, you could just add a line in the fstab.
Could you elaborate more on "adding a line to the fstab?" Beyond that, though, this worked for one of my external hard drives. I was able to mount the second one properly under a new name, but it still shows up as EXTERNAL 2, so I'll probably just leave it alone.

Also, is it possible to rename "Filesystem" to something else?

---

### Post by mcduck on 2007-01-15
The easier way to change the labels is to rename the partitions: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by Quillz on 2007-01-15
> **mcduck said:**
> The easier way to change the labels is to rename the partitions: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")
Those instructions didn't work for me, so I just reformatted on of my external hard drives. It is now renamed as "usbdisk-2," which is fine with me.

---

