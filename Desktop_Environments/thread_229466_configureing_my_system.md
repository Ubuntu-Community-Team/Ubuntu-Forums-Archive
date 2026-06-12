---
title: "configureing my system"
date: 2006-08-04
forum: Desktop Environments
---

### Post by jdm2 on 2006-08-04
I have just install ubuntu 6.06 on a 80 gb hard drive and I have a second hard drvie which is 160 gb.  I want to use the 80 gb as the drive for ubuntu and i want to use the 160 gb as a extra drive for stoge.  How would i go about that?  Thanks

---

### Post by ifokkema on 2006-08-04
Is the second drive partitioned/formatted yet? If you're not too familiar with the command line (fdisk, /etc/fstab and such), I would use gparted to partition/format the disk and System->Administration->Disks for setting the mountpoint(s).

HTH!

---

### Post by jdm2 on 2006-08-04
I have it formatted with extended 2 but I can change that right?

---

### Post by ifokkema on 2006-08-04
> **jdm2 said:**
> I have it formatted with extended 2 but I can change that right?
Sure, gparted allows you to partition or format your drive, also formatting it under a different filesystem type.
Then with the disk administration mentioned above, you can specify where the drive's partition(s) mount on your system.

---

### Post by jdm2 on 2006-08-04
I want to be able to use it as a backup drive for my docs.  Do I need to format it as a primary drive and what format or do I partion it as a extended partition?  Thanks

Also what path should I put it under?  Thanks

---

### Post by ifokkema on 2006-08-04
> **jdm2 said:**
> I want to be able to use it as a backup drive for my docs.  Do I need to format it as a primary drive and what format or do I partion it as a extended partition?  Thanks

Also what path should I put it under?  Thanks
Primary partition is just fine.
Basically, you can put it under whereever you want, such as /backup or so. You should create the directory where you want it first, so if you want to use /backup, you should run:
```
sudo mkdir /backup
```
Then you can select it as the 'access path' in the disks manager.

---

### Post by jdm2 on 2006-08-04
What Should I Format The Drive With?  Thanks

---

### Post by ifokkema on 2006-08-04
> **jdm2 said:**
> What Should I Format The Drive With?  Thanks
Gparted:
```
sudo apt-get install gparted
sudo gparted
```
- Select the drive in the upper right corner. You see your ext2 partition.
- Right click your partition and select 'Format to', and select ext3.
- After formatting, click apply in the menu and quit.

Your drive is now formatted and ready to be mounted.

---

### Post by jdm2 on 2006-08-04
Thanks for all the help.

---

### Post by ifokkema on 2006-08-04
> **jdm2 said:**
> Thanks for all the help.
You're welcome! Be sure to check back if you run into anything else.

---

### Post by jdm2 on 2006-08-04
I'm having trouble formating the drive to ext 3 it wants to stay ext2.  Any ideas?  Thanks

Also it won't let me write to it or excute it.  Can you help?  Thanks

---

### Post by ifokkema on 2006-08-04
> **jdm2 said:**
> I'm having trouble formating the drive to ext 3 it wants to stay ext2.  Any ideas?  Thanks
What's the error you're getting from gparted?
Does it help to remove the partition and create a new one?

---

### Post by jdm2 on 2006-08-04
I think I have where I can write to it but the thing is the drive isn't appering in the computer area.  Any ideas?  Thanks

---

### Post by ifokkema on 2006-08-04
Have you added an Access path (mount point) in System -> Administration -> Disks?

---

### Post by jdm2 on 2006-08-04
yes and the format is still ext2 but that's ok I just want to be able to write to it.  I think I have the writing to it working but it just doesn't apper in the computer area.  Here's the access path
/mnt

---

### Post by ifokkema on 2006-08-04
OK, in the console, type:
```
mount
```
It should read something similar to
/dev/hdb1 on /mnt type ext2 (rw)
If so, your new drive is mounted. Then, open the file manager and navigate to /mnt. Click 'Bookmarks' (in the menu) -> Add bookmark. This will add the /mnt to the bookmark list, also available under 'Places' in the Gnome menu.

---

