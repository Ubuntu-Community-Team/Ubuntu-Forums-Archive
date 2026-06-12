---
title: "i know it's on here, but i forget where"
date: 2008-12-20
forum: General Help
---

### Post by Forbees on 2008-12-20
when i try and play a movie, i get the error "frame skip 8"

i'm using mplayer

i know to fix it, you change some setting . . . . from terminal . . . ?

i forget, i had it done on here, but than i upgraded to ibex and forget how to do it

all i remember, is i type some code in terminal, a window opened up, and i had a choice between 2 or 3 check boxes 

help?

---

### Post by taurus on 2008-12-20
```
gmplayer
```

---

### Post by Forbees on 2008-12-20
that just opens mplayer, didn't fix the flashing

it also tries to stay ontop of other windows, which might be part of the problem too

---

### Post by taurus on 2008-12-20
If it's a video problem, run

```
mplayer -vo **xv**
```
or another video driver.

```
mplayer -vo help
```
for a list of drivers.

---

### Post by Forbees on 2008-12-31
i'm not seeing how this would help . . . it's just listing information

but maybe i need to use a different video driver?

it flickers like a bad refresh rate you see in games . .

---

