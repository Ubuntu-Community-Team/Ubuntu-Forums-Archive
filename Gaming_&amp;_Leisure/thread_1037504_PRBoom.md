---
title: "PRBoom"
date: 2009-01-11
forum: Gaming &amp; Leisure
---

### Post by G-Dub on 2009-01-11
Hey guys, I installed PRBoom via synaptic package manager. I have all the original doom .wad files. Where do I put them so I can use them with PRBoom?

Thanks in advance!

---

### Post by G-Dub on 2009-01-12
any ideas?

---

### Post by Dark Aspect on 2009-01-12
> **G-Dub said:**
> Hey guys, I installed PRBoom via synaptic package manager. I have all the original doom .wad files. Where do I put them so I can use them with PRBoom?

Thanks in advance!

Hello,

you can place your iwads in the /usr/share/games/doom directory under the filenames doom.wad, doom2.wad, tnt.wad etc. Additionally you can start the game telling prboom where it can find your iwads.

```
prboom -iwad /link/to/doom2.wad
```

---

### Post by G-Dub on 2009-01-13
beautiful! this is exactly the info i needed! thanks for the pm too ;)

---

