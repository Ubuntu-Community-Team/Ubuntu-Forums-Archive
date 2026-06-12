---
title: "How to compile QT application &quot;Accelerate your widgets with OpenGL&quot;?"
date: 2009-01-14
forum: General Help
---

### Post by kumar.samay on 2009-01-14
Hello Friends,

I wanted to have an .obj file viewer kind of thing. While surfing over internet I found the application available at [http://labs.trolltech.com/blogs/2008/06/27/accelerate-your-widgets-with-opengl/](http://labs.trolltech.com/blogs/2008/06/27/accelerate-your-widgets-with-opengl/)

So this is the really my first time encounter with Qt + Ubuntu. I installed Qt4 over my ubuntu. Down you may find the installed packages.

*****************************************************************************************************

skumar@Home-Laptop:~$ sudo aptitude search libqt4
i A libqt4-core - Qt 4 core non-GUI functionality runtime li
i libqt4-debug - Qt 4 library debugging symbols
i libqt4-dev - Qt 4 development files
i A libqt4-gui - Qt 4 core GUI functionality runtime librar
i A libqt4-qt3support - Qt 3 compatibility library for Qt 4
p libqt4-ruby - ruby bindings for the Qt4 GUI library
p libqt4-ruby1.8 - Qt 4 bindings for Ruby
p libqt4-ruby1.8-examples - Qt 4 bindings for Ruby - example files
i A libqt4-sql - Qt 4 SQL database module

*****************************************************************************************************

I tried to compile the source code and it shows error as below. I tried to google the problem and found to set QTDIR, use tmake to generate makefilr from *.pro kind of stuff. I did so but could not succeed. I am not sure but I have feeling that it lacks include/lib directory but I really have no idea how to fix it. Kindly show the way to get solve the problem.

Waiting for the reply.

Greetings,
skumar

################################################################

skumar@Home-Laptop:~/Desktop/modelviewer$ ls
main.cpp Makefile Makefile~ model.cpp model.h models openglscene.cpp openglscene.h openglscene.pro openglscene.pro~ point3d.h point3d.h~ qt.obj

skumar@Home-Laptop:~/Desktop/modelviewer$ make
g++ -c -pipe -Wall -W -O2 -DNO_DEBUG -I. -I/usr/include/qt4 -o main.o main.cpp
In file included from openglscene.h:26,
from main.cpp:23:
point3d.h:28:21: error: qglobal.h: No such file or directory
In file included from main.cpp:23:
openglscene.h:28:26: error: QGraphicsScene: No such file or directory
openglscene.h:29:18: error: QLabel: No such file or directory
openglscene.h:30:17: error: QTime: No such file or directory
openglscene.h:33:26: error: QFutureWatcher: No such file or directory
main.cpp:25:17: error: QtGui: No such file or directory
main.cpp:26:21: error: QGLWidget: No such file or directory
In file included from openglscene.h:26,
from main.cpp:23:
point3d.h: In member function ‘float& Point3d::operator[](unsigned int)’:
point3d.h:94: error: ‘Q_ASSERT’ was not declared in this scope
point3d.h: In member function ‘const float& Point3d::operator[](unsigned int) const’:
point3d.h:99: error: ‘Q_ASSERT’ was not declared in this scope
In file included from main.cpp:23:
openglscene.h: At global scope:
openglscene.h:39: error: expected class-name before ‘{’ token
openglscene.h:40: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
openglscene.h:42: error: expected ‘;’ before ‘public’
openglscene.h:45: error: ‘QPainter’ has not been declared
openglscene.h:45: error: expected ‘,’ or ‘...’ before ‘&’ token
openglscene.h:45: error: ISO C++ forbids declaration of ‘QRectF’ with no type
openglscene.h:47: error: expected

:' before ‘slots’
openglscene.h:48: error: expected primary-expression before ‘void’
openglscene.h:48: error: ISO C++ forbids declaration of ‘slots’ with no type
openglscene.h:48: error: expected ‘;’ before ‘void’
openglscene.h:53: error: expected ‘,’ or ‘...’ before ‘&’ token
openglscene.h:53: error: ISO C++ forbids declaration of ‘QString’ with no type
openglscene.h:57: error: ‘QGraphicsSceneMouseEvent’ has not been declared
openglscene.h:58: error: ‘QGraphicsSceneMouseEvent’ has not been declared
openglscene.h:59: error: ‘QGraphicsSceneMouseEvent’ has not been declared
openglscene.h:60: error: ‘QGraphicsSceneWheelEvent’ has not been declared
openglscene.h:63: error: ISO C++ forbids declaration of ‘QDialog’ with no type
openglscene.h:63: error: expected ‘;’ before ‘*’ token
openglscene.h:70: error: ‘QColor’ does not name a type
openglscene.h:71: error: ‘QColor’ does not name a type
openglscene.h:75: error: ‘QTime’ does not name a type
openglscene.h:84: error: ISO C++ forbids declaration of ‘QLabel’ with no type
openglscene.h:84: error: expected ‘;’ before ‘*’ token
openglscene.h:85: error: ISO C++ forbids declaration of ‘QWidget’ with no type
openglscene.h:85: error: expected ‘;’ before ‘*’ token
openglscene.h:87: error: ISO C++ forbids declaration of ‘QGraphicsRectItem’ with no type
openglscene.h:87: error: expected ‘;’ before ‘*’ token
openglscene.h:90: error: ISO C++ forbids declaration of ‘QFutureWatcher’ with no type
openglscene.h:90: error: expected ‘;’ before ‘<’ token
main.cpp:29: error: expected class-name before ‘{’ token
main.cpp:37: error: ‘QResizeEvent’ has not been declared
main.cpp: In constructor ‘GraphicsView::GraphicsView()’:
main.cpp:33: error: ‘tr’ was not declared in this scope
main.cpp:33: error: ‘setWindowTitle’ was not declared in this scope
main.cpp: In member function ‘void GraphicsView::resizeEvent(int*)’:
main.cpp:38: error: ‘scene’ was not declared in this scope
main.cpp:39: error: ‘QPoint’ was not declared in this scope
main.cpp:39: error: request for member ‘size’ in ‘* event’, which is of non-class type ‘int’
main.cpp:39: error: ‘QRect’ was not declared in this scope
main.cpp:40: error: ‘QGraphicsView’ has not been declared
main.cpp: In function ‘int main(int, char**)’:
main.cpp:46: error: ‘QApplication’ was not declared in this scope
main.cpp:46: error: expected 

;' before ‘app’
main.cpp:49: error: ‘class GraphicsView’ has no member named ‘setViewport’
main.cpp:49: error: expected type-specifier before ‘QGLWidget’
main.cpp:49: error: expected `)' before ‘QGLWidget’
main.cpp:50: error: ‘class GraphicsView’ has no member named ‘setViewportUpdateMode’
main.cpp:50: error: ‘QGraphicsView’ has not been declared
main.cpp:51: error: ‘class GraphicsView’ has no member named ‘setScene’
main.cpp:52: error: ‘class GraphicsView’ has no member named ‘show’
main.cpp:54: error: ‘class GraphicsView’ has no member named ‘resize’
main.cpp:56: error: ‘app’ was not declared in this scope
main.cpp: At global scope:
main.cpp:44: warning: unused parameter ‘argc’
main.cpp:44: warning: unused parameter ‘argv’
make: *** [main.o] Error 1

################################################################

---

