---
title: "Windows with BSOD - now BSOD before grub loads."
date: 2009-04-04
forum: General Help
---

### Post by Nixie Pixel on 2009-04-04
Ok, so I was dual booting Vista 64 and Ubuntu Intrepid Ibex (on a second drive), with grub as the boot loader. I left Vista 64 on all night, and in the morning I come back to a BSOD (PFN_LIST_CORRUPT). Upon rebooting, prior to reaching the grub boot loader, I get a BSOD flash up and then immediate reboot. In other words, I can no longer boot into either O/S.

I am currently running off an Ubuntu Live CD, checking the memory with memtest+, but why would I be unable to get to grub before a BSOD happens?

---

### Post by Nixie Pixel on 2009-04-05
Can anyone tell me why the machine would suddenly decide to skip grub and go straight to Windows?

---

### Post by Peter09 on 2009-04-05
How did you install, was it WUBI?

---

### Post by Peter09 on 2009-04-05
The worst case scenario here is a Hard Disk Fault - can you see your Hard Drive from the LiveCD.

---

### Post by Yashiro on 2009-04-05
Windows CANNOT crash before grub has loaded if it's on the MBR.

You must have a wubi install or are using the Windows bootloader via some other means.

---

### Post by Nixie Pixel on 2009-04-05
I installed via the Live CD on my second hard drive, installed windows on my first hard drive, then ran grub setup to set up grub on the first HDD.

I have no idea how this happened either.  Maybe I messed up running grub?  Is there a command I can run to check if grub is on the correct HDD?

---

### Post by JAlexoid on 2009-04-05
I had a lot of instances when Windows would overwrite my MBR without notice, what I used to do, is run:
grub-install /dev/hda 
or
grub-install /dev/sda

---

### Post by Nixie Pixel on 2009-04-05
I can see the hard disk in fdisk just fine using the Live CD.  Running sudo grub-install /dev/sda returns:
Could not find device for /boot:  Not found or not a block device.

---

### Post by Peter09 on 2009-04-06
Try reinstalling the boot loader

[http://www.smokinglinux.com/tutorials/restore-grub-boot-loader-in-your-ubuntu-linux](http://www.smokinglinux.com/tutorials/restore-grub-boot-loader-in-your-ubuntu-linux)

---

