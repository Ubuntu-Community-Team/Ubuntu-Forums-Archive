---
title: "boot Ubuntu using Windows boot-loader"
date: 2006-09-25
forum: Desktop Environments
---

### Post by cccc on 2006-09-25
hi

howto boot Ubuntu using Windows boot-loader ?

kind regards
cccc

---

### Post by orb9220 on 2006-09-25
Keep searching I think there is a thread here about that. Sorry I don't know it.

The reason you might not want that is everytime you have a kernel update it will install grub on your mbr anyway which will intervene before you get to the boot.ini for ubuntu or xp selection.

Is there a reason you don't want to boot xp from grub?

---

### Post by cccc on 2006-09-26
> **orb9220 said:**
> 
The reason you might not want that is everytime you have a kernel update it will install grub on your mbr anyway which will intervene before you get to the boot.ini for ubuntu or xp selection.


are you 100 % sure ?


the reason is, I have the following OS installed:

mickysoft windows
ubuntu
debian
freeBSD

and I'll have MBR untouched and boot all systems using Windows Boot-Loader.

---

### Post by orb9220 on 2006-09-26
Well when I installed ubuntu after xp it wrote a grub-loader automatically which saw xp and included it. This was automatic for the desktop CD and my understanding is if you want to install mbr to other hd or not write to mbr then you have to use the alternate install CD.

---

### Post by lha on 2006-09-28
> **orb9220 said:**
> The reason you might not want that is everytime you have a kernel update it will install grub on your mbr anyway which will intervene before you get to the boot.ini for ubuntu or xp selection.

This is not true. Grub will not overwrite MBR every time you upgrade your kernel.

cccc:

Get the alternative install cd and install Grub into a primary partition during Ubuntu install. (So you already have Ubuntu. Well, just install a Grub for Ubuntu or use Debian's boot loader.) Then get [BootPart]("http://www.winimage.com/bootpart.htm") and add Ubuntu into Windows' boot loader.

---

### Post by orb9220 on 2006-09-28
Sorry didn't catch it due to lack of sleep. It updates the menu.lst not the grub-loader.

---

### Post by steve196 on 2006-09-29
1.) You need to use lilo, not grub. For some reason i found grub cannot be started with ntloader.
2.) The way to do this is: install lilo on your linux partition, copy the first 512 bytes of the linux partition into a file on the windows partition (" dd if=/dev/(where linux is) of=(mountpoint of win partition)/(filename) bs=512 count=1 ") and add the line (filename)="linux" to boot.ini . The lilo and the dd have to be redone everytime the kernel changes.

---

### Post by cccc on 2006-09-29
> **steve196 said:**
> 1.) You need to use lilo, not grub. For some reason i found grub cannot be started with ntloader.


that's not true ! 

ntloader starts grub without any problems:

[http://hacks.oreilly.com/pub/h/2337](http://hacks.oreilly.com/pub/h/2337)

or using bootpart:

[http://www.winimage.com/bootpart.htm](http://www.winimage.com/bootpart.htm)

---

### Post by Ravse on 2006-09-29
> **steve196 said:**
> 1.) You need to use lilo, not grub. For some reason i found grub cannot be started with ntloader.
2.) The way to do this is: install lilo on your linux partition, copy the first 512 bytes of the linux partition into a file on the windows partition (" dd if=/dev/(where linux is) of=(mountpoint of win partition)/(filename) bs=512 count=1 ") and add the line (filename)="linux" to boot.ini . The lilo and the dd have to be redone everytime the kernel changes.

I did the same a few years back to get NTLoader to boot Linux. Works just fine, it's just annoying to update. However, with the current NTFS write support it should be alot easier. As long as you don't chance the size of the file (which you won't, it's always 512 bytes), you'd be able to mount the NTFS partition and do the dd directly (as you already mention) without currupting the filesystem.

Today I use GRUB and don't bother with NTLoader at all. You just have to be careful you don't wipe the partition with the /boot/grub files. Otherwise you will render your system unable to boot, and you need to fix it using some kind of live cd.

---

### Post by lha on 2006-09-29
Grub is much better for use with ntloader than lilo. Lilo stores its configuration on the boot sector. So whenever you get a new kernel or want to change lilo's settings, you have to use dd to add new lilo to ntloader, just like Ravse was forced to do. Grub, on the other hand, stores settings in a file on a partition making it unnecessary to dd boot sector each time a new kernel is installed.

---

