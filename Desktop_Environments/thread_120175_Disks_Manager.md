---
title: "Disks Manager"
date: 2006-01-21
forum: Desktop Environments
---

### Post by durward on 2006-01-21
I am running currently 3 Linux machines:

  1. Asus P2B, Pentium II-MMX 450 MHz Dechutes, RAM 128MB;  boot: WD WDC-AC28400R 8.46GB (/dev/hda); Seagate ST33232A 3.23GB (/dev/hdb); Adaptec AAA133 SCSI controller; 4x IBM DGHS09U 9.17GB (/dev/sda, sdb, sdc, sdd); video: Voodoo3-3000 3DFX 16MB vidram; CD: Imation IMW121032IAM CD Burn-R; OS: Ubuntu Breezy Badger.

  2. Asus A7V-E, AMD Duron 750 MHz, RAM 384MB; Adaptec AHA2940U/UW SCSI controller; boot: WD WD45 Ultra2 4.24GB (/dev/sda); IBM DCHS04U 4.20GB (/dev/sdb); WD WDE9100 9.1GB (/dev/sdc); CD ROM; OS: Ubuntu Breezy Badger

  3. Compaq Presario 1200, AMD K6-III 533MHz, RAM: 128MB, 30GB HDD; DVDROM; OS: Ubuntu Hoary Hedgehog

On the two Breezy Badger machines, the Disks Manager recognizes only the first two hard drives. It will not allow partitioning nor repartitioning: Create and Delete are greyed out. And help will not work: 
   Could not display help
Unable to find the help files in either /usr/share/gnome/help/disks-admin/disks-admin or /usr/share/gnome/help/disks-admin.  Please check your installation.

All the drives are usable on both computers as they are mounted in the fstab.

What is wrong with the Disks Manager?

---

### Post by professor_chaos on 2006-01-21
is the drive you want to partition, mounted when you try?
If so, I don't think you can partition a mounted drive. Someone correct me if I'm wrong here. You may need to partition, while booting into another partition.

---

### Post by durward on 2006-01-21
My question is: Why does Disks Manager not work?

I ran it when the new drives were not partitioned, then when partitioned but not formatted, and then when they were partitioned and formated. It did not show the drives in any of the cases and does not show them now. It only shows the boot drive, the floppy drive and the CDROM drive.

Durward T. Stockman

---

