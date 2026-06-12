---
title: "Qs in Ubuntu"
date: 2006-01-12
forum: Desktop Environments
---

### Post by wolverine88 on 2006-01-12
just installed ubuntu first time. It looks good.

1. the boot menu is kind of odd, I have to press Esc to get to the menu. Which file should I change to allow grub to display automatically?

2. How to set vesa mode to get higher resolution in console mode?

3. The ubuntu set my X server to 1152x864. Which command should I use to change the X config? I tried X86setup and no luck.

Thanks.

---

### Post by MartinG on 2006-01-12
[QUOTE=wolverine88]just installed ubuntu first time. It looks good.

1. the boot menu is kind of odd, I have to press Esc to get to the menu. Which file should I change to allow grub to display automatically?[/QUOTE]/boot/grub/menu.lst

Comment out (add # before) the line hiddenmenu

---

### Post by inigmatus on 2006-01-12
What happens when hiddenmenu is enabled? I'm at work and can't see right now.

---

### Post by hashimoto on 2006-01-12
[QUOTE=wolverine88]3. The ubuntu set my X server to 1152x864. Which command should I use to change the X config? I tried X86setup and no luck.

Thanks.[/QUOTE]
To reconfigure X-server run:
sudo dpkg-reconfigure xserver-xorg

---

### Post by MartinG on 2006-01-12
[QUOTE=inigmatus]What happens when hiddenmenu is enabled? I'm at work and can't see right now.[/QUOTE]You get the behaviour wolverine88 describes, where on bootup you don't see the grub menu, instead you are told to hit ESC if you want a menu.

---

### Post by tmahmood on 2006-01-12
when hiddenmenu is enabled GRUB shows a blank screen which hides the boot menu before booting into the default OS.

i thought hiddenmenu is disabled by default in ubuntu. at least mine was. I hate that too

---

### Post by kaamos on 2006-01-12
[QUOTE=wolverine88]
2. How to set vesa mode to get higher resolution in console mode?
[/QUOTE]

```
gedit /boot/grub/menu.lst
```
And add vga=**XXX** to the kernel you are using. For example 1024x768 is vga=791.

---

### Post by wolverine88 on 2006-01-12
Thanks all of you for the quick reply. Plan to switch from suse to ubuntu.

---

