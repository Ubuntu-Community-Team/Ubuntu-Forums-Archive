---
title: "Desktop frame rate drops after compiz is restarted"
date: 2009-09-16
forum: Desktop Environments
---

### Post by weave on 2009-09-16
Hey everyone.


In short, I can't get Compiz to restart properly with direct rendering; here are some precisions:

When it's started by the X session manager, Compiz runs fines at 60 frame/sec vsynced to my monitor. Howewer, when I switch over to Metacity, and then back to Compiz using the Compiz Fusion Icon, the desktop's frame rate becomes very low, maybe 15 frames per second (for all and any animations).

Even when the desktop's frame rate is very low:
- Compiz doesn't seem to use much CPU (<1%)
- glxgears' (non-vsynced) performance remains the same, so I assume GPU usage by Compiz remains similar

The only way I've found to work around this is to enable indirect rendering (in which case the problem does not manifest), but I just can't get Compiz to restart properly with direct rendering.

I have no clue what the source of the problem could be, any help would be appreciated. Thanks in advance.


Some relevant (maybe?) info:

Running Ubuntu 8.10 x64
Graphics card is Nvidia GF9600GT
Using Nvidia binary drivers 180.11
Vsync enabled in Compiz/driver/anywhere I can think of.

---

