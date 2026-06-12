---
title: "MetaPhi"
date: 2007-05-22
forum: Education &amp; Science
---

### Post by Annalisa on 2007-05-22
Hi!
I tried to install MetaPhi a math program to draw vector fields and more other...
It provides also graphics 3D and I have SiS360, I know is not good for 3D, but I'm actually interested in 2D.
Now the problem is that I cannot find the executable that the readme promised me!
Anyone may help me?

---

### Post by Zootropo on 2007-05-22
> **Annalisa said:**
> Hi!
I tried to install MetaPhi a math program to draw vector fields and more other...
It provides also graphics 3D and I have SiS360, I know is not good for 3D, but I'm actually interested in 2D.
Now the problem is that I cannot find the executable that the readme promised me!
Anyone may help me?

Try to find it with locate or find -name

---

### Post by Annalisa on 2007-05-22
I will be more clear:
I'm sorry but I don't know the name of the executable, the readme says there is the executable but no name for it.....
I paste down here the answer of compilation:

annalisa@computer:~/Desktop/metaphi$ make
g++ -Wall -O3 -I/usr/include/ -I/usr/include/SDL -D_GNU_SOURCE=1 
-D_REENTRANT -D_HAVE_MMX_CPU_ -c vector3d.cpp
vector3d.cpp: In member function ‘float Vector3D::norm() const’:
vector3d.cpp:44: error: ‘sqrt’ was not declared in this scope
make: *** [vector3d.o] Error 1

and this is the output of glx:

annalisa@computer:~/Desktop/metaphi$ glxinfo
name of display: :0.0
X Error of failed request: GLXBadContext
Major opcode of failed request: 142 (GLX)
Minor opcode of failed request: 5 (X_GLXMakeCurrent)
Serial number of failed request: 17
Current serial number in output stream: 17

and sdl seems to work!
annalisa@computer:~/Desktop/metaphi$ sdl-config
Usage: sdl-config [--prefix[=DIR]] [--exec-prefix[=DIR]] [--version] 
[--cflags] [--libs] [--static-libs]

Now the result is that I have no executable in the metaphi directory.
I actually have a text-mmx.sh, just this and I don't know how to open 
it, which software I have to use?
What do you think about these errors?

Bye ^_^

---

### Post by kleeman on 2007-05-22
The subroutine vector3d.cpp is not compiling because it doesn't know where the sqrt function is. It must be missing the math headers. Look in the file and find the lines starting with #include and add this line:
#include <math.h>


Then redo make.

Looks like a weird bug.....

Edit: Out of curiosity I compiled it myself with the fix above and it works.

---

### Post by Annalisa on 2007-05-22
thank you so much!!!
I've got an executable!
But I can't open it...why?
I know, it seems a stupid question, but I actually can't!
This is the output after did what you said...

annalisa@computer:~/Desktop/metaphi$ sudo make
g++ -Wall -O3 -I/usr/include/ -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -D_HAVE_MMX_CPU_ -c vector3d.cpp
g++ -Wall -O3 -I/usr/include/ -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -D_HAVE_MMX_CPU_ -c plots3d.cpp
plots3d.cpp: In function ‘void cache_param_3d(unsigned char, unsigned char, const ExprChunk&, const ExprChunk&, const ExprChunk&)’:
plots3d.cpp:438: warning: ‘z’ may be used uninitialized in this function
plots3d.cpp:438: warning: ‘y’ may be used uninitialized in this function
plots3d.cpp:438: warning: ‘x’ may be used uninitialized in this function
plots3d.cpp:487: warning: ‘z’ may be used uninitialized in this function
plots3d.cpp:487: warning: ‘y’ may be used uninitialized in this function
plots3d.cpp:487: warning: ‘x’ may be used uninitialized in this function
plots3d.cpp: At global scope:
plots3d.cpp:1248: warning: ‘void DrawVector(float, float, float, Vector3D&)’ defined but not used
g++ -Wall -O3 -I/usr/include/ -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -D_HAVE_MMX_CPU_ -c expr.cpp
g++ -Wall -O3 -I/usr/include/ -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -D_HAVE_MMX_CPU_ -c metaphi.cpp
g++ -Wall -O3 -I/usr/include/ -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -L/usr/X11R6/lib -L/usr/lib -L/usr/lib -lSDL -lGL -lGLU -lm -ldl -o metaphi interval-math.o other-funcs.o font-stuff.o graph-misc.o plots2d.o vector3d.o plots3d.o expr.o metaphi.o
annalisa@computer:~/Desktop/metaphi$ metaphi
bash: metaphi: command not found


annalisa@computer:~/Desktop/metaphi$ ls
ChangeLog  expr.o          graph-misc.h       Makefile         other-funcs.h  plots3d.h      vector3d.h
COPYING    font-stuff.cpp  graph-misc.o       metaphi          other-funcs.o  plots3d.o      vector3d.o
doc        font-stuff.h    interval-math.cpp  metaphi.cpp      plots2d.cpp    README
examples   font-stuff.o    interval-math.h    metaphi.h        plots2d.h      test-mmx.sh
expr.cpp   global.h        interval-math.o    metaphi.o        plots2d.o      vector3d.cpp
expr.h     graph-misc.cpp  macosx             other-funcs.cpp  plots3d.cpp    vector3d.cpp~
annalisa@computer:~/Desktop/metaphi$ metaphi
bash: metaphi: command not found

---

### Post by kleeman on 2007-05-22
Try 

./metaphi "(theta rho z)=(u sqrt(v^2+1) v)" -u 0,6.284 -v -10,10

(the subdirectory where the executable is not in your path so you need to put ./  in front)

---

### Post by Annalisa on 2007-05-23
ok!! it works!
thank you so much!
This software is great to draw functions and vector fields...
again, thank you!

---

