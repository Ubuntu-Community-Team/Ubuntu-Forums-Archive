---
title: "Can Simple Backup Destination be on second HD?"
date: 2009-01-26
forum: General Help
---

### Post by Oldhacker on 2009-01-26
It does not appear that Simple Backup offers the option to set Destination on a second HD.

If it can be done, does the second HD have to already be in fstab, and what else is required?

Thanks

---

### Post by scotty64 on 2009-01-27
> **Oldhacker said:**
> It does not appear that Simple Backup offers the option to set Destination on a second HD.

If it can be done, does the second HD have to already be in fstab, and what else is required?

Thanks

Simple Backup can use a second HD as destination. You only have to make sure that the disk is mounted. If your second HD is an internal disk you will have to create a filesystem on the disk (means formatting the disk) and mount the disk. Gparted is a nice program for partitioning and formatting disks - but take care not to format your system disk accidentally. After installing gparted you will find it as "Partition Editor" in the System / Administration menu. Once the disk is formatted you need to create an appropriate entry in /etc/fstab in the case Ubuntu does not mount it automatically.
A second external (USB) disk containing a filesystem should get mounted automatically. I am currently using NTFS on my external 1Tb disk because I had permission problems with ext3.
BTW: It can take hours for simple backup to complete its task.

---

