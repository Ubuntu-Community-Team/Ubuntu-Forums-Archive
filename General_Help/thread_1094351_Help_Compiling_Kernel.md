---
title: "Help Compiling Kernel"
date: 2009-03-12
forum: General Help
---

### Post by t4ggs on 2009-03-12
Hi, I installed DreamLinux (if you wonder why just see the link below) [http://ubuntuforums.org/showthread.php?t=1087641]("http://ubuntuforums.org/showthread.php?t=1087641")

So back to what I was saying, I installed DL 3.5 and wanted to upgrade the kernel to 2.6.28.7 so I followed the instructions here:
[http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html]("http://www.cyberciti.biz/tips/compiling-linux-kernel-26.html")
It's my first time compiling the kernel.

I did everything till step #6, I couldn't create the initrd file, don't know why.

Anyway I tried booting but I get error 15: file not found

Here is my grub.lst

```
# created by menulst_create.rb
#
default  0
timeout  5
gfxmenu (hd0,5)/boot/grub/message.dream
#
title  Dreamlinux (sda6, mbr)
root  (hd0,5)
kernel  /boot/vmlinuz-2.6.28.5-1-i686-dream root=/dev/sda6 vga=791 splash=silent,fadein,theme=default console=tty1 ro quiet resume=/dev/sda7
initrd  /boot/initrd.img-2.6.28.5-1-i686-dream

#MY KERNEL
title           MYKERNEL, kernel 2.6.28.7 Default
root            (hd0,5)
kernel          /boot/vmlinuz root=/dev/sda6 ro
initrd          /boot/initrd.img-2.6.28.7
savedefault
boot

title  Dreamlinux (sda6, mbr) (recovery mode)
root  (hd0,5)
kernel  /boot/vmlinuz-2.6.28.5-1-i686-dream root=/dev/sda6 ro quiet single
initrd  /boot/initrd.img-2.6.28.5-1-i686-dream

title  Dreamlinux (sda6, mbr) (memtest)
root  (hd0,5)
kernel  /boot/memtest86+.bin
quiet

# This is a divider, added to separate the menu items below
title		Other operating systems:
root

title  Microsoft Windows Vista X64
root  (hd0,0)
makeactive
chainloader  +1
```

Thanks for your help.

---

### Post by zvacet on 2009-03-12
Maybe you want to try [this.]("http://www.ubuntugeek.com/automatically-compile-and-install-the-latest-kernel-using-kernelcheck-in-ubuntu.html")

---

