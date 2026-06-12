---
title: "Style Grub Boot Menu"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by FLCLFan on 2007-09-09
Hello, 

I want to "style" my Grub boot menu. 
What I want to do is make the categories (Windows OS, Linux OS, etc) different from the OS choice. Is it possible to make the categories non-selectable? And/or is it possible to somehow bold or change the colour of the categories text?

What I have is this(in /boot/grub/menu.lst):
```

title		****Windows OS****:
root		

title		Windows Vista x64
root		(hd2,0)
makeactive	
chainloader	+1

title		Windows XP x64
root		(hd1,0)	
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)	
chainloader	+1

title		****Linux OS****:
root		

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=72e2e0ac-b108-44f4-b1af-09227341fded ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		****Linux Backup OS (For recovery)****:
root		

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=72e2e0ac-b108-44f4-b1af-09227341fded ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=72e2e0ac-b108-44f4-b1af-09227341fded ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=72e2e0ac-b108-44f4-b1af-09227341fded ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

Thank you for whoever can answer this!

---

### Post by FLCLFan on 2007-09-09
12hr mark and no one knows if this can be done?

---

