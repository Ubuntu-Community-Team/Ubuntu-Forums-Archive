---
title: "compiling racer 0.50 source under hardy"
date: 2008-05-31
forum: Gaming &amp; Leisure
---

### Post by wesmo on 2008-05-31
trying to compile [http://www.sourcefiles.org/Games/Simulation/Racing/rr050src.tgz](http://www.sourcefiles.org/Games/Simulation/Racing/rr050src.tgz) under hardy.

Keep getting compile errors when running make..

Any idea what steps I should take...

---

### Post by Sockerdrickan on 2008-05-31
post output in a [code]

---

### Post by wesmo on 2008-05-31
~/Desktop/rr050src$ make

```
/usr/bin/make -C src/libs/qlib
make[1]: Entering directory `/home/wessam/Desktop/rr050src/src/libs/qlib'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qxwindow.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from qxwindow.cpp:21:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
qxwindow.cpp:31:38: error: X11/extensions/xf86vmode.h: No such file or directory
In file included from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from qxwindow.cpp:21:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from qxwindow.cpp:21:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from qxwindow.cpp:21:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from qxwindow.cpp:21:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from qxwindow.cpp:21:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from qxwindow.cpp:21:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from qxwindow.cpp:21:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from qxwindow.cpp:21:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from qxwindow.cpp:23:
../../../include/qlib/cursor.h: In member function ‘virtual char* QCursor::ClassName()’:
../../../include/qlib/cursor.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/app.h:20,
                 from qxwindow.cpp:24:
../../../include/qlib/display.h: In member function ‘virtual char* QDisplay::ClassName()’:
../../../include/qlib/display.h:18: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/shell.h:7,
                 from ../../../include/qlib/app.h:21,
                 from qxwindow.cpp:24:
../../../include/qlib/draw.h: In member function ‘virtual char* QDraw::ClassName()’:
../../../include/qlib/draw.h:16: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/app.h:21,
                 from qxwindow.cpp:24:
../../../include/qlib/shell.h: In member function ‘virtual char* QShell::ClassName()’:
../../../include/qlib/shell.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/app.h:22,
                 from qxwindow.cpp:24:
../../../include/qlib/font.h: In member function ‘virtual char* QFont::ClassName()’:
../../../include/qlib/font.h:39: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/font.h: In member function ‘virtual char* QFontList::ClassName()’:
../../../include/qlib/font.h:94: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/app.h:23,
                 from qxwindow.cpp:24:
../../../include/qlib/state.h: In member function ‘virtual char* QState::ClassName()’:
../../../include/qlib/state.h:22: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/state.h: In member function ‘virtual char* QStateManager::ClassName()’:
../../../include/qlib/state.h:53: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/control.h:6,
                 from ../../../include/qlib/gel.h:9,
                 from ../../../include/qlib/fxman.h:6,
                 from ../../../include/qlib/app.h:24,
                 from qxwindow.cpp:24:
../../../include/qlib/fx.h: In member function ‘virtual char* QFX::ClassName()’:
../../../include/qlib/fx.h:17: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/fx.h: In member function ‘virtual char* QFXList::ClassName()’:
../../../include/qlib/fx.h:42: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/control.h:7,
                 from ../../../include/qlib/gel.h:9,
                 from ../../../include/qlib/fxman.h:6,
                 from ../../../include/qlib/app.h:24,
                 from qxwindow.cpp:24:
../../../include/qlib/envelope.h: In member function ‘virtual char* QEnvelope::ClassName()’:
../../../include/qlib/envelope.h:23: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/gel.h:9,
                 from ../../../include/qlib/fxman.h:6,
                 from ../../../include/qlib/app.h:24,
                 from qxwindow.cpp:24:
../../../include/qlib/control.h: In member function ‘virtual char* QControl::ClassName()’:
../../../include/qlib/control.h:28: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/fxman.h:6,
                 from ../../../include/qlib/app.h:24,
                 from qxwindow.cpp:24:
../../../include/qlib/gel.h: In member function ‘virtual char* QBasicGel::ClassName()’:
../../../include/qlib/gel.h:37: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/gel.h: In member function ‘virtual char* QGel::ClassName()’:
../../../include/qlib/gel.h:90: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/gel.h: In member function ‘virtual char* QGelList::ClassName()’:
../../../include/qlib/gel.h:144: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/app.h:24,
                 from qxwindow.cpp:24:
../../../include/qlib/fxman.h: In member function ‘virtual char* QFXManager::ClassName()’:
../../../include/qlib/fxman.h:18: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/bc.h:9,
                 from ../../../include/qlib/app.h:26,
                 from qxwindow.cpp:24:
../../../include/qlib/group.h: In member function ‘virtual char* QGroup::ClassName()’:
../../../include/qlib/group.h:14: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/movie.h:7,
                 from ../../../include/qlib/dmmoviein.h:7,
                 from ../../../include/qlib/common/dmedia.h:9,
                 from ../../../include/qlib/alphabuf.h:7,
                 from ../../../include/qlib/bc.h:10,
                 from ../../../include/qlib/app.h:26,
                 from qxwindow.cpp:24:
../../../include/qlib/audport.h: In member function ‘virtual char* QAudioPort::ClassName()’:
../../../include/qlib/audport.h:27: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/common/dmedia.h:17,
                 from ../../../include/qlib/alphabuf.h:7,
                 from ../../../include/qlib/bc.h:10,
                 from ../../../include/qlib/app.h:26,
                 from qxwindow.cpp:24:
../../../include/qlib/vinvout.h: In member function ‘virtual char* QVinVout::ClassName()’:
../../../include/qlib/vinvout.h:16: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/bc.h:10,
                 from ../../../include/qlib/app.h:26,
                 from qxwindow.cpp:24:
../../../include/qlib/alphabuf.h: In member function ‘virtual char* QAlphaBuf::ClassName()’:
../../../include/qlib/alphabuf.h:13: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/app.h:26,
                 from qxwindow.cpp:24:
../../../include/qlib/bc.h: In member function ‘virtual char* QBC::ClassName()’:
../../../include/qlib/bc.h:23: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/info.h:17,
                 from ../../../include/qlib/video.h:15,
                 from ../../../include/qlib/app.h:27,
                 from qxwindow.cpp:24:
../../../include/qlib/file.h: In member function ‘virtual char* QFile::ClassName()’:
../../../include/qlib/file.h:12: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/video.h:15,
                 from ../../../include/qlib/app.h:27,
                 from qxwindow.cpp:24:
../../../include/qlib/info.h: In member function ‘virtual char* QInfo::ClassName()’:
../../../include/qlib/info.h:69: warning: deprecated conversion from string constant to ‘char*’
In file included from qxwindow.cpp:24:
../../../include/qlib/app.h: In member function ‘virtual char* QApp::ClassName()’:
../../../include/qlib/app.h:82: warning: deprecated conversion from string constant to ‘char*’
In file included from qxwindow.cpp:25:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
qxwindow.cpp: In function ‘bool VidModeSwitch(int, int, int)’:
qxwindow.cpp:91: error: ‘XF86VidModeModeInfo’ was not declared in this scope
qxwindow.cpp:91: error: ‘ppModeInfo’ was not declared in this scope
qxwindow.cpp:96: error: ‘mode’ was not declared in this scope
qxwindow.cpp:100: error: ‘XF86VidModeGetAllModeLines’ was not declared in this scope
qxwindow.cpp:109: error: ‘XF86VidModeSwitchToMode’ was not declared in this scope
qxwindow.cpp:112: error: ‘XF86VidModeSetViewPort’ was not declared in this scope
qxwindow.cpp: In member function ‘virtual bool QXWindow::Create()’:
qxwindow.cpp:770: warning: unused variable ‘attribListDV’
qxwindow.cpp: At global scope:
qxwindow.cpp:255: warning: ‘int WaitForNotify(Display*, XEvent*, char*)’ defined but not used
qxwindow.cpp:266: warning: ‘void ListWins()’ defined but not used
make[1]: *** [qxwindow.o] Error 1
make[1]: Leaving directory `/home/wessam/Desktop/rr050src/src/libs/qlib'
make: *** [_subdir_src/libs/qlib] Error 2

```

---

### Post by Sockerdrickan on 2008-05-31
Try this
```
sudo apt-get install xorg-dev xserver-xorg-dev
```
```
make clean && make
```

---

### Post by wesmo on 2008-05-31
new compilation errors now - all seem to be related to qlib...

```
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/opengl.h:15,
                 from qerror.cpp:11:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from qerror.cpp:11:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c getoption.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from getoption.cpp:11:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from getoption.cpp:11:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from getoption.cpp:11:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdebug.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from qdebug.cpp:29:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from qdebug.cpp:29:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
qdebug.cpp: In function ‘void QOLOF(char*, int)’:
qdebug.cpp:62: warning: deprecated conversion from string constant to ‘char*’
qdebug.cpp:64: warning: deprecated conversion from string constant to ‘char*’
qdebug.cpp:66: warning: deprecated conversion from string constant to ‘char*’
qdebug.cpp:73: warning: deprecated conversion from string constant to ‘char*’
qdebug.cpp: In function ‘const char* dbgPrefix()’:
qdebug.cpp:166: warning: deprecated conversion from string constant to ‘char*’
qdebug.cpp:181: warning: comparison between signed and unsigned integer expressions
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qprofile.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from qprofile.cpp:24:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from qprofile.cpp:24:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c cmspline.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from cmspline.cpp:12:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from cmspline.cpp:12:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qcurve.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/info.h:16,
                 from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/info.h:16,
                 from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/info.h:17,
                 from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/file.h: In member function ‘virtual char* QFile::ClassName()’:
../../../include/qlib/file.h:12: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/info.h: In member function ‘virtual char* QInfo::ClassName()’:
../../../include/qlib/info.h:69: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c string.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from string.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from string.cpp:9:
../../../include/qlib/object.h: In member function ‘virtual char* QObject::ClassName()’:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/drawable.h: In member function ‘char* QDrawable::className()’:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/color.h: In member function ‘virtual char* QColor::ClassName()’:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/bitmap.h: In member function ‘char* QBitMap::className() const’:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/image.h: In member function ‘char* QImage::className() const’:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/textstyle.h: In member function ‘virtual char* QTextStyle::ClassName()’:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/canvas.h: In member function ‘virtual char* QCanvas::ClassName()’:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/window.h: In member function ‘virtual char* QXWindow::ClassName()’:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to ‘char*’
../../../include/qlib/window.h: In member function ‘virtual char* QWindow::ClassName()’:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to ‘char*’
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/opengl.h: In member function ‘virtual char* QGLContext::ClassName()’:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to ‘char*’
ar -ar -o ../../../lib/libQ.a q3ddlg.o qfiledlg.o qdlgprog.o qdlgedit.o qdlgview.o qstrdlg.o qtextdlg.o qdialog.o qscreen.o qdisplay.o qmenu.o qbc.o qdraw.o qshell.o qgroup.o qmsg.o qlistbox.o qscrollbar.o qtitlebar.o qeditini.o qprop.o qbutton.o qlabel.o qradio.o qcheck.o qcedit.o qedit.o qprogress.o qwinmgr.o qwindow.o qxwindow.o qdrawable.o qcursor.o qstate.o qkey.o qevent.o qtext.o qmoviebob.o qbob.o qbgr.o qshape.o qgel.o qfxman.o qvideofx.o qfx.o qfxlist.o qcontrol.o qenvelope.o qcube.o qpolygon.o qfont.o qcanvas.o qtextstyle.o qblit.o qblitq.o qopengl.o qgc.o qpsd.o qimage.o qbitmap.o qfilter.o qdxjoy.o qdxeffect.o qdxinput.o qdxsbuf.o qdxsound.o qsample.o qaudport.o qvideo.o qalphabuf.o qcd.o qivs.o qvrlights.o qvrdisplays.o qsermouse.o qtouch.o qmidi.o qserial.o qinstall.o qarchive.o qfile.o qdir.o qclientsocket.o qserversocket.o qapp.o qlex.o qlanguage.o qcolor.o qezscroll.o qscroll.o qgrid.o qdoc.o qview.o qtrackball.o qcsv.o qtimer.o qbuttons.o qtime.o qmultigraph.o qinfo.o qset.o qstring.o qthread.o qsema.o qprocess.o qpsize.o qobject.o qmem.o qmisc.o qeval.o qmessage.o qpoint.o qerror.o getoption.o qdebug.o qprofile.o cmspline.o qcurve.o string.o
ar: q3ddlg.o: File format not recognized
make[1]: *** [../../../lib/libQ.a] Error 1
make[1]: Leaving directory `/home/wessam/Desktop/rr050src/src/libs/qlib'
make: *** [_subdir_src/libs/qlib] Error 2

```

---

### Post by DoktorSeven on 2008-05-31
Your errors aren't in qlib, anything that says "warning" is **not** an error.  Your last few lines are the error:

```
ar -ar -o ../../../lib/libQ.a q3ddlg.o qfiledlg.o qdlgprog.o qdlgedit.o qdlgview.o qstrdlg.o qtextdlg.o qdialog.o qscreen.o qdisplay.o qmenu.o qbc.o qdraw.o qshell.o qgroup.o qmsg.o qlistbox.o qscrollbar.o qtitlebar.o qeditini.o qprop.o qbutton.o qlabel.o qradio.o qcheck.o qcedit.o qedit.o qprogress.o qwinmgr.o qwindow.o qxwindow.o qdrawable.o qcursor.o qstate.o qkey.o qevent.o qtext.o qmoviebob.o qbob.o qbgr.o qshape.o qgel.o qfxman.o qvideofx.o qfx.o qfxlist.o qcontrol.o qenvelope.o qcube.o qpolygon.o qfont.o qcanvas.o qtextstyle.o qblit.o qblitq.o qopengl.o qgc.o qpsd.o qimage.o qbitmap.o qfilter.o qdxjoy.o qdxeffect.o qdxinput.o qdxsbuf.o qdxsound.o qsample.o qaudport.o qvideo.o qalphabuf.o qcd.o qivs.o qvrlights.o qvrdisplays.o qsermouse.o qtouch.o qmidi.o qserial.o qinstall.o qarchive.o qfile.o qdir.o qclientsocket.o qserversocket.o qapp.o qlex.o qlanguage.o qcolor.o qezscroll.o qscroll.o qgrid.o qdoc.o qview.o qtrackball.o qcsv.o qtimer.o qbuttons.o qtime.o qmultigraph.o qinfo.o qset.o qstring.o qthread.o qsema.o qprocess.o qpsize.o qobject.o qmem.o qmisc.o qeval.o qmessage.o qpoint.o qerror.o getoption.o qdebug.o qprofile.o cmspline.o qcurve.o string.o
ar: q3ddlg.o: File format not recognized
make[1]: *** [../../../lib/libQ.a] Error 1
make[1]: Leaving directory `/home/wessam/Desktop/rr050src/src/libs/qlib'
make: *** [_subdir_src/libs/qlib] Error 2
```
Kind of an odd error, as I don't think that command is doing what it should be...

Edit -- grabbed the code and I think I see the issue, it's trying to link a library with "ar", which in Linux is an archiver instead of a linker in other OSes.  I've tried changing the "makefile" in each of the library directories (src/libs/*/makefile) to use g++ (AR=g++) but have no idea what flags it expects...

---

### Post by wesmo on 2008-05-31
hmmm... thanks for looking at it... guess the code is impossible to compile then?

The original source compilation instruction can be found here [http://www.racer.nl/tech/source.htm](http://www.racer.nl/tech/source.htm)

haven't checked the source tgz from there though [http://www.racer.nl/download/v050/rr050src.tgz](http://www.racer.nl/download/v050/rr050src.tgz)

---

### Post by wesmo on 2008-06-01
The source code from the original website ([http://www.racer.nl/download/v050/rr050src.tgz](http://www.racer.nl/download/v050/rr050src.tgz)) seems to generate slightly different errors:

*correction: my bad - same compiler warnings...

```
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdebug.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from qdebug.cpp:29:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from qdebug.cpp:29:
../../../include/qlib/object.h: In member function &#8216;virtual char* QObject::ClassName()&#8217;:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/drawable.h: In member function &#8216;char* QDrawable::className()&#8217;:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/color.h: In member function &#8216;virtual char* QColor::ClassName()&#8217;:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/bitmap.h: In member function &#8216;char* QBitMap::className() const&#8217;:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/image.h: In member function &#8216;char* QImage::className() const&#8217;:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/textstyle.h: In member function &#8216;virtual char* QTextStyle::ClassName()&#8217;:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/canvas.h: In member function &#8216;virtual char* QCanvas::ClassName()&#8217;:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/window.h: In member function &#8216;virtual char* QXWindow::ClassName()&#8217;:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to &#8216;char*&#8217;
../../../include/qlib/window.h: In member function &#8216;virtual char* QWindow::ClassName()&#8217;:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qdebug.cpp:29:
../../../include/qlib/opengl.h: In member function &#8216;virtual char* QGLContext::ClassName()&#8217;:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to &#8216;char*&#8217;
qdebug.cpp: In function &#8216;void QOLOF(char*, int)&#8217;:
qdebug.cpp:62: warning: deprecated conversion from string constant to &#8216;char*&#8217;
qdebug.cpp:64: warning: deprecated conversion from string constant to &#8216;char*&#8217;
qdebug.cpp:66: warning: deprecated conversion from string constant to &#8216;char*&#8217;
qdebug.cpp:73: warning: deprecated conversion from string constant to &#8216;char*&#8217;
qdebug.cpp: In function &#8216;const char* dbgPrefix()&#8217;:
qdebug.cpp:166: warning: deprecated conversion from string constant to &#8216;char*&#8217;
qdebug.cpp:181: warning: comparison between signed and unsigned integer expressions
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qprofile.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from qprofile.cpp:24:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from qprofile.cpp:24:
../../../include/qlib/object.h: In member function &#8216;virtual char* QObject::ClassName()&#8217;:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/drawable.h: In member function &#8216;char* QDrawable::className()&#8217;:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/color.h: In member function &#8216;virtual char* QColor::ClassName()&#8217;:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/bitmap.h: In member function &#8216;char* QBitMap::className() const&#8217;:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/image.h: In member function &#8216;char* QImage::className() const&#8217;:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/textstyle.h: In member function &#8216;virtual char* QTextStyle::ClassName()&#8217;:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/canvas.h: In member function &#8216;virtual char* QCanvas::ClassName()&#8217;:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/window.h: In member function &#8216;virtual char* QXWindow::ClassName()&#8217;:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to &#8216;char*&#8217;
../../../include/qlib/window.h: In member function &#8216;virtual char* QWindow::ClassName()&#8217;:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qprofile.cpp:25:
../../../include/qlib/opengl.h: In member function &#8216;virtual char* QGLContext::ClassName()&#8217;:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to &#8216;char*&#8217;
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c cmspline.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from cmspline.cpp:12:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from cmspline.cpp:12:
../../../include/qlib/object.h: In member function &#8216;virtual char* QObject::ClassName()&#8217;:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/drawable.h: In member function &#8216;char* QDrawable::className()&#8217;:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/color.h: In member function &#8216;virtual char* QColor::ClassName()&#8217;:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/bitmap.h: In member function &#8216;char* QBitMap::className() const&#8217;:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/image.h: In member function &#8216;char* QImage::className() const&#8217;:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/textstyle.h: In member function &#8216;virtual char* QTextStyle::ClassName()&#8217;:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/canvas.h: In member function &#8216;virtual char* QCanvas::ClassName()&#8217;:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/window.h: In member function &#8216;virtual char* QXWindow::ClassName()&#8217;:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to &#8216;char*&#8217;
../../../include/qlib/window.h: In member function &#8216;virtual char* QWindow::ClassName()&#8217;:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from cmspline.cpp:12:
../../../include/qlib/opengl.h: In member function &#8216;virtual char* QGLContext::ClassName()&#8217;:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to &#8216;char*&#8217;
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qcurve.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/info.h:16,
                 from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/info.h:16,
                 from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/object.h: In member function &#8216;virtual char* QObject::ClassName()&#8217;:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/info.h:17,
                 from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/file.h: In member function &#8216;virtual char* QFile::ClassName()&#8217;:
../../../include/qlib/file.h:12: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/curve.h:7,
                 from qcurve.cpp:11:
../../../include/qlib/info.h: In member function &#8216;virtual char* QInfo::ClassName()&#8217;:
../../../include/qlib/info.h:69: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/drawable.h: In member function &#8216;char* QDrawable::className()&#8217;:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/color.h: In member function &#8216;virtual char* QColor::ClassName()&#8217;:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/bitmap.h: In member function &#8216;char* QBitMap::className() const&#8217;:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/image.h: In member function &#8216;char* QImage::className() const&#8217;:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/textstyle.h: In member function &#8216;virtual char* QTextStyle::ClassName()&#8217;:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/canvas.h: In member function &#8216;virtual char* QCanvas::ClassName()&#8217;:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/window.h: In member function &#8216;virtual char* QXWindow::ClassName()&#8217;:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to &#8216;char*&#8217;
../../../include/qlib/window.h: In member function &#8216;virtual char* QWindow::ClassName()&#8217;:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from qcurve.cpp:13:
../../../include/qlib/opengl.h: In member function &#8216;virtual char* QGLContext::ClassName()&#8217;:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to &#8216;char*&#8217;
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c string.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from string.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command-line>: warning: this is the location of the previous definition
In file included from ../../../include/qlib/timer.h:6,
                 from ../../../include/qlib/profile.h:10,
                 from ../../../include/qlib/debug.h:19,
                 from string.cpp:9:
../../../include/qlib/object.h: In member function &#8216;virtual char* QObject::ClassName()&#8217;:
../../../include/qlib/object.h:25: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/drawable.h: In member function &#8216;char* QDrawable::className()&#8217;:
../../../include/qlib/drawable.h:26: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:9,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/color.h: In member function &#8216;virtual char* QColor::ClassName()&#8217;:
../../../include/qlib/color.h:11: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/bitmap.h: In member function &#8216;char* QBitMap::className() const&#8217;:
../../../include/qlib/bitmap.h:30: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:10,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/image.h: In member function &#8216;char* QImage::className() const&#8217;:
../../../include/qlib/image.h:92: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/canvas.h:14,
                 from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/textstyle.h: In member function &#8216;virtual char* QTextStyle::ClassName()&#8217;:
../../../include/qlib/textstyle.h:17: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/window.h:12,
                 from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/canvas.h: In member function &#8216;virtual char* QCanvas::ClassName()&#8217;:
../../../include/qlib/canvas.h:41: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/opengl.h:15,
                 from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/window.h: In member function &#8216;virtual char* QXWindow::ClassName()&#8217;:
../../../include/qlib/window.h:52: warning: deprecated conversion from string constant to &#8216;char*&#8217;
../../../include/qlib/window.h: In member function &#8216;virtual char* QWindow::ClassName()&#8217;:
../../../include/qlib/window.h:161: warning: deprecated conversion from string constant to &#8216;char*&#8217;
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from string.cpp:9:
../../../include/qlib/opengl.h: In member function &#8216;virtual char* QGLContext::ClassName()&#8217;:
../../../include/qlib/opengl.h:60: warning: deprecated conversion from string constant to &#8216;char*&#8217;
ar -ar -o ../../../lib/libQ.a q3ddlg.o qfiledlg.o qdlgprog.o qdlgedit.o qdlgview.o qstrdlg.o qtextdlg.o qdialog.o qscreen.o qdisplay.o qmenu.o qbc.o qdraw.o qshell.o qgroup.o qmsg.o qlistbox.o qscrollbar.o qtitlebar.o qeditini.o qprop.o qbutton.o qlabel.o qradio.o qcheck.o qcedit.o qedit.o qprogress.o qwinmgr.o qwindow.o qxwindow.o qdrawable.o qcursor.o qstate.o qkey.o qevent.o qtext.o qmoviebob.o qbob.o qbgr.o qshape.o qgel.o qfxman.o qvideofx.o qfx.o qfxlist.o qcontrol.o qenvelope.o qcube.o qpolygon.o qfont.o qcanvas.o qtextstyle.o qblit.o qblitq.o qopengl.o qgc.o qpsd.o qimage.o qbitmap.o qfilter.o qdxjoy.o qdxeffect.o qdxinput.o qdxsbuf.o qdxsound.o qsample.o qaudport.o qvideo.o qalphabuf.o qcd.o qivs.o qvrlights.o qvrdisplays.o qsermouse.o qtouch.o qmidi.o qserial.o qinstall.o qarchive.o qfile.o qdir.o qclientsocket.o qserversocket.o qapp.o qlex.o qlanguage.o qcolor.o qezscroll.o qscroll.o qgrid.o qdoc.o qview.o qtrackball.o qcsv.o qtimer.o qbuttons.o qtime.o qmultigraph.o qinfo.o qset.o qstring.o qthread.o qsema.o qprocess.o qpsize.o qobject.o qmem.o qmisc.o qeval.o qmessage.o qpoint.o qerror.o getoption.o qdebug.o qprofile.o cmspline.o qcurve.o string.o
ar: q3ddlg.o: File format not recognized
make[1]: *** [../../../lib/libQ.a] Error 1
make[1]: Leaving directory `/home/wessam/Desktop/rr2/rr050src/src/libs/qlib'
make: *** [_subdir_src/libs/qlib] Error 2

```

---

