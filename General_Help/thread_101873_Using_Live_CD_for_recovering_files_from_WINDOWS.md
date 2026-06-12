---
title: "Using Live CD for recovering files from WINDOWS"
date: 2005-12-10
forum: General Help
---

### Post by maxtors on 2005-12-10
I have a windows laptop that my brother got fustrated with, and hit his hand on the haddisk......  The windows boots up but on login the "BLUE SCREEN OF DEATH" shows up and it reeboots... so them i told my dad i could try to get the family pictures from the bad windows HDD......


So all i want to do is to get all the pictures from the HDD to an external HDD using ubuntu live cd...

1) is this possible
2) if so, make a simple way of doing this :smile: 

:KS THANKS IN ADVANCE :KS

---

### Post by ubuntu27 on 2005-12-10
I am not an expert, but, I believe that you could mount Windows from a Live CD, if not, then there must be other solution.

What File System does your Windows OS use? NTFS? FAT, FAT32 ?

If your OS is Windows XP, then it is more likely that it is using NTFS.

Try this: [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

### Post by aysiu on 2005-12-10
[QUOTE=maxtors]
So all i want to do is to get all the pictures from the HDD to an external HDD using ubuntu live cd...

1) is this possible[/quote] Yes! As long as you can boot from a CD-ROM, yes! If you don't appear to be able to do this, check your BIOS settings (usually entered by pressing Delete, F2, or Escape during bootup).
> 
2) if so, make a simple way of doing this :smile: 

:KS THANKS IN ADVANCE :KS Download a [Knoppix live CD ISO](ftp://mirror.cs.wisc.edu/pub/mirrors/linux/knoppix/KNOPPIX_V4.0.2CD-2005-09-23-EN.iso), burn it as a disk image, boot the disk.  The Windows partition and the external hard drive should automatically appear on the desktop, just copy and paste the files graphically.

---

