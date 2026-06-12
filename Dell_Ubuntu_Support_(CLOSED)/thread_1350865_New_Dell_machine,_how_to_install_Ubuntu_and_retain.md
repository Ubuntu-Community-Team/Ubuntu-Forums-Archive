---
title: "New Dell machine, how to install Ubuntu and retain Dell System Restore functionality?"
date: 2009-12-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DodgeV83 on 2009-12-09
I messed this up on my last machine and would like get it right :)

I would like to install Ubuntu and still have the ability to go back to the original Dell image (bloatware and all).  Is this possible?

In my experience, installing Ubuntu on the machine (even with Wubi) will result in Grub removing all references to the Dell System Restore partition.  Once this is done, there is no way to run Dell Restore from that partition.

My thoughts:

[LIST]
[*]I can use "dd" to clone the drive to an .img on a backup USB hard drive, but this would also copy all empty space, resulting in a 320GB file :(

[*]If I boot with the Dell Restore CD, it will install the OS bare, without bloatware included.
[/LIST]
Is there a way to clone the whole disk (not just specific partitions), without including empty space?  Is there an easier way to retain the ability to restory from the partition?

---

### Post by gbrainin on 2009-12-09
Why not just install Ubuntu using manual partitioning, and just don't use/overwrite the restore partition?

---

### Post by DodgeV83 on 2009-12-09
> **gbrainin said:**
> Why not just install Ubuntu using manual partitioning, and just don't use/overwrite the restore partition?

Even if I keep the partition there, installing GRUB removes the option to start the recovery process from the partition.

---

### Post by br0nx finest on 2009-12-10
> **DodgeV83 said:**
> Even if I keep the partition there, installing GRUB removes the option to start the recovery process from the partition.
I was wondering this myself.
 
IMHO, it would be best to just forget about the Bloatware. I mean do you really need it? What will you be counting on, a free trial to some BS internet provider?

---

### Post by Ottis on 2009-12-10
Long time reader, first time poster.....

The Dell DSRcan be booted to even after the option is no longer displayed. A friend of mine updated her Win XP laptop to Vista, didn't like it and then found that the System restore option was gone. I found this;
[http://www.goodells.net/dellrestore/fixes.htm](http://www.goodells.net/dellrestore/fixes.htm)
and used it to restore the laptop to the original XP confiuration. 
It's an MS-DOS bootable disk to "make" the system boot to the restore partition, I don't know how this would work with Grub installed, I'm still kinda' new to Linux, but if you tinker with Dell PCs you might want to check it out.

Ottis.

---

### Post by efflandt on 2009-12-12
If you did not want to tamper with your hard drive at all, you could always run Linux from USB.

My Dell several year old 1.6 GHz dual-core Dell laptop from work already had 4 partitions, sda1 is something Dell, sda2 is XP Pro, sda3 (sda5) is a Dell media player that can play media from it without running Windows (not sure if that would work if I moved it on the drive) and sda4 is a Dell partition.

So I used a bootable USB stick with live/install Ubuntu iso the first time I traveled with Linux.   And since then shrunk the vfat partition of a WD Passport portable USB drive with gparted, which now has swap and a regular install of 64-bit Ubuntu 9.10.  Dell computers often need Broadcom wireless driver, but I should probably just disable that, because a Linksys WUSB54GSC is stronger, and that or Verizon USB mobile broadband work without any special modules/drivers.  The bootable WD Passport works as well with my personal Toshiba laptop, or or older Athlon64 desktop.

---

### Post by gbrainin on 2009-12-12
> **DodgeV83 said:**
> Even if I keep the partition there, installing GRUB removes the option to start the recovery process from the partition.

I think that if you enter the manual boot selection menu (F12 during the BIOS screen), that the recovery partition is one of the options.  Since this option comes before the bootloader is loaded, changing the bootloader to GRUB shouldn't affect it.

I could be misremembering.  I think it's the recovery on the BIOS list and the hardware test on the GRUB list, but I could have that backwards.

---

### Post by chenxiaolong on 2009-12-12
Dell posted an article on their website showing you how to make a recovery disk: [http://en.community.dell.com/wikis/linux/building-base-ubuntu-factory-iso.aspx](http://en.community.dell.com/wikis/linux/building-base-ubuntu-factory-iso.aspx) (for Linux, obviously)

---

