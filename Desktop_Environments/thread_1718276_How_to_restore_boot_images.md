---
title: "How to restore boot images?"
date: 2011-03-31
forum: Desktop Environments
---

### Post by MasthaX on 2011-03-31
Greetings users,

I am a fairly experienced ubuntu/linux user. But i can't seem to fix my current system, and i really dont want to reinstall as of all custom software i use.

My main goal was resizing my / paritition with gparted. THe tutorial said to remove the boot partition (200 MB EXT4) and remove the SWAP, and then resize the partition. THis all worked out well. After  booting a live CD i reinstalled grub. Try to boot and it drops me to the grub shell.

I tried several things, like reinstalling grub. But this is not the problem. The problem is my /boot only contains a grub directory. No bootimages or configfiles whatsover.

Is there a way to restore these like redownloading an image or putting in a apt-get command to download a new config?

Help is much appreciated :)

---

### Post by MasthaX on 2011-03-31
p.s.

In grub my filesystem is reachable.

I wanted to try this (or similair syntax) but i have no kernel or kernel files :(.

grub>root (hd0,1)
grub>kernel /boot/vmlinuz<put kernel here, i have no kernel :( >
grub> initrd /vmlinuz....
grub>boot

---

### Post by Krytarik on 2011-03-31
I suggest this:
- chroot into your install 
- reinstall the "linux-image-VERSION-generic" packages associated to your currently installed kernels
- reinstall the package "memtest86+"
- update-initramfs
- update-grub
- exit chroot

1.) chroot into your install:

- boot into a LiveCD
- establish an internet connection

Concluding from your previous post, I will use "sda1" for your install partition, but you may re-check it with:
```
sudo fdisk -l
```(lower case L)
```
sudo mount /dev/sda1 /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```2.) reinstall the "linux-image-VERSION-generic" packages associated to your currently installed kernels:

- find out what packages you need to reinstall:
```
dpkg -l |grep linux-image-2.6
```- install those:
```
apt-get install --reinstall linux-image-VERSION-generic
```3.) reinstall the package "memtest86+":
```
apt-get install --reinstall memtest86+
```4.) update-initramfs:
```
update-initramfs -k LATEST_KERNEL_VERSION -c
```5.) update-grub:
```
update-grub
```6.) exit chroot:
```
exit
``````
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
```I hope it works! Good luck!

---

### Post by MasthaX on 2011-03-31
Thank you very much, i will try to do this in a VM first. I will post results.

I haven't seen any problem like mine on this forum so this will be a great addition to the userbase if everything works out fine.

---

### Post by Krytarik on 2011-03-31
> **MasthaX said:**
> 
I haven't seen any problem like mine on this forum so this will be a great addition to the userbase if everything works out fine.
Yeah, I indeed also haven't seen so far in these forums (or anywhere else), that someone accidentially purged half of the boot partition/directory. ;-)

---

### Post by MasthaX on 2011-03-31
Yeah well, i did this on purpose, i didnt know the bootimages were in /boot. So i simply thought to reinstall grub and go.

---

### Post by MasthaX on 2011-03-31
First of all, thank you very much Krytarik, i got it fixed, everything works as it should. thanks to the steps you told me above.

It didnt go all that smooth at first. Got some errors while trying to install the kernels. the "update-initramfs -k LATEST_KERNEL_VERSION -c" command didnt go all that smoothly it gave allot of errors, but as i watched the code execute i saw that the kernel installing ran basically the same process. So that didnt't bother me. After i reconfigured grub i rebooted, still prompted to grub shell, after repeating the same process i thought of reinstall grub, the [ubuntu way]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"). After this i ran an update (update-grub) rebooted, and everything works well now.

So if someone should encounter these problems please first of all remove everything out of your /boot for a clean install;

1. Install the kernel images (using the commands of krytarik
2. Install grub,
3. reconfigure grub (not sure, but may be optional).
4. reboot.

---

### Post by Krytarik on 2011-03-31
But you did replace "LATEST_KERNEL_VERSION" with the actual latest version number of the installed kernels, right?
However, I just yet noticed that I overlooked the "generic" appendix, I should have paid more attention to it, sorry.

So, for me, the command would actually be like this:
```
update-initramfs -k 2.6.32-30-generic -c
```Also, what do you actually mean by "reinstalling grub, the ubuntu way"?
Do you mean the installation of the grub boot loader into the MBR?

And if you really removed the entire "/boot/grub" directory, the reconfiguration of the package "grub-pc" was indeed necessary to recreate it and its content, of course you need also to run "update-grub" after that.

---

