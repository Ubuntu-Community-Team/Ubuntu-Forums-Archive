---
title: "Please help, I can't write files to my internal hard drive"
date: 2006-09-26
forum: Desktop Environments
---

### Post by thenetduck on 2006-09-26
Hi, 
  I have an internal hard drive (slave) and I can read files from it just fine, however, I can't write files to it. I need help figuring this one out. Thanks, 

 The Net Duck

---

### Post by Warbo on 2006-09-26
It depends on what filesystem the drive's partitions use. If it is ext3, reiserfs, xfs or any other linux-friendly filesystem then just make sure the permissions are setup for your user to write to the folder it is mounted in (use "man chmod" to see how to set change these).

If it is VFAT (like FAT32) then you may need to remount it and give access for your user. This would be done with "sudo mount /path/to/mount/point /path/to/mount/point -o remount, uid=YourUsername" The option uid=YourUsername (obviously with that value replaced) can be added to the file /etc/fstab by running "gksudo gedit /etc/fstab" so it will mount with that option at boot.

If the filesystem is NTFS then write support isn't included by default. Look around the forums for "ntfs-3g" if you REALLY need to write to it.

---

