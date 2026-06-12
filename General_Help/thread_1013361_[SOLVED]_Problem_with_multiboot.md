---
title: "[SOLVED] Problem with multiboot"
date: 2008-12-16
forum: General Help
---

### Post by randiroo76073 on 2008-12-16
I seemed to have incured a problem in 8.10 that I didn't run into in 8..04. I just installed Ultimate 8.10 on my sda5(root) & sda6(home). Like usual I installed grub to sda5(hd0,4) and modified my menu.lst to chainload+1. When I try to boot into it I get: "Error 12: Invalid device requested". Here's pertinent part of menu.lst

title		Intrepid++ 8.10, kernel 2.6.27-10-generic (sda1+2,r-sda1)
uuid		a44ae6eb-555b-4642-9b3f-d2423471bf70
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=a44ae6eb-555b-4642-9b3f-d2423471bf70 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Recovery mode)
uuid		a44ae6eb-555b-4642-9b3f-d2423471bf70
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=a44ae6eb-555b-4642-9b3f-d2423471bf70 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Memtest86+
uuid		a44ae6eb-555b-4642-9b3f-d2423471bf70
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		The Rest:
root

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda11.
title		Intrepid 9 dev,(sda11-11+12,r-sda11) 
root		(hd0,10)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=5fb4bbb0-146f-4c0b-bac7-bd4db50450d6 ro splash vga=791 
initrd		/boot/initrd.img-2.6.27-10-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
title		Ultimate,(sda5+6,r-sda5) 
root		(hd0,4)
#kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=514c12b5-fa63-4233-8f4d-2419eacca1a2 ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-10-generic
savedefault
makeactive
chainloader     +1

I've checked that UUID's match, that said boot files are present, tho commented out, per usual practice, can anyone tell me what's wrong ???

---

### Post by caljohnsmith on 2008-12-16
The reason you get that Grub error 12 is because Grub can't set a logical partition "active", i.e. can't set the boot flag on a logical partition. How about trying instead:
```
title Ultimate,(sda5+6,r-sda5)
root (hd0,4)
savedefault
chainloader +1
```
Let me know if that does the trick.

---

### Post by randiroo76073 on 2008-12-16
Thanks for reply caljohnsmith, will try as soon as my download's done :)

It worked on reboot, thanks for help & I'll try to remember that next time :D

---

