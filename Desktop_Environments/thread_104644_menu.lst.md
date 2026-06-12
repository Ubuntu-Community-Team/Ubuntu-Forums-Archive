---
title: "menu.lst"
date: 2005-12-16
forum: Desktop Environments
---

### Post by slrafal on 2005-12-16
Could someone shed some light on my menu.lst file:

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/memtest86+.bin  
boot

Why do I have so many kernel listings? Do I need all of these in this document?

---

### Post by earobinson on 2005-12-16
It is listing all the kernbels you have installed, best way if you dont want so many is to uninstall the kernls you dont use, using synaptic

---

### Post by harisund on 2005-12-16
I think I got all those kernel listings after doing an apt-get dist-upgrade. 

You can ignore them, yes.

---

### Post by Redindian on 2005-12-16
Delete the old kernel i.e. the following 12 lines from your menu.lst

title Ubuntu, kernel 2.6.12-9-386
root (hd0,1)
kernel /vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd /initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root (hd0,1)
kernel /vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd /initrd.img-2.6.12-9-386
boot

---

### Post by earobinson on 2005-12-16
Look at my first post thats all you have to do.

---

### Post by Sutekh on 2005-12-16
Removing the lines from the menu.lst will not remove the kernels, only the option to boot to them

If you want the old (2.6.12-9-386) ones gone (and free up some space), go to Synaptic and look for or search for linux-image-2.6.9-12-386 and remove it.

---

