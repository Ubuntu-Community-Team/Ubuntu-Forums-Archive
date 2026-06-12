---
title: "[SOLVED] Formatting a usb pendrive in fat32 using mkdosfs"
date: 2008-12-27
forum: General Help
---

### Post by nucleuskore on 2008-12-27
After unmounting the pendrive, and using fdisk to set the partition as W95 FAT32, and saving the partition table,I used the following command

sudo mkdosfs -F 32 /dev/sdb1

Now everything was successful, but when I try to paste files as a normal user I cannot because the owner of the filesystem is root (I had to be root to fdisk and mkdosfs).

So how do I solve this problem?

---

### Post by namdung on 2008-12-27
FAT 32 should not have permission issues.

One method:
```
sudo chmod 777 -R /media/disk
```

Just ensure that the USB is in* /media/disk*

---

### Post by vanadium on 2008-12-27
You don't need (nor want) the -R switch. However, a pen disk is normally mounted by default with permissions for the current user. I guess it would have been sufficient to fysically disconnect the drive after formatting, then connect it again to have it mounted with permissions for you as a user.

It not, then indeed you can change the permissions of the mount point, which will be remembered between successive mounts.

---

### Post by nucleuskore on 2008-12-27
Thank you for your replies.

vanadium what you mentioned worked. Thanks again

---

