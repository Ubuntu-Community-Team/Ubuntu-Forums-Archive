---
title: "Warcraft 3 Help"
date: 2006-10-04
forum: Desktop Environments
---

### Post by SexyPastry on 2006-10-04
I installed warcraft3 fine and everything then this error came up from wine when i tried loading it

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!

Any ideas?

---

### Post by Lord Illidan on 2006-10-04
Do you have 3D drivers installed? What is the make of your videocard?
Also, type glxinfo in a terminal and copy output here.

---

### Post by SexyPastry on 2006-10-04
I have a nvidia Geforce 6600 GT 128MB  and the glxinfo says

glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

does that help?

---

### Post by skwillz on 2006-10-04
You could try this (or make sure it is already there)..

(assuming you are in gnome)
```

sudo gedit /etc/X11/xorg.conf
```

go to the Modules section

make sure this is there

```
	Load	"glx"
```

Hope that works.

---

