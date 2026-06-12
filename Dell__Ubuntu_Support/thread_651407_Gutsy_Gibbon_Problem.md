---
title: "Gutsy Gibbon Problem"
date: 2007-12-27
forum: Dell  Ubuntu Support
---

### Post by circuz_phreak on 2007-12-27
Dell Inspiron 1720
t7300, 2GHZ dual core/800MHZ FSB, 4mb cache
256MB Nvidia geForce 8600 GT
2GB Ram
250GB 5400rpm SATA HDD

   Previously had Fiesty Fawn running great after putting some time into it.  I thought I might try updating to Gutsy Gibbon and assumed everything would be fine since it was an upgrade.  The system is a dual boot with windows XP.
   On first reboot the system started up and all the changes made in Fiesty Fawn seemed to hold (fixing the wireless issue etc.).  The only problem is the upgrade changed my menu.lst file and gave me no entry point to windows.  That was the only file I changed and it restored my entry point into windows but gave me this problem when loading ubuntu.

First does a system scan, once finished it displays the following...    
```

check root = bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/644532b1-4720-45d2-8d$ does not exist.  Dropping to a shell!

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)_

```

My first thought was that when I changed the menu.lst file I gave it the wrong access point for the kernel?  I wanted to stay away from coding until I had a better idea of what was going on.  Any help would be appreciated.  Thanks!

---

### Post by natehall on 2007-12-28
This link is for other Dell models but it still might help. It shows known problems and workarounds for the upgrade to Gutsy.
[http://linux.dell.com/wiki/index.php/Ubuntu_7.10](http://linux.dell.com/wiki/index.php/Ubuntu_7.10)

---

### Post by johnw2007 on 2007-12-28
Did you by any chance use Pico to edit menu.lst? I notice that it has chopped off the UUID entry with a $, which Pico is liable to do with long lines if you are not careful.

It looks as though you have to edit menu.lst again to re-instate the entry.

This is the first entry in my menu.lst:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/vmlinuz-2.6.22-14-generic root=UUID=550cf0a2-e206-4888-a811-5e6f8168fbcd ro quiet splash resume=/dev/sda5
initrd		/initrd.img-2.6.22-14-generic
quiet

Note that from kernel to sda5 is all one line.

Basically, the entry root=UUID needs to be changed to point to your root partition. With luck you will be able to use the one from the second entry (recovery mode). If not, it can be replaced by root=/dev/your_root_partition. Which in my case would give:
kernel		/vmlinuz-2.6.22-14-generic root=/dev/sda6 ro quiet splash resume=/dev/sda5

Are you still able to start in recovery mode? If not I can recommend the System Rescue CD, which you can download from [www.sysresccd.org](www.sysresccd.org). Boot the CD then enter:
mkdir /mnt/mydir
mount /dev/your_boot_partition /mnt/mydir

You will then be able to edit /mnt/mydir/grub/menu.lst.

Hope this helps.

---

### Post by circuz_phreak on 2007-12-28
what command can I type in the ash terminal to find out which boot partition it is.  I can't remember which one it is.

---

### Post by johnw2007 on 2007-12-28
You can try fdisk.

If linux is on the first hard drive try fdisk /dev/sda or fdisk /dev/hda. For a second hard drive it would be fdisk /dev/sdb or fdisk /dev/hdb.

The p command will list all the partitions, though not the mount points, but you will see which ones are linux partitions.

In the pre-installed Dell scheme, the boot partition and the root partition are separate. If that is the case with you it is the boot partition you need to mount and the root partition you need to put into menu.lst.

---

### Post by circuz_phreak on 2007-12-29
no luck, typing help gives a set of available commands and fdisk isn't one of them. I'm limited because I am not actually inside linux at the moment.   I'm not sure which, if any of the commands listed can solve my problem.  I'm leaning towards just reformatting and doing a fresh install, which I don't want to do.  I know it's size, is it safe just to guess which one it is?
    I think im just going to download the live cd and maybe try installing overtop of it, or even just formatting the partition and starting from scratch.  It would be nice if  I could use the live cd to fix the problem.  Would I be able to mount the drive and edit the files myself while in the live environment?  I'll see what the deal is after downloading the iso.
    Out of curiosity though, where the root UUID is being chopped off by the $ sign, will it be identical to the backup file I made before changing it?  Otherwise I'm not sure what the ID is supposed to be.  Also, I figure I won't be able to edit the files because of permissions, what's a way to get around that inside the live cd environment?

---

### Post by johnw2007 on 2007-12-29
Fdisk does not appear in the help list. Have you actually tried using it as I suggested? Type fdisk and you should get the syntax prompts.

If you boot with the live/install CD/DVD and select Places - Computer you can see the partitions that are present. Navigate through them until you find the one with (boot/)grub/menu.lst. Ubuntu will mount the partitions as you look in them, probably as /media/disk-x, where x is 1, 2, 3 etc.

In a terminal type sudo su to get admin privelege then use gedit to edit the file.

---

