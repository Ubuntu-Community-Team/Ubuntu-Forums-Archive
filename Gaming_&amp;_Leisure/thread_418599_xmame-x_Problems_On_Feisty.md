---
title: "xmame-x Problems On Feisty"
date: 2007-04-22
forum: Gaming &amp; Leisure
---

### Post by jlacroix on 2007-04-22
Hello, I'm trying to get xmame to work but I am getting these errors:
```

GLERROR: cannot access GLU library libGLU.so
GLERROR: dlerror() returns [libGLU.so: cannot open shared object file: No such file or directory]
Use of OpenGL mode disabled
XDGAOpenFramebuffer failed
Use of DGA-modes is disabled
Error: video mode 2 is not available

```
Opengl games such as penguin racer work fine and I am using the nvidia driver. I tried making a symbolic link that was described in a different thread but it didn't work. :(

---

### Post by ulmcnoob on 2007-04-28
xmame is looking for "libGLU.so" in feisty it is called "libGLU.so.1" 
easy fix make a copy of the file in the name it is looking for

```
sudo cp '/usr/lib/libGLU.so.1' '/usr/lib/libGLU.so'
```

note: i'm a linux noob

---

### Post by jlacroix on 2007-04-28
Thanks!

---

