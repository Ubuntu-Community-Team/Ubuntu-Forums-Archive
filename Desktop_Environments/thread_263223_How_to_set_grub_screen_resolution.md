---
title: "How to set grub screen resolution"
date: 2006-09-22
forum: Desktop Environments
---

### Post by rempel on 2006-09-22
Hey all. I have a Thinkpad R40 with Ubuntu 6.06 installed, and everything is pretty creamy. With this distro I have finally been able to switch from Windows.

Just one minor issue right now: how do I make the grub screen and the boot process use my full 1400*1050 resolution? I was able to do this during the install but since then it uses 800*600 stretched out.

I did some research and based on that added "vga=834" to /boot/grub/menu.lst but this produced no change.

Any advice?

---

### Post by Anduu on 2006-09-22
Well I don't believe that is a valid resolution...

See here for the list of resolutions/codes;
[http://www.ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution](http://www.ubuntuforums.org/showthread.php?t=258484&highlight=grub+resolution)

---

### Post by rempel on 2006-09-25
1400x1050 is indeed a valid resolution. It's called SXGA+, see [http://en.wikipedia.org/wiki/SXGA%2B](http://en.wikipedia.org/wiki/SXGA%2B)

I forget where I found it, but this worked, in /boot/grub/menu.lst I added the bolded part:

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash **vga=0x342**
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

Now the boot screen, once I pass the grub menu, correctly uses 1400x1050 resolution of my Thinkpad R40's lovely UXGA screen

---

