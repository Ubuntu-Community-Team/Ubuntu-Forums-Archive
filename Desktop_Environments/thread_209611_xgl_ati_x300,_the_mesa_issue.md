---
title: "xgl ati x300, the mesa issue"
date: 2006-07-05
forum: Desktop Environments
---

### Post by faz on 2006-07-05
hi,
i've an ati x300 mobility, I configured the ati drivers from the official at website and they works perfectly under xorg (no xgl):
```
:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X300 Generic
OpenGL version string: 2.0.5879 (8.26.18)

```
but if i use xgl instead of xorg i get
```
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
```
without changing a line in my conf! can't really understand!

thank you all who could help me a bit
cheers
fa

---

### Post by Whoopie on 2006-07-21
I also have this issue!

And I can't find a solution. Did you get it to work?

Best regards,
Whoopie

---

### Post by linedpaper on 2006-11-02
i'm having the same issue.  did either of you get this to work?

---

