---
title: "kq loading/graphics problems"
date: 2008-03-15
forum: Gaming &amp; Leisure
---

### Post by LordRaigan on 2008-03-15
Hi im currently new to ubuntu and the linux world ,and im having trouble with the game kq. I downloaded it and opened it and the graphics are all messed up. The sound is fine just the graphic are diagonal lines of different pieces of the game. Someone please help!

---

### Post by acoustibop on 2008-03-15
Have you tried the repository version of the game, LordRaigan?

Also, from the readme in the download:> This game requires the following libraries (not included):

Allegro Game Library 4.2
Dumb Sound Engine 0.9
The libaldmb1 Runtime library
Lua 5.0

Older or newer versions of these libraries will probably not work. Allegro usually breaks ABI
compatability at point releases. Lua 5.1 will not work with this binary.

Do you have the necessary dependencies installed?

**Edit:** FWIW I'm running Gutsy and have all those libraries installed, so I'd guess they're included by default in an up-to-date Gutsy installation.

---

