---
title: "nvidia, fast user switch, terminal woes"
date: 2006-07-21
forum: Desktop Environments
---

### Post by soulcoughy on 2006-07-21
I'm running dapper with kernel 2.6.15-26-k7.
I'm using the repository nvidia kernel & glx drivers.

GL apps work fine, X starts fine.  If i try to do a ctrl-alt-f1 to get me to a console, the entire screen gets all funky.  Stripes of orange everywhere, strange ghosted image.  Really weird.  If i try to do a user switch after the machine has been locked by a screensaver, I end up with a black screen that I can't recover from.

I've tried different versions of the NVIDIA drivers.  Some cause the machine to lock up at random, others exhibit the same behavior I'm experiencing now.

If it matters, the card is a FX5700 and It's driving DVI @ 1680x1050x60Hz

Does anyone have any idea what's going on?  I suspect the nvidia drivers, I guess the next step is to try vesa and see if the same thing happens, but I need GL, so that won't represent a fix.  Thanks.

Edit:  The NV drivers don't suffer from either of these problems.

Brian

---

