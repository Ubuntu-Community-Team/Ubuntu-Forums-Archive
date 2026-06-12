---
title: "boot ubuntu from livecd"
date: 2006-08-19
forum: Desktop Environments
---

### Post by leb3000 on 2006-08-19
Hi,

I have installed ubuntu on one of my hard disks. unfortuntatly the hard disk with the actua grub bootloader on it seems t have died...

How do i boot ubuntu on my hard disk using the live cd?

the grub entry for the hd ubuntu is

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda5 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386

I tried to use this information to boot it from the livecd using "advanced options" but i couldnt get it 2 work

any ideas?

thanks
boot

---

