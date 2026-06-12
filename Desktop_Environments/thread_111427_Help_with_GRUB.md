---
title: "Help with GRUB"
date: 2006-01-02
forum: Desktop Environments
---

### Post by Snurf on 2006-01-02
I have Windows XP on my computer. I installed Ubuntu to my external hard drive and during installation I chose to install the GRUB thing on my main hard drive. Ubuntu had problems when booting and i dont know why so i uninstalled Ubuntu, now, when i start my computer grub says Error 21 or 22. I dont want grub there.... I want my computer to start up in Windows XP.

---

### Post by zambizzi on 2006-01-02
Since you removed the /boot partition where the grub config file resided (grub.conf) - Grub is still there but cannot find a file to read to boot *anything* in your system.

You need to scrub Grub from your master boot record.  The easiest way to do this is to use a Win98 boot disk (you should have one of these laying around if you don't already).  Boot up and then type "fdisk /mbr" - your MBR will be cleared and Windows should boot up fine after that as if nothing ever happened.

If you don't have a Win98 boot disk go to bootdisk.com and make one.

---

### Post by Snurf on 2006-01-02
On bootdisk.com, there are many things to download. You say I need a win98 boot disk even though i have windows xp? 

There are all these Win98 boot discs, which one?:

Windows 95 Original | Mirror1 | 2 | 3
Windows 95 Version B | Mirror1 | 2 | 3
Windows 98 OEM | Mirror1 | 2 | 3
Windows 98 Custom, No Ramdrive | Mirror1 | 2 | 3
Windows 98 SE OEM | Mirror1 | 2 | 3
Windows 98 SE Custom, No Ramdrive | Mirror1 | 2 | 3

---

### Post by mazelado on 2006-01-02
There is a Microsoft KnowledgeBase article for LILO, but it should also work for GRUB:

[http://support.microsoft.com/kb/315224/en-us](http://support.microsoft.com/kb/315224/en-us)

---

### Post by zambizzi on 2006-01-02
[QUOTE=Snurf]On bootdisk.com, there are many things to download. You say I need a win98 boot disk even though i have windows xp? 

There are all these Win98 boot discs, which one?:

Windows 95 Original | Mirror1 | 2 | 3
Windows 95 Version B | Mirror1 | 2 | 3
Windows 98 OEM | Mirror1 | 2 | 3
Windows 98 Custom, No Ramdrive | Mirror1 | 2 | 3
Windows 98 SE OEM | Mirror1 | 2 | 3
Windows 98 SE Custom, No Ramdrive | Mirror1 | 2 | 3[/QUOTE]

Yes, a Win98 boot disk...doesn't matter if you have 2000, XP, etc....this is the easiest method of clearing the mbr.

Get the 5th one down on the list, "Windows 98 SE OEM" - pop in a floppy, and run the install to build the boot disk (in Windows.)

---

### Post by cotcot on 2006-01-02
I suppose you have the installation CD of your XP. 

Boot from your XP CD (check BIOS if this does not work). During the boot you get the questions if it is a new installation or a repair. Enter R of repair.From the repair console you have to type fixmbr to have the original XP loader again.

Please be not demotivated with your Grub experience. There is a way to install Ubuntu without touching the MBR on the hard disk.
During the installation of Ubuntu at the point of the Grub installation the installer asks you where to put Grub. Put a formatted floppy in your floppy drive and fill in 'fd0'. Grub will place the loader on the floppy and will leave your MBR as it was. When you reboot with the floppy inserted you will get the Grub menu. After reboot Ubuntu installs a number of packages to finalise the installation. During the installation the partition with Ubuntu is set active (this is done by default by the Ubuntu installer). You have to make the XP partition active again (for instance with fdisk). If you boot without the floppy you will get your XP as before. 
If you do not have a floppy drive it should work with a USB-stick too (check the BIOS if it recognises the stick). Then you will have to send the Grub loader to something like 'sda0' instead of 'fd0". 
Starting from CD is somewhat more complicated.

Hoping this will help you or give you some inspiration.
Succes !

---

### Post by Snurf on 2006-01-02
How do i get in MSDOS mode to type fdisk /mbr?

---

### Post by zambizzi on 2006-01-02
[QUOTE=Snurf]How do i get in MSDOS mode to type fdisk /mbr?[/QUOTE]

Did you use your XP disk or a bootdisk?  If you used a bootdisk you'd *be* in DOS mode if you had set your BIOS to boot from your floppy drive first.

---

