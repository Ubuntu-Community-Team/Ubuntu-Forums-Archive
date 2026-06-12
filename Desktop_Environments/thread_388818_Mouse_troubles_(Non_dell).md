---
title: "Mouse troubles (Non dell)"
date: 2007-03-19
forum: Desktop Environments
---

### Post by nick_karstedt on 2007-03-19
Alright, so I've got the rig I built, no dell components whatsoever.  I've tried 2 mice so far, and both of them have the same result.  I've burnt 3 copies of the latest 32bit build, same result.  Whenever I move my mouse, it hops all over the screen and preforms mouse clicks, both left and right.  It's completely spastic.  After about 5 sec of that, it completely locks up, and I can not use my mouse OR keyboard (Which functions perfectly until this occurs).

I'm going to try that ```
noapic irqpoll pci=routeirq
``` in boot options and see if that helps... we'll see.  Is there an explanation for this or an actual fix?

The mice are a wireless optical usb compaq (direct logitech ripoff) and a wired optical usb logitech.  I tried each of them, and both of them.

---

### Post by nick_karstedt on 2007-03-20
As I thought, same result.....

---

### Post by nick_karstedt on 2007-03-20
Well awesome, disabling legacy usb is the key!  Glad the problem is fixed right after asking for help... as always....

---

