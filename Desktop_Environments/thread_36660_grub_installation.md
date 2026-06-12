---
title: "grub installation"
date: 2005-05-24
forum: Desktop Environments
---

### Post by hoffman on 2005-05-24
i wish to make a dual boot machine ubuntu with windows xp. I understand that you have to install grub into mbr in order to make it work. Which is the right partition for me to installation or just in /dev/hda?

Noite: I did it b4 but i forgot 
Current setting fstab similar to like this:

proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hda1	/mnt/windows/c	ntfs	umask=0222	0	0
/dev/hda5	/mnt/windows/d	vfat	umask=000	0	0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by mtron on 2005-05-24
grub usually installs during install in the mbr of your hd and it auto - detects winxp OS'es on your computer, so no need to tweak grub prior to install

grub needs a file called /boot/grub/menu.lst (as i said it is usually generated automatically)

an entry to boot ubuntu would look like this:

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

an entry to boot Windows would in your case look like this:

title		Windows XP SP2 
root		(hd0,0)
savedefault
makeactive
chainloader	+1

your posted the content of your /etc/fstab file, which as no direct influence on grub. just one question about this : why don't you mount your winxp partition to /media/winxp 
and the other one to
/media/stuff or whatever

detailed information about auto -mounting partitions at boot up can be found [here](http://www.ubuntuguide.org/#windows)

---

### Post by hoffman on 2005-05-24
that's for my personal reference in terms of mounting. what i really want to know is that you have to install grub in your mbr for first ide hard disk /dev/hda or is going to be in something like this /dev/hda1, /dev/hda2? and why?

Note: not about installation about boot partition

---

