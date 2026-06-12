---
title: "X not redetecting USB mouse after plugging back in"
date: 2005-07-16
forum: Desktop Environments
---

### Post by One Quick Question on 2005-07-16
(I guess I don't have One Quick Question after all.)

Ok, I have an old, junky PS/2 mouse attached to a KVM switch.  I also have a sleek MX 1000 [Dr. Evil]*laser*[/Dr. Evil] mouse on USB.  I move the USB mouse around to whichever computer I'm using heavily at the time.

Now, if I start X with the mouse plugged in, it works, but if I plug it in any time while X is running, it ... doesn't work.  Sort of.
lsusb lists the mouse, and it responds to cat calls (haha, my first Linux pun!), but X ignores it.

In the xorg.conf file, I've tried to make X listen on /dev/input/mice, /dev/input/mouse1, and /dev/input/event3, but they all behave the same.

I'd rather not have to restart X every I want to use the USB mouse after I plug it back in.

Any ideas?

---

