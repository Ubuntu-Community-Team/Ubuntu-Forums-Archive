---
title: "projectM not working?"
date: 2009-05-01
forum: General Help
---

### Post by RSiN on 2009-05-01
I tried installing projectM with synaptic, and I'm not sure what exactly those packages are supposed to give me. I don't see any visualisations for it in totem or rythmbox. There's also no icons or entries to start a separate app in my menus/desktop.

I then also tried to install it manually from sourceforge, but I'm a newb at that stuff, and did not get it to install.

Can anyone give me a step-by-step guide for this? Maybe a link to one that works? I tried serveral from these forums, but was unsuccessful, although I didn't try the SVN guide.

Any help here is appreciated :D

I'm currently using Ubuntu 9.04 Jaunty.

---

### Post by RSiN on 2009-05-01
Just a little more info, when I try to compile it using instructions from another tutorial, I get this error

```
Scanning dependencies of target projectM
[  2%] Building CXX object CMakeFiles/projectM.dir/projectM.o
In file included from /home/rsin/libprojectM-1.2.0/Renderer.hpp:4,
                 from /home/rsin/libprojectM-1.2.0/projectM.cpp:59:
/home/rsin/libprojectM-1.2.0/FBO.hpp:35:21: error: GL/glew.h: No such file or directory
make[2]: *** [CMakeFiles/projectM.dir/projectM.o] Error 1
make[1]: *** [CMakeFiles/projectM.dir/all] Error 2
make: *** [all] Error 2

```

In that directory I can see there's a glew.h file, but I don't think I have that file in my GL folder...

```
rsin@rsin-ubuntu:/usr/include/GL$ ls
glext.h  gl_mangle.h  glu_mangle.h  glx.h         internal
gl.h     glu.h        glxext.h      glx_mangle.h

```

Anyone know if this could be my problem, or how to fix it?

---

### Post by RSiN on 2009-05-01
Ok, so I installed the glew-dev package, and got it installed, also had to install the pulseaudio-dev package for that part of it.

Now it's all up and running :D

---

