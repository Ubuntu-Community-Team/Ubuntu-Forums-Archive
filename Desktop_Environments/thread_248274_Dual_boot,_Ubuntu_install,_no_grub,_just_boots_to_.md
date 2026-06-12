---
title: "Dual boot, Ubuntu install, no grub, just boots to windows"
date: 2006-08-31
forum: Desktop Environments
---

### Post by mrbaz on 2006-08-31
I have two drives.  I have one IDE HDD that I just use to throw data on it.

I have a 250G SATA drive that has Windows XP on it.  I gparted the drive to give me a swap partition and a 38G ext3 partition.

I installed ubuntu (using the video safe mode).  The LiveCD boots up and I run the install.  It does all of the normal things I've always done before.  I then restart the computer after the install prompts me to.  It reboots and goes right into windows.  I don't even get a Grub menu.  :confused:

---

### Post by fritz_monroe on 2006-08-31
Here's a link to an article on the GNU page about [Installing GRUB]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall").  

I don't really know how XP does it's boot routine, but it may be trying to recover from a "corrupt" MBR.

---

### Post by mrbaz on 2006-08-31
> **fritz_monroe said:**
> Here's a link to an article on the GNU page about [Installing GRUB]("http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html#Installing-GRUB-using-grub_002dinstall").  

I don't really know how XP does it's boot routine, but it may be trying to recover from a "corrupt" MBR.


Should I manually install grub to the partition that has XP on it, or to the partition in which Ubuntu is to be installed?

edit: It's showing the IDE drive as hd0 and the SATA drive as HD1.  Would this have anything to do with it?

---

### Post by mrbaz on 2006-09-01
OK, well I got grub installed, but I'm still having a problem with it not booting.  I edited the menu.list under /boot/grub so that the Ubuntu partition is HD1,2, but I still get errors out the wazoo.

Maybe I should just redo everything from scratch.

---

### Post by fbwr75215 on 2006-09-01
I had this problem the first time I installed Ubuntu also.  My setup is nearly the same as yours.  I read somewhere that Ubuntu will install the bootloader on the IDE drive and not the SATA drive by default.  What I did was unplug the IDE drive and installed normally.  Then tested to ensure I can boot into Windows and Ubuntu.  I then just reconnected the IDE drive and it works great.  Hope this helps.

---

