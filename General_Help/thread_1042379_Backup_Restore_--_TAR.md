---
title: "Backup Restore -- TAR"
date: 2009-01-17
forum: General Help
---

### Post by Mercedes300 on 2009-01-17
I've got an Ubuntu file server with six clients each running their own local session of Ubuntu with /home directories residing on the file server along with a central storage area for data.

In attempting to prepare for the eventual failure of the clients' boot drives, I created a TAR file of the contents of the boot drive excluding /home, /proc, /media, /lost+found, /sys, /mnt, and the system wide mass storage directory over the network.

I installed a fresh hard drive, booted with LiveCD, partitioned the hard drive with gparted, and unballed the TAR file to it.  I then created the excluded directories and rebooted.

The system fails to boot and reports:
  Alert! cat /dev/disk/by-uuid/fc188f5f-12db-430e-bffe-4b9ee9a36d32

Any hints?

Thanks for any help.

---

### Post by taurus on 2009-01-17
It's because the UUID for the new harddrive is not matching up with the one from the backup.  Therefore, Ubuntu is unable to boot since it can't mount the root partition, /.

You can look it up to see what the new UUID is.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
```
Then, you need to mount that root partition and change the UUID in /boot/grub/menu.lst & /etc/fstab to reflect the new one.

---

### Post by Mercedes300 on 2009-01-17
> **taurus said:**
> It's because the UUID for the new harddrive is not matching up with the one from the backup.  Therefore, Ubuntu is unable to boot since it can't mount the root partition, /.

You can look it up to see what the new UUID is.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
```
Then, you need to mount that root partition and change the UUID in /boot/grub/menu.lst & /etc/fstab to reflect the new one.


Thanks! That worked!

Tar is fast! I think I like this method of backup!

---

