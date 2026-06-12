---
title: "Keyboard input stops mouse"
date: 2009-11-07
forum: Desktop Environments
---

### Post by darren.shepherd on 2009-11-07
I upgraded to 9.10 and this "bug" is driving me absolutely nuts.  The problem is that when you start typing on the keyboard, the mouse will not move while you are typing.  To reproduce this all you have to do is just move the mouse left and right continuously and then just start typing.  You'll see the mouse won't move anymore.  I have two computers (a Dell D610 laptop and Mac Mini) with 9.10 installed and both have this behavior.  I also tried the 9.04 live CD and confirmed this didn't happen in 9.04.  Please somebody help me.

I assume this has something to do with the X server, or the kernel itself.  You can simulate the issue with just an xterm, so I don't think its gnome, compiz, or anything else.

Darren

---

### Post by marco123 on 2009-11-07
On my laptop it's an option in Preferences>Mouse "Disable touchpad while typing".  Not sure about normal keyboards though, could be the same.

Cheers, Marco.

Edit: I just checked my desktop and the option isn't there, sorry, so don't know about the Mac Mini.

---

### Post by flokason on 2009-11-11
this happens to me also on my desktop pc, laptop is fine

Anyone  knows whats going on?


ps. I have bluetooth mouse and keyboard, but when I use usb mouse and keyboard, this also happens

---

### Post by coffeecat on 2009-11-11
No problem here in Karmic with USB keyboard and mouse. Perhaps this is a hardware-specific bug. Perhaps those affected could post a launchpad bug report.

---

