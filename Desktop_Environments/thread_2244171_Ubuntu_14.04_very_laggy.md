---
title: "Ubuntu 14.04 very laggy"
date: 2014-09-14
forum: Desktop Environments
---

### Post by marshal-banana on 2014-09-14
hi, I have Acer e725 laptop , 2gb ram, dual boot, win xp sp3, ubuntu 14.04. Ubuntu 14.04 is very laggy and freezes alot especially at web browsing, and images scrolling, and grays alot,, how can I solve this?? thx

---

### Post by grahammechanical on 2014-09-14
What graphic adapter does the machine have? How much of its own memory does the graphic adapter have? Run this command

```
/usr/lib/nux/unity_support_test -p
```

What results do you get?

Regards.

---

### Post by marshal-banana on 2014-09-14
hi i get this:

OpenGL vendor string:   Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 
OpenGL version string:  2.1 Mesa 10.1.3

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

---

