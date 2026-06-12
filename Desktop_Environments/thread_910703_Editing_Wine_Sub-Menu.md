---
title: "Editing Wine Sub-Menu"
date: 2008-09-04
forum: Desktop Environments
---

### Post by Bionic Apple on 2008-09-04
I have a really basic question that has not been answered from friends, forums, and even IRC, yet.  Make sure that you try your answer out before you submit it, because this is actually harder than you think.

**How do you put shortcuts into the Wine sub-menu _without_ Alacarte or tools which require downloading?**

So far,  I have put a shortcut into ~/.local/share/applications/wine/.  I edited it with a text editor and put "*Categories=Application;xxxx;*" in.  For xxxx, here are the following values which have _not_ worked of the top of my head: Wine, wine, wine-wine, and Wine-Wine.

---

### Post by Bionic Apple on 2008-09-05
Bump.

---

### Post by Bionic Apple on 2008-09-06
Bumpety Bumpy Bump.

---

### Post by Bionic Apple on 2008-09-07
Repeat after me: B, U, M, P, Bump!

---

### Post by Bionic Apple on 2008-09-08
pumB | Bump

---

### Post by Bionic Apple on 2008-09-10
|) || A A   |)
|) U / v \ |

---

### Post by Bionic Apple on 2008-09-11
**B**ump, **U**mp, **M**p, **P**.

---

### Post by Bionic Apple on 2008-09-12
Lump, Hump, Bump.

---

### Post by Bionic Apple on 2008-09-13
Bum- screw it!  No one knows the answer?

---

### Post by AppleSeed2010 on 2008-09-14
Try to create a file in ~/.local/share/applications like thegame.desktop
A little exemple of mine for wow carto

> 
[Desktop Entry]
Name=WoW Cartographe
Comment=Carte de World of Warcraft
Terminal=false
Type=Application
Categories=Wine;
Exec=/home/xxxxxxxxxx/.wine/Cartographe
Icon=/home/xxxxxxxxxx/.wine/8631_wowcartographe.0.xpm


It should work.

NB : BUMP ^^

---

### Post by Bionic Apple on 2008-09-14
That didn't work.

---

