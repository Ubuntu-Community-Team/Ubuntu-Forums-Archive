---
title: "Kernel compilation"
date: 2005-12-22
forum: General Help
---

### Post by freakanth on 2005-12-22
initrd image is not being created when i compile a new kernel. How do i create it? And how do i get the mkinitrd command? I use Ubuntu 5.10.

---

### Post by Susana on 2005-12-22
sudo mkinitrd -o /boot/initrd.img-`uname -r` `uname -r`

then you edit your menu.lst and add your new initrd

---

