---
title: "OpenGL function cause segmentation fault"
date: 2008-12-11
forum: General Help
---

### Post by Python101 on 2008-12-11
A few days ago, I was exploring a new tool to wrap around PyOpenGL, and in doing so found that almost any OpenGL function caused a segmentation fault in libGL.so.1.

Run in GDB,

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb7d938c0 (LWP 6055)]
0xb7af4156 in glGetError () from /usr/lib/libGL.so.1

python commands run:

```
glutInit()
glutInitDisplayMode(GLUT_RGBA|GLUT_DOUBLE|GLUT_DEPTH)
```

Newst version of PyOpenGL was used. (3.0.0b8 )
I am running Xubuntu 8.10 with all updates.

---

### Post by paradox82 on 2009-01-12
same exact problem. I read a lot of other people are have the same problem but i couldnt find a fix.

```

from OpenGL.GLUT import *
glutInit()
glutInitDisplayMode(GLUT_SINGLE)

```
Gives "segmentation fault". GLUT_DOUBLE does the same

some info running ubuntu 8.10.
```
uname -a
Linux rado-tablet 2.6.27-9-generic #1 SMP Thu Nov 20 21:57:00 UTC 2008 i686 GNU/Linux

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

```

interesting things is that there is a semi-work around. This

```

from OpenGL.GLUT import *
glutInit()
glutCreateWindow('test')
glutInitDisplayMode(GLUT_SINGLE)

```

works fine but the window doesnt integrate with the OS (dont know hhow to describe it otherwise). The picture is there but there is no boundary or close, minimize buttons.

Hope this helps

---

