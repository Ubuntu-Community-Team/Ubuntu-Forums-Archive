---
title: "OSx86 GRUB"
date: 2009-04-26
forum: General Help
---

### Post by SportsGuy2 on 2009-04-26
I am currently dual booting with Ubuntu and Vista, and am using GRUB as my bootloader. 

Is there any possible way to still have GRUB and have OSx86(instead of Darwin, Chameleon, or anything else)?

---

### Post by SportsGuy2 on 2009-04-26
bump... and I think I am going to use iPC

---

### Post by bpalmer4 on 2009-08-30
In my case - I use the GRUB chainloader to get to Darwin.

I must have installed it funny, as the boot sequence included the boot sector for the drive that has OSX86 on it. Which meant that I needed a menu.lst file a little different to most of the posts here.

/dev/sda is a backup drive
/dev/sdb is Windows7
/dev/sdc is Vista and the Linux boot
/dev/sdd is the OSX86 Hackintosh
/dev/sde has my Linux swap, /home and back-up system

Anyway, parted gives this information ... 

```
(parted) print all

Model: ATA MAXTOR STM332062 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  320GB  320GB  primary  ntfs              


Model: ATA ST3500320AS (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  500GB  500GB  primary  ntfs         boot 


Model: ATA ST3500320AS (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      32.3kB  477GB  477GB   primary  ntfs              
 2      477GB   500GB  23.0GB  primary  ext4         boot 


Model: ATA MAXTOR STM332062 (scsi)
Disk /dev/sdd: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size    File system  Name                  Flags
 1      20.5kB  210MB  210MB   fat32        EFI System Partition  boot 
 2      210MB   287GB  287GB   hfs+         Untitled                   
 3      287GB   320GB  32.6GB  hfs+         Untitled                   


Model: ATA ST3500320AS (scsi)
Disk /dev/sde: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 2      32.3kB  451GB  451GB   primary  xfs               
 3      451GB   480GB  29.1GB  primary  linux-swap        
 1      480GB   500GB  20.0GB  primary  xfs          boot 

```

And the relevant bit of GRUB looks like this ...

```

title		Vista (loader)
rootnoverify	(hd2,0)
savedefault
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


title		Windows 7 (loader)
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


title		Apple Hackintosh (loader)
rootnoverify	(hd3,1)
makeactive
chainloader	(hd3)+1

```

---

