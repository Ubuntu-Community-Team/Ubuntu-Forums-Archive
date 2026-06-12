---
title: "QT compilation errors"
date: 2006-02-26
forum: Desktop Environments
---

### Post by BrianB on 2006-02-26
When I try to compile Qt 3.3.5 I get the error ```
C -I/usr/local/qt/mkspecs/linux-g++ -I. -I3rdparty/libpng -I3rdparty/zlib -I../include -I/usr/X11R6/include -I.moc/release-shared-mt/ -o .obj/release-shared-mt/qtaddons_x11.o kernel/qtaddons_x11.cpp
In file included from kernel/qtaddons_x11.cpp:25:
kernel/qt_x11_p.h:66:22: error: X11/Xlib.h: No such file or directory
kernel/qt_x11_p.h:71:23: error: X11/Xutil.h: No such file or directory
kernel/qt_x11_p.h:72:21: error: X11/Xos.h: No such file or directory
kernel/qt_x11_p.h:73:23: error: X11/Xatom.h: No such file or directory
make[2]: *** [.obj/release-shared-mt/qtaddons_x11.o] Error 1
make[2]: Leaving directory `/usr/local/qt/src'
make[1]: *** [sub-src] Error 2
make[1]: Leaving directory `/usr/local/qt'
make: *** [init] Error 2

``` Anybody know whats wrong?

---

### Post by oakz on 2006-02-26
try installing the xlibs-dev package

---

