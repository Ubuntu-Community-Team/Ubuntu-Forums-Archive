---
title: "Why not WinXP AFTER Ubuntu?"
date: 2008-12-04
forum: General Help
---

### Post by melancholy00 on 2008-12-04
HI

Is there anyway I could install Windows XP AFTER having installed Ubuntu?
I would like it can be possible, because I will need re-install Mathematica and I dont know anybody that have this software for Linux...

I already know that Windows likes to be the only OS installed, but I need more convincent reasons (I mean, a better explanation about it).

Thanks!

---

### Post by kebes on 2008-12-04
> **melancholy00 said:**
> HI

Is there anyway I could install Windows XP AFTER having installed Ubuntu?

I already know that Windows likes to be the only OS installed, but I need more convincent reasons (I mean, a better explanation about it).

The reason it's usually recommended to install Windows first (and Linux afterwards) is that Windows will wipe the master boot record (MBR) and put in a "boot only Windows" MBR. This means that you will then only be able to boot Windows (even though Linux is still installed). By installing Linux second, you have the option to replace the Windows MBR with a MBR that enables dual-booting. Ubuntu uses the "grub" boot-loader to do this.


So it is easiest to install Windows first and Linux second, since Linux will put in a "proper" MBR (one that allows dual-booting).


However, you can install Windows second if you want. It will erase the Linx boot-loader (grub). But then you can manually re-install grub as the boot-loader, and manually add Windows and Linux as boot entries, and then you'll again be able to dual-boot into either Linux or Windows.


To learn how to do this, search the web and these forums for "manual install grub" or "re-install grub" or "restore grub" or "configure grub boot loader" and phrases like that.

This community document explains how to do it:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Here are some other links that seem to describe how to do it:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)
[http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

---

### Post by ToFue on 2008-12-04
do a forum search for "dual boot"

however if you're installing to a separate disk for xp, then unplug the linux drive/disk and install xp normally. After that, plug the linux disk back in and upon reboot, set the bios to boot from the linux drive (you'll have to identify which one is which on your specific machine).

You'll then have to add a <GRUB?> entry that identifies the windows boot image, and makes it an option to choose that install by editing the bootloader's .conf file manually.

again, there are plenty of posts that'll walk you through it.. just do a forum search for "dual boot walkthrough" or something.. 

this is a fly-by reply, but hope this helps! :)

---

### Post by binbash on 2008-12-04
you can but you have to re-install grub after windows

---

### Post by sedawk on 2008-12-04
I think it is possible, but you have to take special care:

* Create a FAT32/NTFS partition with Ubuntu before running the installation
  (does WXP installer complain about preconfigured disks?)
  and activate that partition 
* Make a backup of the bootblock (first 512 bytes on the HDD) with Ubuntu.
* Have a LiveCD ready because you have to reinstall the grub bootblock
  later on.
* Add a new entry to grub's menu.lst to boot WXP.


Have you checked if Mathematica runs in Wine? Check the
Application Database at [www.winehq.com](www.winehq.com).
I love Wine. I use a different WINEPREFIX for every new application,
so removing an app simply means to remove the "WINEPREFIX" directory.
Say goodbye to cleanup problems people have with a real WXP.

Or use a free virtualization product (VMWare server, VirtualBox)
to run a virtual Windows and Mathematica inside. Works if
Mathematica doesn't need DirectX.

---

### Post by Phases on 2008-12-04
Well, I'm sure you can dual boot still it just might be tricky, require help of others besides me but....


... Have you considered Wine or Virtualizing XP? 

That's what I do, virtualize it with VirtualBox for my few XP needs I still have. 

But, no accelerated graphics so like... games and stuff like that it's not good for.

Wine would be okay for accelerated graphics, but it works with some stuff, not with others as I understand it.

Edit: wow I was severely ninja'd... That's what happens I get sidetracked while typing post..

---

