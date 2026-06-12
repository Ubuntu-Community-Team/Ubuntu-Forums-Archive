---
title: "Busybox... No one elses solutions work"
date: 2009-01-21
forum: General Help
---

### Post by Recognition101 on 2009-01-21
So, Like others, I tried to install Ubuntu with WUBI on an NTFS harddrive running Vista and ended up with the BusyBox prompt.

I'm an experienced Linux user, and I don't post much here because I can normally solve my own problems using other threads.

Here's what I've tried so far:
[LIST=1]
[*]Adding these boot parameters. I Added them after the end of this boot line (scroll right to see):
```
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=syncio **[I ADDED THINGS HERE]**
```
[LIST]
[*]pci=nomsi
[*]all_generic_ide
[*]irqpoll
[*]floppy=off
[/LIST]
[COLOR="White"].[/COLOR]
[COLOR="White"].[/COLOR]
[*]Removing all external USB drives
[COLOR="White"].[/COLOR]
[*]Typing exit, waiting 10 minutes, typing exit again
[COLOR="White"].[/COLOR]
[*]chkdsk and clean restarts
[COLOR="White"].[/COLOR]
[*]Setting BIOS option to RAID (it was already set like that because I do in fact have a RAID5 of 4 Seagate 250GB Drives)
[/LIST]

When I make it boot up without the quiet parameter, it screams about IO errors, it claims it's requesting some very high number on disk but the disk doesn't go that high, so it fails. It says that same two line error over and over again, possibly with different numbers.

I tried the Live CD and that boots into ubuntu just fine.

Thanks so much for reading!

---

### Post by Feivel on 2009-01-21
> **Recognition101 said:**
> So, Like others, I tried to install Ubuntu with WUBI on an NTFS harddrive running Vista and ended up with the BusyBox prompt.

I'm an experienced Linux user, and I don't post much here because I can normally solve my own problems using other threads.

Here's what I've tried so far:
[LIST=1]
[*]Adding these boot parameters. I Added them after the end of this boot line (scroll right to see):
```
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/installation.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_US.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --   ROOTFLAGS=syncio **[I ADDED THINGS HERE]**
```
[LIST]
[*]pci=nomsi
[*]all_generic_ide
[*]irqpoll
[*]floppy=off
[/LIST]
[COLOR="White"].[/COLOR]
[COLOR="White"].[/COLOR]
[*]Removing all external USB drives
[COLOR="White"].[/COLOR]
[*]Typing exit, waiting 10 minutes, typing exit again
[COLOR="White"].[/COLOR]
[*]chkdsk and clean restarts
[COLOR="White"].[/COLOR]
[*]Setting BIOS option to RAID (it was already set like that because I do in fact have a RAID5 of 4 Seagate 250GB Drives)
[/LIST]

When I make it boot up without the quiet parameter, it screams about IO errors, it claims it's requesting some very high number on disk but the disk doesn't go that high, so it fails. It says that same two line error over and over again, possibly with different numbers.

I tried the Live CD and that boots into ubuntu just fine.

Thanks so much for reading!
When are you getting the busybox prompt? Is it during the first boot after you run Wubi? Linux isn't installed until your first reboot so changing any parameters before that risks either an aborted or screwed up install.

---

### Post by Recognition101 on 2009-01-22
Oh no, I didn't change any parameters before it failed.

I installed ubuntu 8.10 with WUBI, then cleanly restarted the computer. I then selected ubuntu from the windows boot loader, and the Ubuntu logo with the bar showed up (the bar bouncing back and forth, not the loading style one), and then I was given the BusyBox prompt before it could turn into the loading bar.

I uninstalled Ubuntu in add/remove programs and reinstalled it with WUBI after I did the chkdisk, thinking it was a bad install, but it still failed. It was at that point I started messing with boot parameters through GRUB (hitting escape, then e, etc).

---

### Post by Yashiro on 2009-01-22
> ## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=560420320420180F loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=560420320420180F loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-23-generic

title		Ubuntu 8.04.1, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1

Is what my old grub menu.lst looked like when I used to use wubi.
Your kernel line seems insanely bloated and plain wrong. Perhaps the install has failed and left you with some interim .lst? Not sure. Perhaps it's due to the raid.

---

### Post by Recognition101 on 2009-01-22
I agree, Yashiro.

I've seen other .lst files and they all look like yours, not mine. For instance, I'm pretty sure the UUID is something that's absolutely necessary and unique to each harddrive.

I'd try yours, but I think I need my own UUID.
Another weird thing is that the folder:

C:\ubuntu\install\boot\grub

Is completely empty. I've tried copying .lst files into that directory, but it doesn't seem to work. I'd agree with the corrupt install thing, but it consistently installs in a corrupt fashion, because, like I mentioned, it breaks in the same fashion after multiple installs.

EDIT: By the way, I know the iso isn't corrupt since the iso (in CD form) can boot into a perfectly usable Live CD that works on the machine in question. I just don't want to partition because I've had bad experience with Vista thinking grub is a harddrive corruption and "fixing" it, leaving the machine unable to boot either OS.

---

### Post by Yashiro on 2009-01-22
> RAID5 of 4 Seagate 250GB Drives
Is probably the issue.

---

