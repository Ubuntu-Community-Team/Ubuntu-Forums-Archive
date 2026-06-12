---
title: "Need help triple booting..."
date: 2005-12-31
forum: General Help
---

### Post by kudu on 2005-12-31
Here's the scoop:

I have two HDs. hda with Win XP on it, and hdb with Ubuntu on it. I want to install Gentoo on hdb alongside of Ubuntu.

I used the default partition scheme when I installed Ubuntu. I Created two new primary partitions to hold Gentoo, hdb3 for /boot and hdb4 for /root.

Here's my fdisk output showing my hdb setup:

The number of cylinders for this disk is set to 9726.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/hdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5713    45889641   83  Linux
/dev/hdb2            9539        9726     1510110    f  W95 Ext'd (LBA)
/dev/hdb3   *        5714        5778      522112+  83  Linux
/dev/hdb4            5779        9538    30202200   83  Linux
/dev/hdb5            9539        9726     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order

My question is how best to go about installing Gentoo and how do I setup grub? Also, how do I handle the swap partition ?

This is the complete Linux education, let me tell you! Gentoo is a bugger to install.

Thanks and...

HAPPY NEW YEAR TO ALL!!

---

### Post by Luke771 on 2005-12-31
C'mon, you dont need any help: A three-OS boot sounds like much, but you can actually do it: you have already configured a dual boot; now, one more OS, one more line in the boot loader, that's all.
I guess you can have one swap partition for both Linuxes, you won't be using them at the same time, after all, but it's only my newbie guess, you may want to double check on this one.
I've never done anything like that but I'm pretty sure that any boot loader can do the trick by simply addling a line for the new OS. Even the one that comes with Windows.
I mean, open your boot loader configuration file, look how it directs the boot sequence to the OS's; copy the line to Ubuntu and change it a little bit to make it point to Gentoo.
To get some help with the actual lines, just check out how the configuration a dual boot all-Linux system shoul look like, in some forum, linuxquestions.org has the answer, than simply "merge" the all-Linux and the Lin-Win configuration... it can't be too difficult.
It must work, the proof is that Grub makes Ubuntu multi boot with Windows, Recovery Mode and Memtest, that's already a 4-boot system (and some people have two separate Linux kernels, making it 6 possible boots on one machine)
So what's the problem? Just add a line for Gentoo and you're done.
You can install a copy of Grub on a floppy and configure it like your current boot loader, so you can boot from floppy if you mess up your boot loader.
Or, you can keep the boot loader as it is, try the new three-OS configuration on the floppy, and duplicate it on the hard disk when you are sure that it works... I don't think you really need to do this, but it feels good to have a backup anyway.

---

