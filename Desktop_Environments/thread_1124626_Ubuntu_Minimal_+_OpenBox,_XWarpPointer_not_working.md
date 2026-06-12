---
title: "Ubuntu Minimal + OpenBox, XWarpPointer not working"
date: 2009-04-13
forum: Desktop Environments
---

### Post by tommed on 2009-04-13
Hi Guys,

Apologies if this isn't the best place for this post, but it seemed the closest match..?

I am working on C program to control the mouse using hand gestures (and my webcam).. I have everything working, however when I call XWarpPointer nothing happens (no errors either!)

I thought it might be my code (available at [http://is.gd/rVpk]("http://is.gd/rVpk")), so I installed xdotools and called:

xdotools movemouse 10 10

..but nothing happened?! I believe that OpenBox (my window manager) is running on top of X11, so why wouldn't this work? I even tried running it as root (to see if it was a permissions problem) but that didn't work either.

I may also be worth noting that I am running the OS in a VirtualBox, hosted on a mac (sorry my setup isn't very simple?!!)

Could anyone suggest why I am unable to control the position of my mouse using X11 commands (either from my program or from xdotools)?

The code snippet I am using is basically:

//...
Display *xdisplay1 = XOpenDisplay(NULL);
if (!xdisplay1) exit(1);
XWarpPointer(xdisplay1, None, None, 0, 0, 0, 0, 10, 10);
XCloseDisplay(xdisplay1);
//...

It compiles fine, and xdisplay1 is definitely populated?!! HELP!

Many Thanks,
Tom

---

### Post by jordansissel on 2010-04-24
Found this post while digging into this exact problem ;)

This is a known issue with VirtualBox. Pointer movement initiated by the guest OS isn't forwarded to the host os, even in full screen mode.

This is the best response I could find on the topic: 
[http://forums.virtualbox.org/viewtopic.php?f=1&t=24496&start=75#p115917](http://forums.virtualbox.org/viewtopic.php?f=1&t=24496&start=75#p115917)

-Jordan

---

