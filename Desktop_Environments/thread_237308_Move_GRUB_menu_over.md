---
title: "Move GRUB menu over?"
date: 2006-08-15
forum: Desktop Environments
---

### Post by wilberfan on 2006-08-15
I've got a new LCD monitor, and the GRUB menu appears partially off the left side of the screen.

I've been doing some searching/reading in these forums and it seems that the resolution of the GRUB menu is fixed at 640x480 (or whatever).

The resolution doesn't bother me--it's not being able to read all the choices in the menu that's a little irritating.

Is there a way to just move it over to the right a bit?  :confused: 

(And I'm not asking about the Ubuntu splash; I've found the threads regarding the "vga=xxx" in the menu.list file.)

Thanks, 

Scott

---

### Post by wieman01 on 2006-08-16
You can adjust the alignment of your screen using the display's control functions (x-y axis, etc.). Have you tried that? It should stick.

---

### Post by wilberfan on 2006-08-16
> **wieman01 said:**
> You can adjust the alignment of your screen using the display's control functions (x-y axis, etc.). Have you tried that? It should stick.

Well, more details:

I have the LCD monitor hooked up to two machines, one VGA and one digital.

The machine that's using the VGA connection (the Ubuntu box) is the one that has the grub screen too far left.  (The grub screen from the digital connection is fine.)

Maybe I'm mistaken, but I'm assuming that if I change the monitor settings to move the grub screen to the right--that EVERYTHING ELSE will now be too far to the right? 

[edit]  Well, I just tried it, out of curiosity.   It wasn't possible to move it far enough to the right (the horizontal monitor setting was "50"--and moving it to "100" did move the grub menu to the right, but left most part of the menu was still off the screen).

S.

---

### Post by wilberfan on 2006-08-19
Just in case future n00bs find this thread, here's what fixed my problem:

When the GRUB menu came up, I just hit the "Auto" button on the side of my HP f1905 monitor!

D'oh!  

It (apparently) scanned what was displayed, and moved all of the text over accordingly....

Very nifty.

---

### Post by wieman01 on 2006-08-20
You're right. Pretty much what I did in the first place as well. So it WAS a hardware rather than a GRUB issue. :-)

---

