---
title: "Keyboard repetition"
date: 2006-08-17
forum: Desktop Environments
---

### Post by munku on 2006-08-17
Hello, I am brand new with Ubuntu. 

I just installed it, and I can't seem to use it. Everything is great until I hit the Login screen. As soon as that happens my keyboard starts to repeat keypresses (dozens and dozens), however
this does not happen when I am in console mode.

My machine is older and is a desktop.
AMD K6/2 500
190-something ram
15 gig drive.

---

### Post by murataht on 2006-08-17
if it is ok in console and act strange in GUI, i think it should be a X server configuration problem. maybe it can be fixed with some hack to the /etc/X11/xorg.conf file. just a suggestion. 

if it can't be fixed, try with another keyboard. maybe this is a simpler solution. 

good luck

Murat

---

### Post by munku on 2006-08-22
Actually I found a perminent solution people might be interested in. The keyboard is not faulty (brand-spanking new) but something to do with the clock. If you add clock=tsc into the boot procedures of grub, it will work fine.

---

