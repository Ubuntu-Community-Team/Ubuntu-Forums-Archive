---
title: "Can u use xwinwrap with gxmame"
date: 2006-08-01
forum: Gaming &amp; Leisure
---

### Post by nero2150 on 2006-08-01
I wonder if it is possible. I m using gxmame in xgl/compiz but it loads up as 
a transparent desktop with the game playing but you cannot use any apps tho u can play because it is on top of everything :confused: 
So I was thinking it wound be cool :cool:  to have an arcade playing desktop.
I dont know how to type the cmd for xwinwrap

Might be something like

 xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- xmame etc etc something blabla romname
Plz can someone help. basically I a noob.. #-o

---

### Post by morphx on 2007-05-02
Sure...
Try this:
```
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- xmame -rid WID 1941
```

Of course, change "1941" for a rom that you "own"...

---

