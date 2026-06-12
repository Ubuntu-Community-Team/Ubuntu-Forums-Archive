---
title: "vmlinuz.old and initrd.img.old"
date: 2005-05-13
forum: Desktop Environments
---

### Post by rusi_pathan on 2005-05-13
Originally I had the 386 kernel and then I installed 686. But then I removed linux-686 reverting back to the original 386 kernel. Now everything is as it were before but my [FONT=Courier New]vmlinuz[/FONT] and [FONT=Courier New]initrd.img[/FONT] are now [FONT=Courier New]vmlinuz.old[/FONT] and [FONT=Courier New]initrd.img.old[/FONT]

So can I remove .old from these files or can I delete them alltogether ?

Btw / looks like

[FONT=Courier New]bin
boot
cdrom
dev
etc
home
initrd
initrd.img.old
lib
lost+found
media
mnt
opt
proc
root
sbin
srv
sys
tmp
usr
var
vmlinuz.old[/FONT]

and my menu.lst has

[FONT=Courier New]title		Ubuntu, kernel 2.6.8.1-3-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.8.1-3-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.8.1-3-386
savedefault
boot

title		Memory test
root		(hd0,0)
kernel		/boot/memtest86+.bin[/FONT]

---

