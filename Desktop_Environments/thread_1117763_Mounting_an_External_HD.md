---
title: "Mounting an External HD"
date: 2009-04-06
forum: Desktop Environments
---

### Post by Clandestine07 on 2009-04-06
I am fairly new to Ubuntu and am trying to get data off my external HD. However Ubuntu will not auto detect it, I have been trying to manually mount the drive but I keep getting errors. Here is the data I currently have:

sudo fdisk -l
>Disk /dev/sdb: 500.1 GB, 500107862016 bytes
>255 heads, 63 sectors/track, 60801 cylinders
>Units = cylinders of 16065 * 512 = 8225280 bytes
>Disk identifier: 0xe52424c9
>
>   Device Boot      Start         End      Blocks   Id  System
>/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS



Next I do a sudo mkdir /mnt/usbdrive with no errors
Then:
sudo mount -t ntfs /dev/sdb /mnt/usbdrive

After which I get the following error:

>NTFS signature is missing.
>Failed to mount '/dev/sdb': Invalid argument
>The device '/dev/sdb' doesn't have a valid NTFS.
>Maybe you selected the wrong device? Or the whole disk instead of a
>partition (e.g. /dev/hda, not /dev/hda1)? Or the other 


Any help is most appreciated

---

### Post by Anthon on 2009-04-06
try to do:
sudo mount -t ntfs /dev/sdb1 /mnt/usbdrive
(notice the '1' after sdb), the way you do it you try to mount the complete drive (sdb) and not the first partition (sdb1)

---

### Post by Clandestine07 on 2009-04-06
Thanks for that one, drive works perfectly now!

---

