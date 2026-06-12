---
title: "Removing Linux"
date: 2008-12-18
forum: General Help
---

### Post by bengreer on 2008-12-18
I need help getting ubuntu off of my computer and restoring Windows to its full partition! I tried using the disk to repartition the drive but it wouldn't access the disk! It is dual booted with Windows!

---

### Post by cybrsaylr on 2008-12-18
If you're going back to MS just use MS to format the drive and start all over.

---

### Post by dagoth_pie on 2008-12-18
use the live cd to delete the ubuntu partition, that way you can use whatever tools youd use on windows to reload the partition, you will also need an xp recovery cd to run fixboot since in deleting ubuntu youll delete the grub config file

---

### Post by jerome1232 on 2008-12-18
> **bengreer said:**
> I need help getting ubuntu off of my computer and restoring Windows to its full partition! I tried using the disk to repartition the drive but it wouldn't access the disk! It is dual booted with Windows!

Which disk wouldn't access the drive, The Ubuntu Live cd or the Windows setup cd.

Also what version of Windows is this that your trying to re-install?

---

### Post by zvacet on 2008-12-18
Download [Gparted live CD]("http://gparted.sourceforge.net/") and with it delete Ubuntu partition and unallocated space add to your Windows partition or make another NTFS partition.

---

### Post by craigaa on 2008-12-18
Hi,

You have two things you need to do to completely remove Ubuntu.

1. Remove the Ubuntu partitions (root and swap) and resize the Windows partition back to the full disk size.

2. Remove Grub and return to the Windows bootloader.

Assumptions: 
1.) You have an Ubuntu live cd and can boot off of it.
2.) You are using Windows XP.
3.) You have a Windows XP Install disk. (Not a recovery disk)

Instructions:
1.) Boot off the Ubuntu Live CD.
2.) Go System > Administration > Partition Editor
3.) Unmount the swap partition.
4.) Delete the swap partition.
5.) Delete the Ubuntu partition(s). (Probably ext3)
6.) Resize the Windows partition to use the entire disk. (Probably NTFS)
7.) Ensure all changes are applied without errors.
8.) Reboot with your windows boot disk.
9.) Select the recovery console option.
10.) At the prompt type ¨fdisk /mbr¨.
11.) Restart into Windows.

Thank you for using Ubuntu and hope to see you again soon. :-)

Regards

Craig A.

---

