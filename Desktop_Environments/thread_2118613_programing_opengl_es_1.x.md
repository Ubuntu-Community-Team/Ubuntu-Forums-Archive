---
title: "programing opengl es 1.x"
date: 2013-02-21
forum: Desktop Environments
---

### Post by mIXpRo on 2013-02-21
hi,

since ubuntu phone os and tablet will be using opengl es ,
i wanted to program somthing using it , i search software center for anything related and i found [COLOR=Navy]libgles1-mesa-dev[/COLOR] i wrote a simple main program and included :
#include <GLES/gl.h>
#include <GLES/glext.h>

and it compiles , but if try to use an opengl es function it says undefined reference .
(meaning the include without using functions compile , but after writing a function it give that error)

i compiled using simple 
gcc ./*.c -o xxx

how can i use this library to program opengl es 1.x ??


thnks

---

