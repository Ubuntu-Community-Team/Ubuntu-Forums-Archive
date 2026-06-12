---
title: "Startup video display problem"
date: 2007-03-18
forum: Desktop Environments
---

### Post by beckejc on 2007-03-18
I have a startup problem.  

The startup screen displaying all of the drivers being loaded and the ubuntu logo on a black background is all screwed up on my machine.

The logo and text are very small an on the lower right hand of the screen.  The menu.lst looks like:

title		Ubuntu, kernel 2.6.17-11-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-386 root=UUID=ea317c32-0050-47cd-8b52-6917491e0230 ro splash vga=794
initrd		/boot/initrd.img-2.6.17-11-386
savedefault
boot

I added the vga=794 based on somebodies suggestion on the forums.  Any other value I chose ends up with half the logo on the right side of the screen and half on the left.

I have a GEFORCE4 MX 4000 card and have a Gateway EV700 monitor.

---

### Post by beckejc on 2007-04-08
Thanks guys.  Really helped.:confused:

---

### Post by jakev383 on 2007-04-08
Try vga=791
I have a laptop that needed that one.

---

