---
title: "problem with usb external hard disk"
date: 2011-11-18
forum: Desktop Environments
---

### Post by forsubhi on 2011-11-18
I have very strange problem with my hard disk I have two partition of ntfs on it and when I move files or create files on it and plug it out then plug it in the files go away (not existed) ,what is the problem ?

---

### Post by BillyBoa on 2011-11-18
Try to defrag the drive

---

### Post by BillyBoa on 2011-11-18
Obviously your HDD is failing and the computer is making a CHKDSK and pass them to hidden files, named dir.0001 and so on.

Try to make visible the hidden files in your Explorer or search for them through Ubuntu.

---

### Post by ajgreeny on 2011-11-18
Are you removing the external disk properly, either unmounting it or ejecting it first before you unplug it?

If you don't do that your ubuntu system will see the disk as still in use and not be able to mount it again.

---

### Post by forsubhi on 2011-11-18
I try safely remove but I receive the message 
Failed to eject medium; one or more volumes on the medium are busy.

---

### Post by BillyBoa on 2011-11-18
> **forsubhi said:**
> I try safely remove but I receive the message 
Failed to eject medium; one or more volumes on the medium are busy.

If you are in Ubuntu check to see if you have installed the ntfs-3g driver.

From a terminal

```
sudo umount /media/external
```

Or go to Disk Utility and unmount the USB with right click.

Boot to your Windows part and do what I said to my comment above. Do a CHKDSK and try to unhidden the files.

---

