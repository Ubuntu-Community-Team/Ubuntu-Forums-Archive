---
title: "grub problem"
date: 2008-12-03
forum: General Help
---

### Post by suhaib1thariq on 2008-12-03
i had just installed intrepid .....while i installed it the grub looks like
		Ubuntu 8.10, kernel 2.6.27-7-generic
		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
		Ubuntu 8.10, memtest86+



after i updated all updates in update manager 
it looks like

Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+




it is booting       in both versions of kernel
whats this how can i solve it?

---

### Post by dudumomo on 2008-12-03
Hello
It's normal.
You have updated your kernel, hence you have an other line to boot on the new kernel.
You should now boot on the latest kernel, the 2.6.27-9

You can modify the grub file to delete the lines of the 2.6.27-7's kernel

Is it clear ?

---

### Post by gTinker on 2008-12-03
[QUOTE=suhaib1thariq]
it is booting       in both versions of kernel
whats this how can i solve it?[/QUOTE]

It's capable of booting either kernel, old or new, depending on which one you choose.

It is usually recommended to keep the old kernel for a few days in order to make sure the new kernel works acceptably with your system, then you may choose to delete those old kernel choices from the GRUB menu.lst.

---

### Post by anaconda on 2008-12-03
you can delete those extra entries from /boot/grub/menu.lst -file, or you can open synaptic and remove the old unneeded kernel from there. Grub entries will be removed once synaptic removes the kernel..

---

### Post by JohnFH on 2008-12-03
> **suhaib1thariq said:**
> 
Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+

it is booting       in both versions of kernel
whats this how can i solve it?

It's not booting both versions at once, but as already pointed out, it's capable of booting either.  Which line is highlighted in the menu?  That's the kernel that will get booted (sounds vicious!).

To remove the old one, use Synaptic to search for 'linux-image-2' and remove the old one.  Synaptic should update the grub menu for you I think.

---

### Post by JohnFH on 2008-12-03
> **anaconda said:**
> you can delete those extra entries from /boot/grub/menu.lst -file, or you can open synaptic and remove the old unneeded kernel from there. Grub entries will be removed once synaptic removes the kernel..

ahhhh pthpthpthpthpth!  I can't type as fast as you ....

---

