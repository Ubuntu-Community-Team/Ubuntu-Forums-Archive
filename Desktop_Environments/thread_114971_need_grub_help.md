---
title: "need grub help"
date: 2006-01-09
forum: Desktop Environments
---

### Post by blu.gecko on 2006-01-09
I am building a new desktop machine. I want to write the mbr (grub) to floppy and not the partition, is there a way to do this after the installation and then erase the grub from the partition so other operating systems will boot normally. I realize that ubuntu will have to go on 1st so that the other OS will not over write any settings.

here are the new system specs:
Intel p4 mainboard
P4 2.4 retail
1024 ddr 400mhz
80gig sata150
samsund dvdrw
floppy
ATI ASUS 9200SE 128mb video

---

### Post by thekiller on 2006-01-09
I dont know why would you want to erase grub after the installation. If you define everything correctly in /boot/grub/menu.lst, all operating systems on the machine should boot perfectly. However, making a bootable floppy is a plus just in case something messes up during the install process.

---

### Post by bikeman on 2006-01-10
Actually, you may be able to install Ubuntu last depending on what other operating systems you want to install.  I cannot speak for other operating systems, but I have Windows XP on my home PC.  I have installed several versions of Linux (sequentially, not concurrently) after Windows was installed and runningh and only had a problem once.  That case was a known bug in the installer for that distro (might have been an early version of Fedora Core, I don't remember).  All of the distros, including Ubuntu, give you the option to put your boot manager on a floppy, at least if you use the expert installation option.  If you do that, then your primary OS (again, at least if it is Windows) will boot directly without even seeing that Ubuntu exists.  That would probably be the easiest option.

Anyway, after you create your Ubuntu boot floppy, you should be able to remove GRUB by simply rewriting the MBR (master boot record).  For Windows XP, use your installation disk, boot to the CD, choose repair, then indicate the drive letter for the windows installation when it asks.  When you get a C:> then use the command fixmbr.  That will rewrite the MBR and your PC will automatically boot to Windows XP.  As long as your BIOS checks the floppy before the hard drive in the boot sequence, you can still boot to Linux from the floppy (just DON'T lose it!).

None of this applies if you want to install multiple distros of Linux - I have no experience with that.

Good luck and enjoy Ubuntu.
Dan

---

