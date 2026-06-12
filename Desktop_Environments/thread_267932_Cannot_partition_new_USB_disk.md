---
title: "Cannot partition new USB disk"
date: 2006-09-29
forum: Desktop Environments
---

### Post by danielph on 2006-09-29
I need a bit of help here. I have a new USB disk which is showing up ok in  dmesg as follows:

```
Sep 29 17:16:10 localhost kernel: [17182375.976000] scsi4 : SCSI emulation for USB Mass Storage devices
Sep 29 17:16:15 localhost kernel: [17182380.976000]   Vendor:           Model:                   Rev: 0811
Sep 29 17:16:15 localhost kernel: [17182380.976000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Sep 29 17:16:15 localhost kernel: [17182380.976000] SCSI device sda: 16777472 512-byte hdwr sectors (8590 MB)
Sep 29 17:16:15 localhost kernel: [17182380.980000] SCSI device sda: 16777472 512-byte hdwr sectors (8590 MB)

```and this cdrom open error when I try and open the disk device in parted
```
Sep 29 17:22:33 localhost kernel: [17182759.316000] cdrom: open failed.
Sep 29 17:22:33 localhost kernel: [17182759.324000] cdrom: open failed.
Sep 29 17:22:33 localhost kernel: [17182759.332000] cdrom: open failed.
Sep 29 17:22:48 localhost kernel: [17182774.048000] usb 3-2: reset high speed USB device using ehci_hcd and address 7
Sep 29 17:23:18 localhost kernel: [17182804.292000] usb 3-2: reset high speed USB device using ehci_hcd and address 7
Sep 29 17:23:48 localhost kernel: [17182834.536000] usb 3-2: reset high speed USB device using ehci_hcd and address 7
Sep 29 17:23:49 localhost kernel: [17182834.668000] sd 4:0:0:0: SCSI error: return code = 0x50000
Sep 29 17:23:49 localhost kernel: [17182834.668000] end_request: I/O error, dev sda, sector 16777344
```

I tried to partition it using gparted, but had a problem during an operation and it hung. Before I was able to access it in parted, gparted and cfdisk and sfdisk.

Now I get the following errors:

 ```
sfdisk -l /dev/sda
/dev/sda: No such file or directory
sfdisk: cannot open /dev/sda for reading

``````
parted
Error: No device found
Retry/Cancel?
```cfdisk - fatal error cannot open disk.

Anyone got any suggestions how I can wipe the partition table?

thanks

---

### Post by x64Jimbo on 2006-09-29
sudo dd if=/dev/zero of=/dev/sda
easiest low-level format ever.

---

### Post by danielph on 2006-09-29
```
sudo dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': No space left on device
774977+0 records in
774976+0 records out
Segmentation fault

```This did give me access to parted and fdisk, but I was asked to specify number of cylinders in fdisk. I entered 1023 and this seemed to calculate the size ok, however an error occured "Inappropriate ioctl for device" see below:```
Disk /dev/sda: 0 MB, 0 bytes
255 heads, 63 sectors/track, 1023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1023     8217216   83  Linux

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 25: Inappropriate ioctl for device.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
```

After the reboot I am back to square one, I cannot see the disk.

Any suggestions please????

---

### Post by x64Jimbo on 2006-09-29
Can you try plugging it into someone else's computer and formatting it there?

---

### Post by danielph on 2006-09-29
i tried it on my laptop with exactly the same results. 

 I have just resolved the ioctl problem, it was the filesystem id needed to be vfat or ntfs - this is a firmware restriction. It doubles up as a video player when it is not a usbdisk (or it would do). 

So, the problem now is that after a reboot I am back with 

```
 sudo fdisk /dev/sda

Unable to open /dev/sda
```

Until I low level format again.

---

### Post by danielph on 2006-09-29
It would appear that after running dd
```
 sudo dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': No space left on device
774977+0 records in
774976+0 records out
Segmentation fault
```I am left with a 378MB partition. This is due to a misread of the number of cylinders, 48 instead of 1023. 


fdisk and testdisk show this and I am able to change it, but after a reboot I am back to "unable to open" and have to run dd.

errmm...............

---

### Post by x64Jimbo on 2006-09-29
Is this a video ipod, by chance? If so, use the apple restore utility.

---

### Post by danielph on 2006-09-29
No, it's nothing as funky as that, it's a usb housing with video out and a remote control. You fill it up with Xvid, divX, mpeg or even iso's of your DVD's then plug into a TV. Inside is a new 80GB WD800 disk. It will also store music and photos. 

It doesn't seem to want to play with Linux, though there really isnt a reason that it should have a problem, except perhaps the firmware.

---

### Post by x64Jimbo on 2006-09-30
The firmware could easily have something to do with it. Try connecting it to a win box and see if it works. I want to be sure what kind of problem we're dealing with here.

---

### Post by danielph on 2006-09-30
I am working on it. Had to install XP on my laptop to try it, after 2 hours of updates and patches for USB I saw the device as a USB device and even saw the disk as it connected (Hardware Device Manager), but it would not show up in Disk Manager. I will look at this more and post the conclusions for completeness, but I think we are moving out of the realms of Ubuntu desktop issues here.

It looks like I will have to get the external disk setup on FAT32 for a proper test and run it with XP, which will take some time as I need to install the external disk internally to access it. I actually think I have faulty hardware here anyway, but it's not over till the fat lady sings.

thanks for you help anyway.

---

