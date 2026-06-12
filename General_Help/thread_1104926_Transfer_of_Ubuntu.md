---
title: "Transfer of Ubuntu?"
date: 2009-03-24
forum: General Help
---

### Post by sv1cdn on 2009-03-24
Dear all.
I am running Ubuntu 8.10 with a Quad CPU and 3GB RAM plus 300GB hard disk. I want to change my CPU to more powerfull Quad and to 4GB RAM, also motherboard change.
So, if I simply move the hard disk from one pc to other with Ubuntu work?
What if I have an empty new hard disk of 500GB, how can I move the Ubuntu partitions to the new?
Thank you for the help!

---

### Post by Tony Flury on 2009-03-24
I can confirm that (unlike Windows that objects to H/W changes), you can take a HD with Ubuntu from one PC to another - and in general it should boot fine.

The only gotchas might be things like Graphics (best to go into recovery mode first and reset the X server), and maybe your networking might be a tad troublesome.

---

### Post by sv1cdn on 2009-03-24
Great, thanks!
Do you know anything about how to copy one partition to a bigger hard disk?

---

### Post by x33a on 2009-03-24
if you are running ubuntu 64 bit, then it should work. but, if you are using ubuntu 32 bit, then the added ram would not be detected, though i think there are some workarounds for that.

---

### Post by Nostalos on 2009-03-24
> **sv1cdn said:**
> Great, thanks!
Do you know anything about how to copy one partition to a bigger hard disk?

Might want to have a look at Clonezilla [http://www.clonezilla.org/](http://www.clonezilla.org/)

Never used it myself as its nothing you can't do with a Live CD and an external USB drive.   But hear its far easier to use ;)

---

### Post by sv1cdn on 2009-03-24
> **x33a said:**
> if you are running ubuntu 64 bit, then it should work. but, if you are using ubuntu 32 bit, then the added ram would not be detected, though i think there are some workarounds for that.

Thanks, I am running 32bit Ubuntu. When I upgraded my RAM from 2GB to 3GB it worked fine.

---

### Post by x33a on 2009-03-24
take a look here:

[http://ubuntuforums.org/showthread.php?t=1099633](http://ubuntuforums.org/showthread.php?t=1099633)

---

### Post by mikechant on 2009-03-24
> Thanks, I am running 32bit Ubuntu. When I upgraded my RAM from 2GB to 3GB it worked fine.

But going from 3Gb to 4Gb is not the same as going from 2gb to 3Gb.

Standard 32bit Ubuntu (or any standard 32 bit OS) will only see about 3-3.5Gb of 4Gb.

You then have a choice:
a) Waste some RAM
b) Reinstall with the 64Bit version and your memory addressing will be limited only by the amount of RAM you can physically install.
c) Use your current installation but switch the kernel to the 32-bit server kernel. This uses a feature called PAE (see wikipedia article for details) to support up to 64Gb total memory but only 4Gb max per application.

---

### Post by seydou on 2009-03-24
> **sv1cdn said:**
> Great, thanks!
Do you know anything about how to copy one partition to a bigger hard disk?

With linux this should not be a big problem. I would recommend following:

- attach your new hdd to the pc and boot from live cd
- partition your new hdd (I use fdisk), make active and format the partition (fdisk and makefs.ext3 could do the job, consider also labeling the partions for better management)
- mount the partition you want to copy, and the newly formated one
- copy the data
   example: cp -av /mnt/olddisk/* /mnt/newdisk/

Once you have done that, edit etc/fstab on the newdisk mount, so it would reflect the new partition on boot - here comes to handly labeling. See documentation of fstab, if unsure what to do. You can also edit boot/grub/menu.1st file at this point or do it later.

Now you can reboot, and test boot new hdd. If you use grub to load the system, it makes it easy. Switch to grup prompt (pressing "c" on menu), and issue the commands, for example, asuming that old drive is still first to boot, and new is second (note that grub numbering starts from 0, that's why we use 1 in this case):
   root (hd1,0)
   kernel /vmlinuz ro root=/dev/sdb1
   initrd /initrd.img
   boot
You can use tab in CLI to complete the path and filenames. If everything is correct, you should boot without problems. If it works, reboot again and re-install the grub on new disk. Make sure that you copy the grub images from /usr/lib/grub/... directory to /boot/grub/, provided they are not already there.

On boot, switch to grub CLI again, and issue following:
   root (hd1,0)
   find /boot/grub/stage1
   setup (hd1)
This installs the bootloader to master boot record of the new hdd.

Now you can either remove the old drive or change the boot order in bios, and if you did not forgot to make your new partition active, you should boot the old system from shiny new hdd.

---

