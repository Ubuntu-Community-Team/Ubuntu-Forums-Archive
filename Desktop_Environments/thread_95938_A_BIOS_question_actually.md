---
title: "A BIOS question actually"
date: 2005-11-27
forum: Desktop Environments
---

### Post by LadyLuck on 2005-11-27
Hi all. 
Just singed upp after installing Ubuntu 5.04 (from Linux Format 68) on an old DELL box and upgrading to 5.10 over the web. Prior to install I added a second hard drive as slave. Ubuntu saw it during install and I have the option (GRUB) to boot to Win on the slave drive. However it seems the BIOS does not recognice the second drive and    booting fails claiming the drive is non-existent.

So I guess this is really a question of getting some help with the BIOS. I need to look a the contents of the slave once before I reformat the thing. 
Thanks
LL

---

### Post by dcstar on 2005-11-27
[QUOTE=LadyLuck]Hi all. 
Just singed upp after installing Ubuntu 5.04 (from Linux Format 68) on an old DELL box and upgrading to 5.10 over the web. Prior to install I added a second hard drive as slave. Ubuntu saw it during install and I have the option (GRUB) to boot to Win on the slave drive. However it seems the BIOS does not recognice the second drive and    booting fails claiming the drive is non-existent.

So I guess this is really a question of getting some help with the BIOS. I need to look a the contents of the slave once before I reformat the thing. 
Thanks
LL[/QUOTE]
Go into your BIOS and make sure that the Drive is set to "Autodetect", and you should see both drives detected on the BIOS screen when you reboot your PC.

Is it on the same IDE channel as your Master drive?

---

### Post by LadyLuck on 2005-11-28
Thanks David, that worked well. The BIOS now correctly identifies both drives. I tried to boot to WIN on the slave but it failed so now I'm curious to know if I can mount the slave in Ubuntu and look at the directories and files on the slave before I wipe it clean.  And a pointer on how to eventually reformat the slave would be very much appreciated.

---

### Post by wrtrdood on 2005-11-28
You should be able to mount the drive easily under Ubuntu.  In fact, you may find that it's detected and mounted for you (under /media).  There's a number of ways to prep the drive for use in GNU/Linux.  Depending on the filesystem you want to use there's an mkfs variant to help you along.  I think I saw GUI utilities under both Gnome and KDE as well.  Look up the man pages on fdisk and mkfs and you should be good to go.

Windows must be the primary to boot.  You can probably just swap this to get it to boot up.  Just another option.

---

