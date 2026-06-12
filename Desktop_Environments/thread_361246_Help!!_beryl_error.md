---
title: "Help!! beryl error"
date: 2007-02-14
forum: Desktop Environments
---

### Post by Opeth115 on 2007-02-14
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
 
i get that error whenever i type beryl-manager into my terminal anyone know what i could do?

---

### Post by Waappu on 2007-02-14
Hi

Have you this line in /etc/X11/xorg.conf file
```
Load "glx"
```

---

