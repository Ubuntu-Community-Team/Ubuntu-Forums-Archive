---
title: "Can I make the startup text when I boot look all sexy? (framebuffers?)"
date: 2005-04-26
forum: Desktop Environments
---

### Post by simianMiscreant on 2005-04-26
When I had Gentoo, my friend helped me set the framebuffer when my system booted up so that the letters looked the proper size...or whatever. I have a 1920x1200 widescreen, so it'd be cool if I could get my bootup text looking all nice and small. I think he built support for something into the kernel, and then told Grub to do something...I forget. Sorry I'm such a n00b, but if anyone has any idea what I'm talking about, I'd really like some help  :wink: . Thanks in advance!

---

### Post by charlesb on 2005-04-26
You can set the vga option in the arguments of the kernel, in /boot/grub/menu.lst. I don't know for your resolution, for a 1280x1204 I set vga=0x31a

Cheers

---

### Post by simianMiscreant on 2005-04-26
anyone know what that vga option would be? i searched google...

---

### Post by dude2425 on 2005-04-26
What would one set for 1600x1200?
I tryed 79[6-9], which in theory should allow me to use 1600x1200, but it just doesn't work, it asks me to scan or something.

---

### Post by svyatogor on 2005-04-26
[QUOTE=simianMiscreant]anyone know what that vga option would be? i searched google...[/QUOTE]

Have a look here:

[http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=10)

---

### Post by simianMiscreant on 2005-04-26
ok so I found the VESA code I want to use: 0x31F

but where do i put it? and furthermore, how do I build kernel support for vesa?

---

### Post by charlesb on 2005-04-27
[QUOTE=simianMiscreant]ok so I found the VESA code I want to use: 0x31F

but where do i put it? and furthermore, how do I build kernel support for vesa?[/QUOTE]There's no need to recompile your kernel!. In a terminal enter this :
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst
```
In the editor you find a part llike this:
```
title Ubuntu
    kernel (hd0,1)/boot/vmlinuz root=/dev/sda2
    initrd (hd0,1)/boot/initrd.img
```that you must edit so that it looks like this:
```
title Ubuntu
    kernel (hd0,1)/boot/vmlinuz root=/dev/sda2 [COLOR=Red]vga=0x31f[/COLOR]
    initrd (hd0,1)/boot/initrd.img
```Save file, and restart.
Cheers

---

### Post by tmowerman on 2005-04-27
I have an ati card and can get the full screen mode from a console with

```
sudo modprobe radeonfb
``` 

I was just wondering if this was equivalent, and if not if there are any benefits or disadvantages to either method

---

### Post by NTolerance on 2005-04-27
[QUOTE=charlesb]There's no need to recompile your kernel!. In a terminal enter this :
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst
```
In the editor you find a part llike this:
```
title Ubuntu
    kernel (hd0,1)/boot/vmlinuz root=/dev/sda2
    initrd (hd0,1)/boot/initrd.img
```that you must edit so that it looks like this:
```
title Ubuntu
    kernel (hd0,1)/boot/vmlinuz root=/dev/sda2 [COLOR=Red]vga=0x31f[/COLOR]
    initrd (hd0,1)/boot/initrd.img
```Save file, and restart.
Cheers[/QUOTE]

Works great, thanks.

---

### Post by tread on 2005-04-27
Can't you also set vga=ask, in which case you will be prompted at boot, and shown different resolution options?

I'm pretty sure that would work too.

---

