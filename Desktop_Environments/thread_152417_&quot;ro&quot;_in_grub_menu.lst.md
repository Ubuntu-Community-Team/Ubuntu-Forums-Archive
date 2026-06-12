---
title: "&quot;ro&quot; in grub menu.lst?"
date: 2006-03-29
forum: Desktop Environments
---

### Post by maxwellcom on 2006-03-29
hi there,

with each new kernel update, i find myself revisiting grub's menu.lst file to edit the grub boot menu.  in the following menu configuration:

title		Linux
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda3 ro vga=0x317
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

what does "ro" stand for?  i don't recall seeing it before (but could be easily mistaken), and don't know exactly what it does.

thanks!

---

### Post by ispmarin on 2006-03-29
It stands for read only. It is default to kernel boot line in grub.

---

### Post by dcstar on 2006-03-30
[QUOTE=maxwellcom]hi there,

with each new kernel update, i find myself revisiting grub's menu.lst file to edit the grub boot menu.  in the following menu configuration:

title		Linux
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-**386** root=/dev/sda3 ro vga=0x317
.......
[/QUOTE]
BTW, have a read of this:

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

