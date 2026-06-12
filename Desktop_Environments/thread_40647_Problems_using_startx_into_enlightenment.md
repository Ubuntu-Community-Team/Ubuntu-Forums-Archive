---
title: "Problems using startx into enlightenment"
date: 2005-06-09
forum: Desktop Environments
---

### Post by Pixel on 2005-06-09
Everything was working fine until I installed my nVidia drivers, they work fine, but now my xorg is odd

I can boot into stuff fine with it, it's jsut what happens when I type startx.

If I type startx, it goes straight into gnome, but if I try to go into another WM like fluxbox or enlightenment, It gets errors saying it's not a valid arguement.

How can I change it so it doesnt automaticly boot into gnome? I'd prefer if I could just have it boot straight into Enlightenment instead of gnome, via startx.

---

### Post by defkewl on 2005-06-10
Add /home/user/.xinitrc with this command:
exec enlightenment

---

