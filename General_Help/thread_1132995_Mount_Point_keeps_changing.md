---
title: "Mount Point keeps changing?"
date: 2009-04-22
forum: General Help
---

### Post by snorbens on 2009-04-22
Hi,
A few days ago I created a partition for using backup via sbackup.

The mount point was originally /media/disk then yesterday it automatically became /media/disk-1 and today it became /media/disk-2 and therefore sbackup is not backing up. 

It originally backed up ok to the default of /media/disk. Then after I noticed it had changed to /media/disk-1. I changed the default and backed up ok. Now it has changed to /media/disk-2. 

I obviously do not want to keep changing the default.

Anyone any ideas of what may be going on??

Thanks

---

### Post by StuartN on 2009-04-22
If you give your partition a volume label then it will become /mnt/<volume label>

This is easy if you plug your drive into Windows (!) with a right-click for properties, but it seems you need mlabel in Ubuntu [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by snorbens on 2009-04-22
> **StuartN said:**
> If you give your partition a volume label then it will become /mnt/<volume label>

This is easy if you plug your drive into Windows (!) with a right-click for properties, but it seems you need mlabel in Ubuntu [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

Thankyou I will check that out and have a go tommorrow.

Cheers

Snorbens

---

### Post by cariboo on 2009-04-22
You can also use gparted, to change the volume label. Gparted is in the repositories. Once installed go to System-->Administration-->Partition Editor. The drive you are changing the label on has to be unmounted.

---

### Post by drs305 on 2009-04-22
Or for an ext3 partition, just run this:
```
sudo tune2fs -L <labelname> <device>
```
Example: sudo tune2fs -L windows /dev/sda1

For ntfs:
```

sudo apt-get install ntfsprogs
sudo ntfslabel <device> <label> 

```
Example: sudo ntfslabel /dev/sda1 windows

---

### Post by snorbens on 2009-04-22
Thanks all for your advice will have a go after my supper.

Once again thanks a lot.

This is one reason I love Ubuntu.............plenty of helpful advice without any prejudice against us noobs

---

