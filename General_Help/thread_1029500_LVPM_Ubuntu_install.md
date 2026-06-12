---
title: "LVPM Ubuntu install"
date: 2009-01-03
forum: General Help
---

### Post by Polomint01 on 2009-01-03
Sorry, I posted this in the wrong section, should have posted it here

I have just transferred my Ubuntu 8.04 from wubi to a dedicated hard drive.

The transfer worked well, my new hdd is a 500gb internal hdd, I am using a hard drive usb docking station (i don't like opening the desktop until I have to).

So I booted up, and no sign of my new install, checked menu.lst and its there.

Selected it, and got error 23.

I have had a little look around on the forums, and it seems to be letting the pc know where the root is for the new install.

My problem is being that it is on a different hdd how do I let it know what the root is.

Please find below part of my menu.lst file.


title Ubuntu 8.04.1, kernel 2.6.24-19-generic
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=DA3C0DD43C0DAC97 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=DA3C0DD43C0DAC97 loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.24-19-generic

title Ubuntu 8.04.1, kernel 2.6.24-18-generic
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=DA3C0DD43C0DAC97 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04.1, kernel 2.6.24-18-generic (recovery mode)
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=DA3C0DD43C0DAC97 loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=DA3C0DD43C0DAC97 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, kernel 2.6.24-16-generic (recovery mode)
root (hd0,1)/ubuntu/disks
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=DA3C0DD43C0DAC97 loop=/ubuntu/disks/root.disk ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04.1, memtest86+
root (hd0,1)/ubuntu/disks
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title Windows NT/2000/XP (loader)
root (hd0,0)
savedefault
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
chainloader +1



title Ubuntu-on-/dev/sdd1
root (hdd,0)
configfile /boot/grub/menu.lst




title Ubuntu-on-/dev/sdd1
root (hdd,0)
configfile /boot/grub/menu.lst


You can see, the new install at the end, any help welcome.

I will, install this drive inside the case, but need to transfer files from xp onto first.

many thanks

Paul
Polomint01 is online now Report Post   	Edit/Delete Message

---

