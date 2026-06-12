---
title: "[SOLVED] Warcraft 3 through WINE lags. A lot."
date: 2008-12-20
forum: General Help
---

### Post by Cadeyrn on 2008-12-20
I know I have full support for my video card and OpenGL and everything, and I have my video card drivers installed, and I have Warcraft III set to OpenGL, etc., but when I launch it even the menus are extremely choppy. It also flashes me pieces of the desktop. As far as any other aspect of the game... Well, truthfully I'm too afraid to try.

---

### Post by Cadeyrn on 2008-12-21
Hmm... Well, I manage to accidentally figure out the artifacts and flashes were because I had Visual Effects on for Compiz. The lagging is still unknown, but I'm gonna try installing the ATI driver. I thought I wouldn't need it since Alien Arena and even Extra Visual Effects doesn't lag one teeny bit, but I'm gonna try it.

---

### Post by blackgr on 2008-12-21
Try running war3.exe with -opengl frefix.

```
wine war.exe -opengl
```

and dont forget to turn off compiz

---

### Post by Cadeyrn on 2008-12-21
It worked!! Your idea combined with my ATI driver finally installed properly.

In fact, it's in my other workspace updating right now. :)

EDIT: Ooh! The driver also undid the random deletion of my favorite Human-Clearlooks theme, and it also made my keyboard's volume wheel not take forever to be recognized!

---

