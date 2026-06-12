---
title: "Fiesty: How to change USB Flash drive labels"
date: 2007-04-28
forum: Desktop Environments
---

### Post by tman_ubuntu on 2007-04-28
With Edgy, when plugging in  a usb flashdrive it mounts it with whatever brand name the flashdrive has as the label.  However, with Fiesty it puts a generic "disk" as the label.  Is there a way of making Fiesty mount the drive with a customized label as to be more intuitive for people new to linux and gnome desktop?

---

### Post by mcduck on 2007-04-29
Yes, the name comes from the disk partition label, so giving a name to the partition(s) on your flash drive will also change the name Ubuntu uses when mounting the drive.

---

### Post by Blaxter on 2007-04-29
mcduck is right, ubuntu takes the partition name. You set it when format the flashdrive. You can do that using mkfs.vfat (if u wanna fat32l) with -n parameter

> -n volume-name
              Sets the volume name (label) of the filesystem.  The volume name can be up to 11 characters long.  The default is no label.

---

### Post by tman_ubuntu on 2007-04-29
> **Blaxter said:**
> mcduck is right, ubuntu takes the partition name. You set it when format the flashdrive. You can do that using mkfs.vfat (if u wanna fat32l) with -n parameter

Hmmm.  That's weird then.  I've never formatted this drive before and Edgy labeled it different than what Fiesty is labeling it.  But it's good to know anyhow.

---

### Post by mcduck on 2007-04-29
> **tman_ubuntu said:**
> Hmmm.  That's weird then.  I've never formatted this drive before and Edgy labeled it different than what Fiesty is labeling it.  But it's good to know anyhow.

If the partition has no label then Ubuntu uses some generic name, which is probably what you are seeing now.

---

### Post by ronocdh on 2007-04-29
> **Blaxter said:**
> mcduck is right, ubuntu takes the partition name. You set it when format the flashdrive. You can do that using mkfs.vfat (if u wanna fat32l) with -n parameter
Very helpful thread for me; can you please go into more detail about the syntax of this command? An explicit example would be very informative! =)

---

### Post by mcduck on 2007-04-30
You'll find instructions how to set labels for different file systems in here: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

---

### Post by Ek0nomik on 2007-05-04
> **mcduck said:**
> You'll find instructions how to set labels for different file systems in here: [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive")

Thanks for that link.  Helped a bunch!

---

