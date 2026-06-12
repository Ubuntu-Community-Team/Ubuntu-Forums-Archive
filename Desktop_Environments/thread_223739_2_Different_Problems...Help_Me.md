---
title: "2 Different Problems...Help Me"
date: 2006-07-26
forum: Desktop Environments
---

### Post by rosingjh on 2006-07-26
Hi I have two problems I am trying to solve on ubuntu.  First, I run a machine with both windows and linux on it.  I am wondering if I can change the operating system chooser at the begining of boot to default as windows or eliminate the timed countdown.  I have not made the switch completely to linux and therefore use windows more making it a hassle when my computer automatically boots into ubuntu.  Next, I downloaded the binary of Songbird from songbirdnest.com.  For some reason it worked but I dont think I installed it right.  There is no support I can find to install such an application (It does not show up on any add/remove program manager).  Finally, just a side note, I was expecting ubuntu 6.06 to have the "spedial effects" when switching screens.  I saw a movie with cube like characterisitcs when switching work places and was wondering if that is included in this release.  Thanks

---

### Post by aysiu on 2006-07-26
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by cucisan on 2006-07-26
open your /boot/grub/menu.lst and see at which position your Windows-entry is

my grub conf looks like this:
> 
default         0
timeout         10

title           Ubuntu, kernel 2.6.15-26-k7
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/sda2 ro quiet splash noapic nolapic acpi=off
initrd          /boot/initrd.img-2.6.15-26-k7
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-k7 root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.15-26-k7
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

title           Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1



which would make "Ubuntu, kernel 2.6.15-26-k7" 0, "Ubuntu, kernel 2.6.15-26-k7 (recovery mode)" 1 and so on..
in my case i would set the line
> default 0
to
> default 4

or just use the command

> sudo grub-set-default 4

for these "effects" you need to install XGL+compiz, of which howtos can be found in these forums.. but first you have to get your 3d acceleration to work (XGL is known to work well with ATI/Nvidia/Intel based cards)

---

