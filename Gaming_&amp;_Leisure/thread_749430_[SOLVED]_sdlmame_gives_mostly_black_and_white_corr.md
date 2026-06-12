---
title: "[SOLVED] sdlmame gives mostly black and white corrupted visuals"
date: 2008-04-08
forum: Gaming &amp; Leisure
---

### Post by pabc on 2008-04-08
sdlmame 0.123 seems to work fine up until I actually start a ROM.

The video output is black and white only, with maybe every other 10 pixels not rendered and the screen half wrapped around on itself.

I cant see anything obvious in the ini file. 

Any suggestions?

---

### Post by pabc on 2008-04-08
I've changed video to 'soft' instead of 'opengl' in the ini file and it works fine now.

---

### Post by disturbedite on 2008-04-08
you should also update to 0.124.

---

### Post by svamppi on 2008-08-31
I have the same problem. And while it works fine when setting rendering to soft it would be nice to know why opengl doesn't work. I have an ati radeon x1950 pro.

---

### Post by FranMichaels on 2008-08-31
Does setting antialias=0 (under "vector options") in mame.ini fix it?

Also, are you using the open source drivers or fglrx. If the latter, that's likely why its sucking...

---

### Post by Number6 on 2008-09-19
Seems that having Compiz activated can cause choppy sound too, I'm under fglrx! Why the hell can't ATI get it right for god's sake?

---

### Post by jukingeo on 2008-11-30
> **FranMichaels said:**
> Does setting antialias=0 (under "vector options") in mame.ini fix it?

Also, are you using the open source drivers or fglrx. If the latter, that's likely why its sucking...

I have the same problem too and I also set my video from "opengl" to "soft" and that did the trick.  I did try your suggestions but they didn't work.

More then likely I do have the open source drivers as I do remember having trouble getting the company's drivers to work.  I have an ATI 9600XT video card.

The games I tried thusfar (arkanoid, pacman, mspacman, etc) do run with plenty speed enough.  So perhaps I am just best off leaving it set at soft.  At least it is working.

Geo

---

