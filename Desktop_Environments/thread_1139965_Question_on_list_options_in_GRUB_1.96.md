---
title: "Question on list options in GRUB 1.96"
date: 2009-04-27
forum: Desktop Environments
---

### Post by bcschmerker on 2009-04-27
I recently upgraded the Grand Unified Bootloader to v. 1.96 on my Everex; Startup Manager only works with 0.92, a setback but one that can be worked around.  The AutoMagic list of /boot/grub/menu.lst is similar to the following:
```

title		Chainload into GRUB 2
root		(hd0,0)
kernel		/boot/grub/core.img
savedefault

title		Debian GNU/Linux, kernel 2.6.24-23-rt
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=* ro 
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault

title		Debian GNU/Linux, kernel 2.6.24-23-rt (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-rt root=UUID=* ro single
initrd		/boot/initrd.img-2.6.24-23-rt
savedefault

title		Debian GNU/Linux, kernel 2.6.24-23-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=* ro 
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault

title		Debian GNU/Linux, kernel 2.6.24-23-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=* ro single
initrd		/boot/initrd.img-2.6.24-23-generic
savedefault

title		Debian GNU/Linux, kernel memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

```What I'd like to do is show the Startup and Shutdown checklists below the "ubuntu" splash, and possibly another behavior option as well.  What options are available for this, and would they be placed after the "boot=UUID=*", as I believe the case to be??

---

