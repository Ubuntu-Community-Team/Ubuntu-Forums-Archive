---
title: "Window Behavior Changes when Adding Third Monitor"
date: 2011-02-26
forum: Desktop Environments
---

### Post by bcollier on 2011-02-26
When I run my dual monitors with twinview on an NVidia GeForce 8400GS when I maximize a window it does it as you would expect (on one monitor) and when a pop up comes out of an application or when I bring up Synapse it appears in the center of my monitor.  However, when I add a third monitor as a separate X window, the behavior of the windows on my dual screens becomes very different.  It maximizes across both monitors, and Synapse opens with the center between the two monitors.

Any thoughts on how to fix this or why it would change?

---

### Post by Krytarik on 2011-02-27
Hi bcollier and welcome to the forums!

I don't know exactly how the TwinView option of the nvdia driver works, but I did a web search a while ago on how to get it to handle 3 monitors, and it seems that it can only handle 2 monitors.

So, I guess what is happening in your case is that TwinView handles the first both monitors as one and the third as the other one. I would try to set up the xorg.conf that way, that the third monitor is not handled by TwinView, this guide may be handy for this:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

Greetings.

---

### Post by bcollier on 2011-03-08
thanks, I tried that and the interface was just clumsy, having a seperate screen that I couldn't reach.  I use hotkeys a lot, and you never knew where the program would pop up.  As a result I just put my third monitor on a shelf until better support comes along.  windows 1, ubuntu 0.

---

