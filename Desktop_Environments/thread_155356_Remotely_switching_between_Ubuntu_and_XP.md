---
title: "Remotely switching between Ubuntu and XP"
date: 2006-04-04
forum: Desktop Environments
---

### Post by DjKritical on 2006-04-04
Hi :) 

I use my computer remotely from work using VNC

I don't know much about GRUB... is there a way to alter GRUB from XP?

I've had a look at the file /boot/grub/menu.lst is this the file to change the default bootable os?

:-k 

Any help = Greatly appriciated!

:mrgreen:

---

### Post by Lux Perpetua on 2006-04-04
There is probably a line in your menu.lst that says "default 0" or something like that. That identifies which OS is the "default" when grub runs. Changing the 0 to another number changes which OS is the default (chang it to the number of the OS's entry in the grub menu, counting from 0). Is that what you're asking? 

I don't know anything about VNC, but I don't know if that's relevant to your question.

---

### Post by DjKritical on 2006-04-04
You've answered half my question..

VNC allows me to access my Desktop over an internet connection which I do all day at work...

Here's what I can do so far...

- Computer boots into Ubuntu by default

1.  Log into Ubuntu from Work

2.  Alter the /boot/grub/menu.list file to boot XP

3.  Restart Ubuntu

- Computer boots into XP by default

4.  Log into my XP

**5.  Alter the /boot/grub/menu.lst to boot Ubuntu**

6.  Restart XP

- Computer boots into Ubuntu by default

----------------------

Number 5 is the only thing I'm unsure of now?

:-k

---

### Post by Ian Maxwell on 2006-04-05
I don't know about editing the Grub config file from Windows--I'm told it has ext2 support, but I've never checked myself. However, another possible (though ugly and hackish) solution would be to create an image of the Windows MBR, and an image of the Grub MBR. Then you could get to Windows by overwriting the MBR and rebooting, and back to Linux by overwriting it again and rebooting again.

---

### Post by DjKritical on 2006-04-05
Now that's thinking outside the box :mrgreen: 

I have no idea how to do that though...

---

### Post by Sendervictorius on 2006-04-05
Just to push the envelope: you could run your PC as a virtual machine (using such as VMWare), and have both XP and linux running at the same time!

Then you could switch between ubuntu and XP instantly whenever you wanted. To allow it to happen, you would have to set up networking so that one operating system became a network gateway for the other. Not sure how you would manage with VNC - I suspect you could connect to either one of two ports of your gateway machine, then tunnel one port to your other virtual machine. Or do it with router/firewall settings. The mind boggles! :)

---

### Post by mozetti on 2006-04-05
[QUOTE=Ian Maxwell]I don't know about editing the Grub config file from Windows--I'm told it has ext2 support, but I've never checked myself.[/QUOTE]

There's a driver/dll package you can install in XP that enables ext2 support. I've installed it and used it a few days - now I can access my root & home partitions in WindowsXP. Since ext3 is just ext2 with journaling support, the ext2 driver works on ext3 partitions, but you don't get the journaling.

---

### Post by DjKritical on 2006-04-07
VMWare & Qemu are viable options however the reason I want to dual boot is because I use windows mainly for gaming... I've tried Cedega however it runs too slow for my liking..

The Ext2 drivers for windows are read only so I would be able to view the grub config file.. which wouldn't be of much use =(

Cheers tho...

I'm still trying to figure out a way to do this however...

If grub were installed on a Fat32 partition that would work.. I don't know much about grub tho.. 

:-k

---

### Post by Sendervictorius on 2006-04-08
If your windows boots onto a fat partition, it may be easier to boot directly into the windows bootloader, and choose which OS to boot by editing C:\boot.ini - rather than using grub. That way you can edit boot.ini from linux to change to windows, and edit from windows to reboot to linux. Of course it won't work if windows is on ntfs, unless you make-do with the unstable updatable linux ntfs drivers.

---

### Post by DjKritical on 2006-04-10
I installed windows on a Fat partition, excellent idea!

So I would have to remove grub, boot from the windows partition, and point the boot ini towards the linux partition?

---

### Post by Sendervictorius on 2006-04-11
No, you don't need to get rid of grub. You put an entry in boot.ini that points to your linux partition, and grub. Then you change your MBR record to point to your windows partition. You need to run a utility called bootpart in windows that creates a link file that points to your linux partition. A lot of this assumes you have windows installed on your first disk partition. I hope this applies to you.

This link: [http://home.ubalt.edu/abento/linux/redhat-install/dualbootNT.html](http://home.ubalt.edu/abento/linux/redhat-install/dualbootNT.html) describes how to set up dual boot using windows. You should then be able to boot to grub, select windows boot, get the bootloader menu, and choose linux, then start grub again, then... ;) 

Then once that is working, you then overwrite the master boot record (MBR). I can't remember how I last did that - it was some time ago.   A quick google turned up this:

The simplest way to repair or re-create MBR is to run Microsoft's standard utility called FDISK with a parameter /MBR, like
	A:\> FDISK.EXE  /MBR

Which I think assumes that you have a boot floppy that boots to DOS. You can download a DOS disk image from the internet. google to find.


I think you should keep grub so you can interrupt the boot process if need be, change run levels, change grub boot options, boot failsafe, etc. Just keep the automatic timeout setting low, and set the default OS in grub

Let me know how it goes.

---

