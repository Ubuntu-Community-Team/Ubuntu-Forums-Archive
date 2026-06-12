---
title: "Some help with formatting SD Card"
date: 2009-03-24
forum: General Help
---

### Post by Kaik541 on 2009-03-24
I'm currently trying to format an SD card. Only issue is I'm not using a USB card reader, but my system's built in SD/MMC reader. This device functions well enough with reading and writing to and from the SD card.

Unfortunately, because of how gparted works (I assume) its not showing up in the devices list, mounted or unmounted. It actually registers as /dev/mmcblk0 or /dev/mmcblk1 and isn't showing up in gparted.

I tried using fdisk to delete the partition table using the "o" command. Created a new partition (n). Chose primary, partition 1, default cylinder values. Selected partition 1 (t) and set it to FAT16 filesystem (6) and then attempted to write it to the SD card using the "w" command. It then outputs:

"The partition table has been altered!

Calling ioctl() to re-read partition table."

And then just hangs for an inexplicably long time. It is a standard 2 GB SD card (not SDHC). I hope some one knows how to help me with this issue. I'm waiting for the "syncing disks" response, but its not coming up.

EDIT: Yes I know, 2 GB is the very upper limit of the FAT16 file system. It still should be capable of formatting it though.

---

### Post by adult swim on 2009-03-24
to format it to fat 16 from a terminal run these commands ```
sudo umount /dev/mmcblk0

sudo mkfs.vfat -F 16 /dev/mmcblk0
``` you may need to change /dev/mmcblk0 to the correct mountpoint.

---

