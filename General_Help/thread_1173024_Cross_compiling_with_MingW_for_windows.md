---
title: "Cross compiling with MingW for windows"
date: 2009-05-29
forum: General Help
---

### Post by bgbnbigben on 2009-05-29
Hey guys,

So recently i coded a bunch of crap with glut 'because i could', and now i have the urge to show off to my friends.
They all use windows, i use linux.

I installed MinGW, and have no problem cross compiling with it, except for when it comes to linking to the GLUT library.
At this point, i cant, for the life of me, work out what to do to get it to compile with the GLUT library.

When i use g++, this works fine, and even produces a great snowman army, however using either the -lglut32 or the -lglut switch for MinGW just produces an error proclaiming that my "GL/glut.h" file doesnt exist, as well as going on to tell me that all of the glut functions ive called dont exist (due to the lack of the header file)

Can anyone help me iron out this problem?
Thanks,
Ben

---

### Post by ActiveFrost on 2009-05-29
Linking to these libs ( exactly in the same order as shown below ) **might** solve your problem : 
```
-lglut32 -lglu32 -lopengl32
```

---

### Post by bgbnbigben on 2009-05-30
```
ben-ubuntu:file_name_goes_here$ i586-mingw32msvc-c++ snowman.cpp -o snowman.exe -O3 -lglut32 -lglu32 -lopengl32
snowman.cpp:3:21: error: GL/glut.h: No such file or directory
```

Even with those switches, it's the exact same problem.....

---

### Post by StuartN on 2009-05-30
The “glut.h” file should be placed in the “include\GL\” directory of your MinGW installation.

---

### Post by bgbnbigben on 2009-05-30
ok, i eventually cp -R'd my entire /usr/include/GL/ directory into the mingw include directory, compiled and then got stuck with a new error:

```
ben@file_path$ i586-mingw32msvc-c++ snowman.cpp -o snowman.exe -O3 -lglut32 -lglu32 -lopengl32
In file included from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/GL/freeglut_std.h:114,
                 from /usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/GL/glut.h:17,
                 from snowman.cpp:3:
/usr/lib/gcc/i586-mingw32msvc/4.2.1-sjlj/../../../../i586-mingw32msvc/include/GL/gl.h:89:25: error: GL/mesa_wgl.h: No such file or directory
```

funny story; this sort of crap was the exact reason i gave up windows :)
Oh well, at least im making some headway here :)

---

### Post by bgbnbigben on 2009-05-31
So after installing mesa's version of OpenGL/GLUT and fiddling around with copying stuff everywhere, stealing the glut32.dll file off my windows partition and setting up wine, it's started to work for windows :)
Thanks to those that helped!

---

