---
title: "[SOLVED] gparted doesn't recognize centos 5.2 file system"
date: 2008-12-20
forum: General Help
---

### Post by walter_j on 2008-12-20
I installed centos 5.2, but it didn't use my ubuntu boot loader. I want to add centos to the ubuntu boot loader and was going to mount the centos partition in order to determine settings needed for the bootloader. I used gparted to check the file system for centos but it doesn't recognize the file system. how can i mount the centos partition so that i can determine the grub boot loader settings? does ubuntu have the file system drivers for centos?


Walter

---

### Post by logos34 on 2008-12-20
does it show up in

sudo fdisk -l

?

Sometimes gparted doesn't see the partition for various reasons...You can try manually adding a centos boot entry to ubuntu grub like this (assuming for example that centos / is /dev/sda3):

gksudo gedit /boot/grub/menu.lst

add this to bottom:
> 
title Centos 5.2
configfile (hd0,2)/boot/grub/menu.lst

---

### Post by walter_j on 2008-12-20
This worked great. Thanks. I never seen this solution before. I guess it gets the bootloader to use the menu created by the distro. I could have used this for fedora 10 too, since it had exactly the same problem. Fedora had another problem and wouldn't boot so I gave up. Centos seems to be in a time warp... Makes you appreciate how much work ubuntu developers put into the distro.

---

### Post by logos34 on 2008-12-20
> **walter_j said:**
> This worked great. Thanks. I never seen this solution before. I guess it gets the bootloader to use the menu created by the distro. 

Yes, exactly.  It's just a grub command to look for and use the other OS's menu.  The nice thing about it vs. using the the exact vmlinuz and initrd lines is that you don't have to worry about editing it after CentOS kernel updates.  Nor do you need to have grub boot code installed to the other OS's / partition, as you do in 'chainloader' format.  You do have to go through two grub screens, though, but IMO it's no big deal (in fact you could hide the second one if it really bugged you)

good luck and enjoy

---

### Post by walter_j on 2008-12-20
-30 C with a breeze here today, so I have lots of time to muck about with my system. Maybe i'll try to get fedora working again...

---

