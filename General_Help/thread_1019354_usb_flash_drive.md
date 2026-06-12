---
title: "usb flash drive"
date: 2008-12-23
forum: General Help
---

### Post by xGutsAndGloryx on 2008-12-23
my flash drive isn't working on my linux pc. it works under on my windows pc. it shows up under places as a usb drive. when i put my cursor over it. it says, "Rescan Usb Drive." Does anyone know what i can do to get it to work?

---

### Post by vanadium on 2008-12-23
Have the file system of the USB drive checked. Ubuntu will not automatically mount file systems that are damaged in order to preserve your data.

---

### Post by namdung on 2008-12-23
Try using GParted to format the USB if required.

---

### Post by xGutsAndGloryx on 2008-12-23
> **vanadium said:**
> Have the file system of the USB drive checked. Ubuntu will not automatically mount file systems that are damaged in order to preserve your data.


how do you check the file system of the usb drive?

---

### Post by xGutsAndGloryx on 2008-12-23
> **namdung said:**
> Try using GParted to format the USB if required.

do you only type GParted in the command prompt?

---

### Post by vanadium on 2008-12-24
Checking a file system:

Find the device name of the partition of the USB from either one of the commands "sudo fdisk -l" or "sudo blkid".

Unmount the partition (if it is mounted).

Use the fsck command with root permissions: "sudo fsck /dev/sdb1"

/dev/sdb1 is an example of a device name for a partition.

If it is a fat partition, you will need to run dosfsck  with an option to effectively repair the disk: "sudo dosfsck -a /dev/sdb1" Alternatively, the option -r can be used for an interactive repair. This command is the equivalent to "chkdsk /f a:" in MS DOS.

Reformatting the USB is also a solution indeed, but is overkill. It will erase the data that are on the disk.

---

### Post by namdung on 2008-12-24
> **xGutsAndGloryx said:**
> do you only type GParted in the command prompt?

To install GParted: sudo apt-get install gparted
To start: sudo gparted

---

