---
title: "Unable to Format USB drive (Olympus)"
date: 2009-02-27
forum: General Help
---

### Post by keyshawn on 2009-02-27
EDIT: I double posted, please see [http://ubuntuforums.org/showthread.php?t=1082139](http://ubuntuforums.org/showthread.php?t=1082139) instead.

Hi, 

I am trying to format a USB drive (it's actually a Olympus WS-300M, a digital voice recorder, but it acts like a USB drive. It normally mounts to the computer like a typical USB drive). in ubuntu 8.10. At this point, I'm not concerned about recovering any data on the drive. The device has worked with linux smoothly in the past, but the device has become corrupted (not sure how it happened) The device appears in nautilus, but none of the files within the device appear. 

Also, 
The drive does not appear in gparted but it does mount, because: sudo fdisk -l returns: 

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         500      255786    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 44) logical=(0, 6, 12)
```After doing some searching,
I read [http://ubuntuforums.org/showpost.php?p=4558786&postcount=3](http://ubuntuforums.org/showpost.php?p=4558786&postcount=3)

and followed the directions. 

After unmounting the drive, I issued: sudo mkdosfs -v -F 16 /dev/sdc1
This returned:
```
mkdosfs 2.11 (12 Mar 2005)
mkdosfs: unable to open /dev/sdc1
```
Right now, I'm trying to find other ways to format this USB hard drive.

thanks, 
keyshawn

---

