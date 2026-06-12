---
title: "Latest 8.10 Kernel Update was not added to menu.lst"
date: 2009-06-03
forum: General Help
---

### Post by beastrace91 on 2009-06-03
I recently run the automatic updater on my G1Sn to upgrade my kernel to the latest 2.6.27-14-generic, and I see the correct files for the kernel in my /boot directory. How ever it was not added automatically to my menu.lst - is it safe to copy over the entry for the 2.6.27-11-generic kernel and simply change the number or is there more to it than that?

~Jeff

---

### Post by Shazaam on 2009-06-03
If done correctly it is safe to edit menu.lst to reflect the new kernel. Like this...
Old-
```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
initrd
```
New-
```
title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro quiet splash vga=773 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		7f2d5801-46dd-4a87-a30a-c7a55afb67ab
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=7f2d5801-46dd-4a87-a30a-c7a55afb67ab ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

```
Make sure you use your uuid's not mine. :)

---

### Post by lisati on 2009-06-03
Running the following at the command line should also work:
```
sudo update-grub
```

---

