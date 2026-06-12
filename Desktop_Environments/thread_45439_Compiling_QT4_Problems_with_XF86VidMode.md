---
title: "Compiling QT4: Problems with XF86VidMode"
date: 2005-06-30
forum: Desktop Environments
---

### Post by kamstrup on 2005-06-30
*[COPIED FROM Ubuntu Forums > Other Ubuntu Support  > Programming Talk ]*

Surfing the wave, I went straight for compiling QT4 this morning, but ran into some troubles after a lengthy compilation.

My compilation exits with the following error:
```
...
g++ -Wl,-rpath,/usr/lib -Wl,-rpath,/usr/lib -o grabber .obj/debug-shared/glwidget.o .obj/debug-shared/main.o .obj/debug-shared/mainwindow.o .obj/debug-shared/moc_glwidget.o .obj/debug-shared/moc_mainwindow.o   -L/media/space/programs/qt-x11-opensource-desktop-4.0.0/lib -L/usr/X11R6/lib -L/media/space/programs/qt-x11-opensource-desktop-4.0.0/lib -L/usr/X11R6/lib -lQtOpenGL_debug -lQtGui_debug -lpng -lSM -lICE -lXi -lXrender -lXrandr -lfreetype -lfontconfig -lXext -lX11 -lm -lQtCore_debug -lz -ldl -lGLU -lGL -lpthread
/media/space/programs/qt-x11-opensource-desktop-4.0.0/lib/libQtOpenGL_debug.so: undefined reference to `XF86VidModeQueryVersion'
/media/space/programs/qt-x11-opensource-desktop-4.0.0/lib/libQtOpenGL_debug.so: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
```

I *do* have the libxxf86vm1and corresponding -dev package installed and have the file  /usr/X11R6/include/X11/extensions/xf86vmode.h, so what gives ..?

Other apps/libs requiring XF86VidMode stuff has been compilng nicely otherwise. Any clues?

Cheers!

---

