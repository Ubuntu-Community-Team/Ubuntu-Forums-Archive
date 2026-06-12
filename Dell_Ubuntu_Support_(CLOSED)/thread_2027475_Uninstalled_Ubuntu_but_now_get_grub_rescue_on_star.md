---
title: "Uninstalled Ubuntu but now get grub rescue on startup."
date: 2012-07-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by harryt98 on 2012-07-16
I had Ubuntu dual booted with Windows 7. I no longer needed Ubuntu on my laptop (as I was trying it and now have it on my desktop) so I decided to get rid of it. However when I now start my computer it goes straight to a screen saying:
error: no such partition.
grub rescue>
How can I fix this problem? Any help would be appreciated, thank-you. :D

---

### Post by Laiquendi on 2012-07-16
From Win7 repair disk (hope you have one) repair booting issue, it has to re-write the booting options.

---

### Post by oldfred on 2012-07-16
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by chinchillas on 2012-07-24
How do I do all this if I have a recovery CD but the computer with the problem is a netbook, thus no CD slot? 
I only have a mac available (snow leopard) with a cd slot; can I use this to make a usb bootable disk? If so, how? I've read 20 tutorials and have had zero help. I'm burning down.

---

### Post by oldfred on 2012-07-24
Always best to have a repairCD or USB for the current version of every operating system installed.

I used a Windows repairCD to make a Windows repair USB as I could not find a way to make the USB directly from Ubuntu. 
Do not know about a Mac and whether there is a way. Since you can install Windows in a Mac, I would think there may be a way.
[https://help.ubuntu.com/community/Installation/FromUSBStick/#From_Mac_OSX](https://help.ubuntu.com/community/Installation/FromUSBStick/#From_Mac_OSX)

If you know anyone with the same (32 or 64 bit) version of Windows:
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

If just booting Windows you can install a Windows work alike, for all the instructions on liveCD, just create a liveUSB.

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.


And this can be installed into an Ubuntu liveCD/USB or downloaded as a liveCD/USB, also will install a Windows work alike boot loader syslinux, if you want Windows to boot:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

