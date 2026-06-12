---
title: "repair dual boot two separate drives linux/windows - GPT detected"
date: 2021-12-11
forum: Debian
---

### Post by antonio-ub21 on 2021-12-11
Hi, this is my first post in this forum. Although I have been using linux for a long time due I am by no means an advanced linux user. I have a dual boot machine with Windows (sda) and debian bullseye (sdb) in two separate drives. My BIOS boot is set into Legacy+UEFI but I have tried UEFI only option as well. I recently changed my linux OS to debian and the dual boot stopped working. I can run debian only.

I tried boot-repair in a Ubuntu live-usb but get the warning "GPT detected, create BIOS-Boot partition etc" so, before doing changes and then regret, I prefer to ask here in the first place. You can see the details in this pastebin created with boot-repair: 

[https://pastebin.ubuntu.com/p/gXhY6dYYvk/](https://pastebin.ubuntu.com/p/gXhY6dYYvk/)

Many thanks in advance

---

### Post by oldfred on 2021-12-11
Moved to Other OS since no Ubuntu.
You were in Chat sub-forum which is what it says Chat, not help.

Also had to edit link as it was not working. You had an extra /plain/ at end.

You have BIOS/MBR install of Windows and UEFI/gpt install of Debian.

Since newer UEFI system, better to backup & reinstall Windows in UEFI boot mode. Change from MBR to gpt will totally erase drive.
Microsoft has required vendors to install in UEFI boot mode since 2012. And some new systems are UEFI only.

You can use your Windows repair/recovery flash drive to restore a Windows boot loader in BIOS boot mode to sda. Boot-Repair when booted in BIOS mode, may offer to install a Windows type boot loader - syslinux, if you use Advanced mode.

You then can dual boot but only from UEFI boot menu. 
UEFI & BIOS are not compatible and once you start booting in one mode, you  cannot switch modes. Or grub can only boot other systems in same boot mode.

You also can convert Ubuntu to BIOS boot mode on gpt partitioned drive if you do add the 1 or 2MB unformatted partition with bios_grub flag. And then install the BIOS version of grub - grub-pc. Only use Advanced mode with Boot-Repair as you want Windows boot loader in MBR of Windows drive, if booting in BIOS mode.

---

### Post by antonio-ub21 on 2021-12-13
Many thanks oldfred for such a detailed answer. I'd like to avoid a reinstall since I can't boot into windows and have to back up my data. In any case I will do if that's the best alternative.

---

### Post by oldfred on 2021-12-13
Just do not use Boot-Repair's auto fix in BIOS mode. It will want to install grub2's BIOS version to MBR of all drives.
You want to keep a Windows BIOS boot loader in MBR of Windows drive.
Boot-Repair's advanced options give the choice of boot loader & drive. 

Since two drives you can dual boot with Windows in BIOS mode and Ubuntu in UEFI mode, but only from UEFI boot menu. UEFI & BIOS are not compatible, once you start to boot, you cannot change. Or grub can only boot other installs in same boot mode.

And Ubuntu normally wants to install grub to first drive. In UEFI mode it then wants an ESP - efi system partition on first drive. 
With multiple drives you typically have to manually partition to have ESP on Ubuntu drive & manually install grub to that drive after install.

Windows has fast start up which sets hibernation flag whether BIOS or UEFI. 
The Linux NTFS driver will not mount the NTFS partition (normally) to prevent damage to the hibernation & loss of data.
And Windows updates often turn that setting back on.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Even if you want to keep Windows in old BIOS mode, you should plan on eventually converting.
Manufacturers are now making systems that are UEFI only, so development of BIOS mode drivers will not be as active.

---

