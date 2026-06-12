---
title: "The problems in installing qtiplot-0.9.8.9"
date: 2013-01-31
forum: Education &amp; Science
---

### Post by googlezzz on 2013-01-31
In installing qtiplot-0.9.8.9, I refer to the previous thread of the forum: [http://ubuntuforums.org/showthread.php?t=1521703](http://ubuntuforums.org/showthread.php?t=1521703)

The versions are diffrent, I can't get around "qwtplot3d".
the error messages are listed below:

make[1]: Entering directory `/home/graphene/Downloads/qtiplot-0.9.8.9/3rdparty/qwtplot3d'
g++ -c -pipe -m64 -O2 -fPIC -D_REENTRANT -Wall -W -DGL2PS_HAVE_LIBPNG -DQT_NO_DEBUG -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/local/Trolltech/Qt-4.8.4/mkspecs/qws/linux-x86_64-g++ -I. -I/usr/local/Trolltech/Qt-4.8.4/include/QtCore -I/usr/local/Trolltech/Qt-4.8.4/include/QtNetwork -I/usr/local/Trolltech/Qt-4.8.4/include/QtGui -I/usr/local/Trolltech/Qt-4.8.4/include/QtOpenGL -I/usr/local/Trolltech/Qt-4.8.4/include -Iinclude -I../zlib -I../libpng/ -Ilib/tmp -o lib/tmp/qwt3d_extglwidget.o src/qwt3d_extglwidget.cpp
In file included from include/qwt3d_types.h:26:0,
                 from include/qwt3d_extglwidget.h:4,
                 from src/qwt3d_extglwidget.cpp:7:
include/qwt3d_openglhelper.h: In function ‘const GLubyte* Qwt3D::gl_error()’:
include/qwt3d_openglhelper.h:67:31: error: ‘gluErrorString’ was not declared in this scope
In file included from include/qwt3d_types.h:26:0,
                 from include/qwt3d_extglwidget.h:4,
                 from src/qwt3d_extglwidget.cpp:7:
include/qwt3d_openglhelper.h: In function ‘bool Qwt3D::ViewPort2World(double&, double&, double&, double, double, double)’:
include/qwt3d_openglhelper.h:104:97: error: ‘gluUnProject’ was not declared in this scope
include/qwt3d_openglhelper.h: In function ‘bool Qwt3D::World2ViewPort(double&, double&, double&, double, double, double)’:
include/qwt3d_openglhelper.h:120:95: error: ‘gluProject’ was not declared in this scope
make[1]: *** [lib/tmp/qwt3d_extglwidget.o] Error 1
make[1]: Leaving directory `/home/graphene/Downloads/qtiplot-0.9.8.9/3rdparty/qwtplot3d'
make: *** [sub-3rdparty-qwtplot3d-make_default] Error 2

please help!!! thank you!!!

---

### Post by googlezzz on 2013-01-31
The above problems are resolved.
The new problem is the following:

rc/analysis/Fit.cpp: In member function ‘gsl_multimin_fminimizer* Fit::fitSimplex(gsl_multimin_function, int&, int&)’:
src/analysis/Fit.cpp:166:42: error: ‘gsl_multimin_fminimizer_nmsimplex2’ was not declared in this scope
make[1]: *** [../tmp/qtiplot/Fit.o] Error 1
make[1]: Leaving directory `/home/graphene/Downloads/qtiplot-0.9.8.9/qtiplot'
make: *** [sub-qtiplot-make_default] Error 2

---

