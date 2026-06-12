---
title: "How do I get more Fonts?"
date: 2007-04-19
forum: Desktop Environments
---

### Post by SNYP40A1 on 2007-04-19
I want the fonts that I had in WinXP.  How do I install more fonts?

---

### Post by girishv on 2007-04-19
If you still have windows XP, you can use all the truetype fonts you have. Just make a directory (I call it /home/myname/.fonts). Copy the fonts (.ttf files) from windows XP (it will be under WINDOWS/Fonts directory). Add the font path to X

cd .fonts
mkfontscale
mkfontdir
xset +fp /home/myname/.fonts
xset fp rehash

replace directory with the full path of the directory where you copied your fonts

Your fonts will be seen by all the programs. One easy way is to install msttcorefonts package.

Goodluck

Girish

---

