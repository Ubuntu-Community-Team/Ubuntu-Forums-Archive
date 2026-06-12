---
title: "Making a window big causes it to freeze/stop redrawing"
date: 2009-04-13
forum: Desktop Environments
---

### Post by memories on 2009-04-13
This is very annoying. If I make a window "too big" it will stop redrawing.

If I maximize the Firefox window, it will turn gray and stay gray until I resize it down to something small like 800x600. Then it works perfectly. 

This happens with any window. With videos, if I open a video and then make it full screen, It begins blinking (the entire screen), but if I un-maximize it and then maximize it again, it works. This is only with videos though. With other apps they never work in fullscreen. 

This happens with pretty much every window. i.e., if I open a text file, it opens maximized in gvim by default, and I need to manually drag the edges to make it smaller than half the screen before I can see the text and the cursor blinks etc. 

This does NOT happen if the window opens up maximized by default along with Gnome. For example I have some prism windows that open up maximized, and they can remain maximized for the enter session. I can also minimize/maximize with no problems afterwards, but if I open a new window (same app), it will have the annoying behavior described above. 

A maximized console window turns all black. 

**I'm using **
compiz
ubuntu 8.10
geforce 8600 w/ official 177.82 drivers
Kernel 2.6.27-9-generic
I'm using dual screen with twinview

I don't remember when the problem began. It never happened in 8.04 but I don't think it began right after 8.10 - but I've had it for months but have been too lazy to post about it. I was thinking about just waiting for 9.04 but this is unbearable. 

Can I upgrade my Ibex to 9.04 beta using apt-get?

---

### Post by etjacobsen on 2009-06-17
Is there any word on this bug? Does this appear in the bug tracker?

I am running:
OS: 64-bit 9.04 Ubuntu
Video Card: nVidia Quadro NVS 140M(from lspci) with 512mb memory
nVidia Driver: 180.44
Resolution: Running two monitors at 1680x1050 each for 3360x1050 combined.

This is extremely frustrating, windows will sometimes randomly seem to stop redrawing and must be lowered in size to see, sometimes around half the size of a single monitor, making most software practically unusable at that size.

It *seems* to happen when the system is running low on memory, so possibly related to using swap or somehow not allocating video memory properly.

---

