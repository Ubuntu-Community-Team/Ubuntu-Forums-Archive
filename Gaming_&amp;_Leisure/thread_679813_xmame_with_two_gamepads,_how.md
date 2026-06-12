---
title: "xmame with two gamepads, how ?"
date: 2008-01-27
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2008-01-27
Hello, 

I have 2 gamepads, that are detected in the /dev/input.

I would like to get xmame working with them both:
```
 xmame mameroms/myrom.zip -fullscreen -jdev /dev/input/js0  -jdev /dev/input/js1
```
  
>  xmame mameroms/myrom.zip -fullscreen -jt 1

and no way to get both working. What probably i am entering wrong in the code ?

thanks for infos !

---

### Post by frenchn00b on 2008-01-28
S O L V E D !

```
xmame.SDL mameroms/myrom.zip -fullscreen -jt 5 -ef 5
```

PRESS TAB 
go in player 1, and configure hte gamepads
up
1/SUPPR to put NONE
2/ choose the stick direction.. .
next down

---

