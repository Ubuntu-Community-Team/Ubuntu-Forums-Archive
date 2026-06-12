---
title: "reverting back to a previous kernel?"
date: 2005-01-06
forum: Desktop Environments
---

### Post by tiiim on 2005-01-06
i installed a PPC kernel with sleep on it however this cause errors when i start so want to downgrade to one i have before.

I looked in /boot and found i have the previous img but the files the link files have .old. How do i use a previous kernel and set it up to work? im guessing i have to change links but how?

---

### Post by jbh on 2005-01-06
if you use GRUB (default boot loaded) it will prompt you which kernel you want to ldd, so loading an older kernel is no prob. It should be in there by default anyways /boot/grub/menu.lst .. all my old kernels are

or sudo apt-get remove (kernel name) then re-install the one that isn't h00ped

---

### Post by tiiim on 2005-01-06
[QUOTE=jbh]if you use GRUB (default boot loaded) it will prompt you which kernel you want to ldd, so loading an older kernel is no prob. It should be in there by default anyways /boot/grub/menu.lst .. all my old kernels are[/QUOTE]
 well i removed the kernel but the symbolic have not updated . i went to the yaboot.conf and put the old image at the top as a temp solution but how do i create the new sybmolic links?

---

### Post by tiiim on 2005-01-06
[QUOTE=tiiim]well i removed the kernel but the symbolic have not updated . i went to the yaboot.conf and put the old image at the top as a temp solution but how do i create the new sybmolic links?[/QUOTE]
 fixed the symbolic links by hand... nothing like finding out and doing it uself eh ;)

i used ln -s [kernel file] vmlinux

and same for the intrd files

and updated conf with the new boot config and did ybin and now system works fine booted both in Linux and old mode and works fine now. So im assuming when i update the kernel next time it will automatically update the links like it done for every other time :)

---

