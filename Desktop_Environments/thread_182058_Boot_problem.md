---
title: "Boot problem"
date: 2006-05-25
forum: Desktop Environments
---

### Post by bmujeeb on 2006-05-25
I have installed Kubuntu 5.10 on my hd0 (first boot drive) next to windows xp. I already have suse 10 on my hd1 and GRUB boot loader is installed. 

while installing Kubuntu i couldnt replace grub and neither i can install LILO on my MBR at hd0.

Now I can boot kubuntu with my suse boot disk but i tried to edit already installed Grub (menu.lst) but Kubuntu doesnt boot.

I have installed kubuntu on /dev/hda4 and swap partition is before that
i have used the following command in GRUB

title kubuntu, kernel 2.6.12-9-386 
    root (hd0,3)
    kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda4 ro quiet splash
    initrd /boot/initrd.img-2.6.12-9-386

please help me out...

---

### Post by Sef on 2006-05-25
Check out [Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub").

---

