---
title: "Problem with tty1- tty6"
date: 2009-02-14
forum: General Help
---

### Post by helbent forleder on 2009-02-14
Hi.:):)
I am using the netbook remix on an Asus eee 1000H. I have a strange problem that I've just recently noticed.
When I open a virtual terminal all that I see is a flashing cursor. I can type commands and they work, but I can't see what I am doing on the screen. :(
If I boot in recovery mode and I run repair on the X server, I can use the terminal normally (I can see everything) for that session only. The next reboot it's back to typing blind.
Any ideas how I should go about finding the problem and fixing it?
Here's the relevant part of my /boot/grub/menu.lst
```
title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=419385a0-4b2e-43b6-807f-d2f3b785e872 ro quiet splash vga=771
initrd		/boot/initrd.img-2.6.24-21-eeepc
initrd		/boot/initrd.img-2.6.24-21-eeepc
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-21-eeepc (recovery mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.24-21-eeepc root=UUID=419385a0-4b2e-43b6-807f-d2f3b785e872 ro single
initrd		/boot/initrd.img-2.6.24-21-eeepc

title		Ubuntu 8.04.1, memtest86+
root		(hd0,3)
kernel		/boot/memtest86+.bin
quiet
```
Any ideas would be appreciated!:guitar:

---

### Post by dcstar on 2009-02-14
> **helbent forleder said:**
> Hi.:):)
I am using the netbook remix on an Asus eee 1000H. I have a strange problem that I've just recently noticed.
When I open a virtual terminal all that I see is a flashing cursor. I can type commands and they work, but I can't see what I am doing on the screen. :(
If I boot in recovery mode and I run repair on the X server, I can use the terminal normally (I can see everything) for that session only. The next reboot it's back to typing blind.
Any ideas how I should go about finding the problem and fixing it?
Here's the relevant part of my /boot/grub/menu.lst

Any ideas would be appreciated!:guitar:

Try removing or changing the "vga=xxx" option.

PS Please don't "quote" code, use the Code function.

---

### Post by helbent forleder on 2009-02-14
Thanks for your help.
The resolution of this screen is strange - 1024x600. I haven't managed to find the appropriate vga code for it.
Any ideas about where, I can find it?
:)

---

### Post by helbent forleder on 2009-02-14
Thanks DCStar... you got me on the right track. I found this: 
[http://forums.msiwind.net/default-msiwind/1024x600-vga-code-for-menu-lst-t4219.html](http://forums.msiwind.net/default-msiwind/1024x600-vga-code-for-menu-lst-t4219.html)
and set the changed the vga mode to "vga=normal". Everything is fine again! :)

---

### Post by macabro22 on 2009-07-22
> **helbent forleder said:**
> Thanks DCStar... you got me on the right track. I found this: 
[http://forums.msiwind.net/default-msiwind/1024x600-vga-code-for-menu-lst-t4219.html](http://forums.msiwind.net/default-msiwind/1024x600-vga-code-for-menu-lst-t4219.html)
and set the changed the vga mode to "vga=normal". Everything is fine again! :)

Thanks! That does work. Maybe we should open a bug against UNR so this becomes default?

---

