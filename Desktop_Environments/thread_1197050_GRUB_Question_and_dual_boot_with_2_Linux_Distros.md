---
title: "GRUB Question and dual boot with 2 Linux Distros"
date: 2009-06-25
forum: Desktop Environments
---

### Post by The Bane on 2009-06-25
All, thanks in advance for any and all assistance...

I have two HDDs. A 320GB and a 30GB. I was using the smaller for backups and whatnot while running Ubuntu 8.10 on the larger. I decided to check out Ubuntu Server, as I was feeling more secure using Linux... :(

I put Server on the smaller HDD. When it was not what I was looking for, I put another distribution of Linux on it (PCLinuxOS 2009). This made a mess of my GRUB Loader, and even after re-installing Ubuntu 8.10 on the large HDD, I can not boot to it. I did boot to it once, but as soon as I restarted the system... nothing.

What I get after turning on the PC and selecting Ubuntu 8.10 as the boot OS:

----------------------------------------
root(hd1, 0)
Filesystem type is ext2fs, partition type 0x83

Error 15: File not found

Press any key to continue...
----------------------------------------

I looked at the GRUB Loader Config in the PCLinuxOS Administrator options and it looks fine (as far as I can tell), though it does show PCLinuxOS to be the "default" boot OS.

Anyone able to help me get back to true dual boot status?

Best,
The Bane

---

### Post by Locutus_of_Borg on 2009-06-25
insert livecd into optical drive
boot form said livecd
once booted, open a terminal
become root (sudo -i, sudo su, su, su -, sudo root, etc.)
mount your ubuntu installation's root directory at /mnt (if, for example, on your first hard drive, ubuntu was installed occupying the entire drive, the command 'mount /dev/sda1 /mnt' would mount your root directory at /mnt)
re-install grub on your MBR using the settings from the original ubuntu install with the following command:```
grub-install --no-floppy --root-directory=/dev/sda1 /dev/sda
```

if you had more than one partition on the 320gb drive, determine the partition that has /boot on it.

you can do this by first, from the livecd still, inside the root terminal, issuing the command 'fdisk -l' and looking at the 320gb drive section of the output, then mounting each partition and listing the contents until you find the correct one, e.g.```
mount /dev/sda1 /mnt/
ls /mnt/
umount /mnt/
```
when you find the one that has /boot in it, don't unmount it, then continue with the grub-install command


theres another way to do it, but as convoluted as what i just said sounds, the other way is more of a hassle in my opinion

---

### Post by Locutus_of_Borg on 2009-06-25
oh and after re-installing grub, make sure that in /mnt/boot/grub/menu.lst that your entry to boot ubuntu is pointing to the correct drive and partition 

(hd0,0) = /dev/sda1
(hd0,1) = /dev/sda2
(hd1,0) = /dev/sdb1
etc.

and that the kernel line's "root=" parameter is matching above...and of course that it specifies a kernel that does in fact exist

---

### Post by The Bane on 2009-06-26
> **Locutus_of_Borg said:**
> oh and after re-installing grub, make sure that in /mnt/boot/grub/menu.lst that your entry to boot ubuntu is pointing to the correct drive and partition 

(hd0,0) = /dev/sda1
(hd0,1) = /dev/sda2
(hd1,0) = /dev/sdb1
etc.

and that the kernel line's "root=" parameter is matching above...and of course that it specifies a kernel that does in fact exist

I think I grok the first part. Specially since it was installed on the entire drive so finding the boot point should be easy.

Not sure I get the last, quoted part. Will I have all those (hd#, #) entries. Guess I don't know what I am looking for here.

So, I will have 2 grub loaders now? Or will the command line listed get rid of the PCLinuxOS grub loader?

Thanks for the help thus far,

The Bane

---

### Post by Locutus_of_Borg on 2009-06-26
you will only have one boot loader, if you installed grub onto the second hard drives MBR, that will only get loaded if you either chose to boot form it in the BIOS, or boot to it from the grub version you will have just installed on your main drive's MBR

after mounting ubuntu to /mnt, look at the menu.lst for grub, it will be located at /mnt/boot/grub/menu.lst, assuming you are still on the livecd, and have your ubuntu installation mounted at /mnt and are already in  root terminal

```
gedit /mnt/boot/grub/menu.lst
```

since it is the first drive, you will need an entry like the following to boot ubuntu:
```
title Ubuntu Linux
root (hd0,0)
kernel /boot/$KERNEL root=/dev/sda1 ro quiet splash
initrd $INITRD
```

you will need to change $KERNEL and $INITRD to one of your installed kernels/initrd's ```
ls /mnt/boot
``` will list what is in /boot of ubuntu, one of these is your kernel, and one of them is your initrd 
the initrd will end in .img, the kernel should start with 'vmlinuz' just make sure both have the same version number for what you put into the menu.lst file

---

