---
title: "Usplash problems"
date: 2005-10-14
forum: Desktop Environments
---

### Post by aleksabl on 2005-10-14
Hi,

My screen is blank during the boot process. This happend after installing usplash. Does anyone have a clue about what might be wrong?

---

### Post by SilentCacophony on 2005-10-15
One thing I can think of, is that if you set anything other than the default resolution in /boot/grub/menu.lst, using the *vga=xxx* option, it seems to just blank. That's what it did to me when I tried vga=794, anyway, which is what I use when doing the server install.

---

### Post by aleksabl on 2005-10-15
Thanks for trying to help, but as I use the default settings the problem is probably laying elsewhere...

---

### Post by manicka on 2005-10-15
This may help

[http://ubuntuforums.org/showthread.php?t=76309&highlight=usplash+slower](http://ubuntuforums.org/showthread.php?t=76309&highlight=usplash+slower)

---

### Post by aleksabl on 2005-10-15
I don't think that's the problem. I have a pretty fast laptop computer. The scree n doesn't jump back to text-mode - the screen is just blank until gdm kicks in.

---

### Post by gmc on 2005-10-16
[QUOTE=SilentCacophony]One thing I can think of, is that if you set anything other than the default resolution in /boot/grub/menu.lst, using the *vga=xxx* option, it seems to just blank. That's what it did to me when I tried vga=794, anyway, which is what I use when doing the server install.[/QUOTE]

Not to dispute this statement, but I found that if you use (in my case) vga=792 (1024x768x24), the splash screen wouldn't work, however by switching to vga=0x318 (1024x768x24) it would. A bit weird, but it is possible to use the vga= parameter with usplash. Try setting the hexidecimal value for the graphics mode you want, rather than the decimal value and see if that works.

G.

---

