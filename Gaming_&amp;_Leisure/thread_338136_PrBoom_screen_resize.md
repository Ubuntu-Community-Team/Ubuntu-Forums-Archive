---
title: "PrBoom screen resize"
date: 2007-01-14
forum: Gaming &amp; Leisure
---

### Post by benuski on 2007-01-14
When I try to play Doom on PrBoom, the screen is very small in the middle of a lot of black space.  Is there any way to make the screen larger?  Also, does anyone know how to play Doom II through PrBom or lxdoom?  I'm pretty sure that it is in the freedoom package.
Thanks!

---

### Post by BoyOfDestiny on 2007-01-14
> **benuski said:**
> When I try to play Doom on PrBoom, the screen is very small in the middle of a lot of black space.  Is there any way to make the screen larger?  Also, does anyone know how to play Doom II through PrBom or lxdoom?  I'm pretty sure that it is in the freedoom package.
Thanks!

Sure. You just need to edit your prboom.cfg

nano ~/.prboom/prboom.cfg
or gedit ~/.prboom/prboom.cfg

Under #Files, just make it point to your DOOM2.WAD (EDIT: Just to clarify, you need a copy of DOOM2 for that file, or you can use the shareware wad. The doom engine is open sourced, but the game data itself isn't... That's why freedoom exists as a "replacement", and the package doesn't contain the actual ID doom games)

Under #Video, change the settings as you see fit.

Have fun!

---

