---
title: "XGL/Compiz and OpenTTD"
date: 2006-06-03
forum: Gaming &amp; Leisure
---

### Post by Hagbarddenstore on 2006-06-03
Well... I have nVidia GLX and xgl/compiz. It works fine... But when i start the game OpenTTD it's transparent... and i se my background picture... I dont wanna have it transparent... any idea howto make not transparent so i can play again?

---

### Post by Paool on 2006-06-18
I've got the same problem... :( Any ideas?

---

### Post by Scunizi on 2006-06-18
"Alt" mouse scroll wheel doesn't change it?  or right mouse click on title bar and choose transparancy restetting the level?  Never played this game so just throwing darts.

---

### Post by Paool on 2006-06-19
no, it isn't transparent, just... has no background o_O

---

### Post by Paool on 2006-06-19
problem's solved :) just type:

export XLIB_SKIP_ARGB_VISUALS=1 && XLIB_SKIP_ARGB_VISUALS=1 openttd

and OpenTTD works fine under xgl :D

---

