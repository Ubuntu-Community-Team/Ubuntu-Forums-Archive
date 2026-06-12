---
title: "Racer (racer.nl)"
date: 2005-07-14
forum: Gaming &amp; Leisure
---

### Post by RJARRRPCGP on 2005-07-14
This game looks good!!!! But, it looks like I'm gonna be in error-hell!!! Because of dependency problems, which are even worse than the DLL-hell problem of Windows!!! Thus making Linux look like a loser. 

Because nobody said how to install this under Ubuntu 5.04. ("Hoary")

I really wished that I could install it with **apt-get**!

---

### Post by RJARRRPCGP on 2005-07-14
***BUMP*** 

I'm getting fed up, because I can't install it with **apt-get** !!!  ](*,)

---

### Post by BoyOfDestiny on 2005-07-15
Spending about 10 seconds with google...

[http://www.racer.nl/tech/source.htm](http://www.racer.nl/tech/source.htm)

This has the source package and explains how to install it.

Normally, just make sure you have autoconf, automake, build-essential, and maybe checkinstall.

Any dependencies reported missing, just use synaptic to grab it.

---

### Post by RJARRRPCGP on 2005-07-15
Bad news, I gotten a shit load of errors, really dirty error messages too that basically mean that the entire thing is required to be rewritten!!! What did I do wrong?

root@ubuntu:~/Desktop/rr050src# make
/usr/bin/make -C src/libs/qlib
make[1]: Entering directory `/home/rjarrrpcgp/Desktop/rr050src/src/libs/qlib'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/l inux -Wall  -c q3ddlg.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from q3ddlg.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
In file included from ../../../include/qlib/bitmap.h:8,
                 from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/dialog.h:8,
                 from q3ddlg.cpp:9:
../../../include/qlib/drawable.h:12:20: GL/glx.h: No such file or directory
In file included from ../../../include/qlib/bitmap.h:8,
                 from ../../../include/qlib/image.h:6,
                 from ../../../include/qlib/dialog.h:8,
                 from q3ddlg.cpp:9:
../../../include/qlib/drawable.h:37: error: ISO C++ forbids declaration of `
   GLXDrawable' with no type
../../../include/qlib/drawable.h:37: error: `GLXDrawable' declared as a
   `virtual' field
../../../include/qlib/drawable.h:37: error: parse error before `(' token
../../../include/qlib/drawable.h:39: error: ISO C++ forbids declaration of `
   Drawable' with no type
../../../include/qlib/drawable.h:39: error: `Drawable' declared as a `virtual'
   field
../../../include/qlib/drawable.h:39: error: parse error before `(' token
In file included from ../../../include/qlib/dialog.h:9,
                 from q3ddlg.cpp:9:
../../../include/qlib/window.h:17:57: X11/X.h: No such file or directory
In file included from ../../../include/qlib/dialog.h:9,
                 from q3ddlg.cpp:9:
../../../include/qlib/window.h:41: error: syntax error before `;' token
../../../include/qlib/window.h:66: error: syntax error before `*' token
../../../include/qlib/window.h:69: error: 'QWindowRef' is used as a type, but
   is not defined as a type.
../../../include/qlib/window.h:90: error: parse error before `)' token
../../../include/qlib/window.h:91: error: parse error before `)' token
../../../include/qlib/window.h:96: error: syntax error before `*' token
../../../include/qlib/window.h:104: error: semicolon missing after declaration
   of `QXWindow'
../../../include/qlib/window.h:104: error: two or more data types in
   declaration of `PrefWM'
../../../include/qlib/window.h:104: error: invalid return type for function `
   QXWindow PrefWM(bool)'
../../../include/qlib/window.h:104: error:   because the following virtual
   functions are abstract:
../../../include/qlib/drawable.h:45: error:     virtual int QDrawable::GetWidth( )
../../../include/qlib/drawable.h:46: error:     virtual int QDrawable::GetHeight ()
../../../include/qlib/window.h: In function `QXWindow* GetParent()':
../../../include/qlib/window.h:123: error: `parent' undeclared (first use this
   function)
../../../include/qlib/window.h:123: error: (Each undeclared identifier is
   reported only once for each function it appears in.)
../../../include/qlib/window.h: At global scope:
../../../include/qlib/window.h:128: error: parse error before `)' token
../../../include/qlib/window.h:134: error: parse error before `)' token
../../../include/qlib/window.h:150: error: virtual outside class declaration
../../../include/qlib/window.h:153: error: parse error before `}' token
../../../include/qlib/window.h:364: error: type specifier omitted for parameter
   `Window'
../../../include/qlib/window.h:364: error: parse error before `=' token
../../../include/qlib/window.h:369: error: `Window' was not declared in this
   scope
../../../include/qlib/window.h:369: error: parse error before `,' token
../../../include/qlib/window.h:370: error: `Window' was not declared in this
   scope
../../../include/qlib/window.h:370: error: parse error before `)' token
In file included from ../../../include/qlib/font.h:6,
                 from ../../../include/qlib/edit.h:8,
                 from ../../../include/qlib/dialog.h:11,
                 from q3ddlg.cpp:9:
../../../include/qlib/app.h:15:22: X11/Xlib.h: No such file or directory
../../../include/qlib/app.h:16:23: X11/Xutil.h: No such file or directory
../../../include/qlib/app.h:17:19: X11/X.h: No such file or directory
../../../include/qlib/app.h:18:27: X11/Intrinsic.h: No such file or directory
In file included from ../../../include/qlib/bc.h:10,
                 from ../../../include/qlib/app.h:26,
                 from ../../../include/qlib/font.h:6,
                 from ../../../include/qlib/edit.h:8,
                 from ../../../include/qlib/dialog.h:11,
                 from q3ddlg.cpp:9:
../../../include/qlib/alphabuf.h:60: error: parse error before `)' token
In file included from ../../../include/qlib/font.h:6,
                 from ../../../include/qlib/edit.h:8,
                 from ../../../include/qlib/dialog.h:11,
                 from q3ddlg.cpp:9:
../../../include/qlib/app.h:117: error: parse error before `[' token
../../../include/qlib/app.h:148: error: `Window' was not declared in this scope
../../../include/qlib/app.h:148: error: parse error before `)' token
../../../include/qlib/app.h:169: error: parse error before `)' token
In file included from ../../../include/qlib/edit.h:8,
                 from ../../../include/qlib/dialog.h:11,
                 from q3ddlg.cpp:9:
../../../include/qlib/font.h:9:22: X11/Xlib.h: No such file or directory
In file included from ../../../include/qlib/edit.h:8,
                 from ../../../include/qlib/dialog.h:11,
                 from q3ddlg.cpp:9:
../../../include/qlib/font.h:75: error: parse error before `)' token
In file included from q3ddlg.cpp:9:
../../../include/qlib/dialog.h:18:57: X11/X.h: No such file or directory
In file included from q3ddlg.cpp:14:
../../../include/linux/bstring.h:9:7: warning: no newline at end of file
q3ddlg.cpp:18:22: X11/Xlib.h: No such file or directory
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from q3ddlg.cpp:20:
../../../include/qlib/opengl.h:17:55: X11/Xlib.h: No such file or directory
../../../include/qlib/opengl.h:35:19: GL/gl.h: No such file or directory
../../../include/qlib/opengl.h:36:20: GL/glu.h: No such file or directory
../../../include/qlib/opengl.h:39:20: GL/glx.h: No such file or directory
In file included from ../../../include/qlib/error.h:7,
                 from ../../../include/qlib/debug.h:21,
                 from q3ddlg.cpp:20:
../../../include/qlib/opengl.h:104: error: 'GLXContext' is used as a type, but
   is not defined as a type.
../../../include/qlib/opengl.h:118: error: type specifier omitted for parameter
   `XVisualInfo'
../../../include/qlib/opengl.h:118: error: parse error before `*' token
../../../include/qlib/opengl.h:122: error: parse error before `ctx'
../../../include/qlib/opengl.h:140: error: parse error before `)' token
In file included from ../../../include/qlib/debug.h:21,
                 from q3ddlg.cpp:20:
../../../include/qlib/error.h:48: error: parse error before `,' token
../../../include/qlib/error.h:50: error: parse error before `,' token
../../../include/qlib/error.h:52: error: parse error before `,' token
../../../include/qlib/error.h:54: error: parse error before `,' token
q3ddlg.cpp:41: warning: `int orgX' defined but not used
q3ddlg.cpp:41: warning: `int orgY' defined but not used
make[1]: *** [q3ddlg.o] Error 1
make[1]: Leaving directory `/home/rjarrrpcgp/Desktop/rr050src/src/libs/qlib'
make: *** [_subdir_src/libs/qlib] Error 2
root@ubuntu:~/Desktop/rr050src#

---

### Post by RJARRRPCGP on 2005-07-15
***BUMP*** 

I dunno what the cause is. Is it because XFree86 is required? If XFree86 is required, then it's incompatible with Hoary!!!

---

### Post by udha on 2005-07-17
[QUOTE=RJARRRPCGP]***BUMP*** 

I dunno what the cause is. Is it because XFree86 is required? If XFree86 is required, then it's incompatible with Hoary!!![/QUOTE]
 Try this command just to make sure you have the compilers etc needed to install and compile source code:

```
sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
```

---

### Post by RJARRRPCGP on 2005-07-17
[QUOTE=udha]Try this command just to make sure you have the compilers etc needed to install and compile source code:

```
sudo apt-get install cvs build-essential bison flex-old libasound2-dev x-window-system-dev libpng12-dev libjpeg62-dev libfreetype6-dev libxrender-dev libttf2 libttf-dev libsdl1.2-dev libsdl-ttf2.0-dev libsdl-net1.2-dev libsdl-gfx1.2-dev msttcorefonts libfontconfig1-dev
```[/QUOTE]

Thank you a lot, because the parse errors and syntax errors went away!!!! But I'm still getting errors and the error messages I'm getting now definitely mean that it's looking for XFree86:

rjarrrpcgp@ubuntu:~/rr050src$ make
/usr/bin/make -C src/libs/qlib
make[1]: Entering directory `/home/rjarrrpcgp/rr050src/src/libs/qlib'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c q3ddlg.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from q3ddlg.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
In file included from q3ddlg.cpp:14:
../../../include/linux/bstring.h:9:7: warning: no newline at end of file
q3ddlg.cpp:41: warning: `int orgX' defined but not used
q3ddlg.cpp:41: warning: `int orgY' defined but not used
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qfiledlg.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from qfiledlg.cpp:17:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qfiledlg.cpp:20: warning: ignoring #pragma hdrstop
qfiledlg.cpp: In member function `QFileDialog::QFileDialog(QWindow*, QRect*,
   const char*)':
qfiledlg.cpp:52: warning: unused variable `int i'
qfiledlg.cpp: In member function `void QFileDialog::ShowDir()':
qfiledlg.cpp:146: warning: unused variable `int i'
qfiledlg.cpp:146: warning: unused variable `int base'
qfiledlg.cpp: In function `bool fdEH(QEvent*)':
qfiledlg.cpp:167: warning: unused variable `int i'
qfiledlg.cpp: In function `bool QDlgFile(const char*, QInfo*, const char*,
   char*, char*, char*)':
qfiledlg.cpp:324: warning: unused variable `char odir[1024]'
qfiledlg.cpp:324: warning: unused variable `char ofile[1024]'
qfiledlg.cpp:324: warning: unused variable `char ofilter[1024]'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdlgprog.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from qdlgprog.cpp:8:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qdlgprog.cpp:12: warning: ignoring #pragma hdrstop
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdlgedit.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from qdlgedit.cpp:8:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qdlgedit.cpp: In function `bool QDlgEditFile(const char*, int, const char*,
   int)':
qdlgedit.cpp:45: warning: comparison between signed and unsigned integer
   expressions
qdlgedit.cpp:51: warning: label `retry' defined but not used
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdlgview.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from qdlgview.cpp:8:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qdlgview.cpp: In function `bool QDlgViewFile(const char*, int, const char*,
   const char*, QRect*)':
qdlgview.cpp:37: warning: comparison between signed and unsigned integer
   expressions
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qstrdlg.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from qstrdlg.cpp:15:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
In file included from qstrdlg.cpp:21:
../../../include/linux/bstring.h:9:7: warning: no newline at end of file
qstrdlg.cpp: In function `bool fdEH(QEvent*)':
qstrdlg.cpp:100: warning: label `do_ok' defined but not used
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qtextdlg.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from qtextdlg.cpp:13:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
In file included from qtextdlg.cpp:19:
../../../include/linux/bstring.h:9:7: warning: no newline at end of file
qtextdlg.cpp: In member function `QTextDialog::QTextDialog(QWindow*, QRect*,
   const char*, const char*, int)':
qtextdlg.cpp:52: warning: unused variable `int i'
qtextdlg.cpp: In function `bool fdEH(QEvent*)':
qtextdlg.cpp:103: warning: unused variable `int i'
qtextdlg.cpp:103: warning: unused variable `int n'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdialog.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/dialog.h:6,
                 from qdialog.cpp:17:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
In file included from qdialog.cpp:21:
../../../include/linux/bstring.h:9:7: warning: no newline at end of file
qdialog.cpp: In member function `virtual bool QDialog::EvButtonRelease(int,
   int, int)':
qdialog.cpp:168: warning: unused variable `int nx'
qdialog.cpp:168: warning: unused variable `int ny'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qscreen.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/display.h:7,
                 from qscreen.cpp:8:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdisplay.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/display.h:7,
                 from qdisplay.cpp:11:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qmenu.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/button.h:6,
                 from ../../../include/qlib/menu.h:6,
                 from qmenu.cpp:11:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qbc.cpp
In file included from ../../../include/qlib/app.h:6,
                 from qbc.cpp:20:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qbc.cpp: In function `void ConvertToFullSize(QBC*, int)':
qbc.cpp:277: warning: unused variable `QGLContext*gl'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qdraw.cpp
In file included from ../../../include/qlib/app.h:6,
                 from qdraw.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qshell.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/shell.h:6,
                 from qshell.cpp:12:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qgroup.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/group.h:6,
                 from qgroup.cpp:8:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qgroup.cpp: In member function `virtual void QGroup::Paint(QRect*)':
qgroup.cpp:37: warning: unused variable `int sw'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qmsg.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/msg.h:6,
                 from qmsg.cpp:10:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qmsg.cpp: In member function `virtual void QMsg::Paint(QRect*)':
qmsg.cpp:92: warning: unused variable `QCanvas*cvs'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qlistbox.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/button.h:6,
                 from ../../../include/qlib/scrollbar.h:6,
                 from ../../../include/qlib/listbox.h:6,
                 from qlistbox.cpp:11:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qlistbox.cpp:19: warning: ignoring #pragma hdrstop
qlistbox.cpp: In member function `QListBox::QListBox(QWindow*, QRect*, int)':
qlistbox.cpp:53: warning: unused variable `int bHgt'
qlistbox.cpp: In member function `void QListBox::GetItemRect(int, QRect*)':
qlistbox.cpp:110: warning: unused variable `int w'
qlistbox.cpp:110: warning: unused variable `int h'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qscrollbar.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/button.h:6,
                 from ../../../include/qlib/scrollbar.h:6,
                 from qscrollbar.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qscrollbar.cpp:14: warning: ignoring #pragma hdrstop
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qtitlebar.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/button.h:6,
                 from ../../../include/qlib/titlebar.h:6,
                 from qtitlebar.cpp:8:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qtitlebar.cpp:13: warning: ignoring #pragma hdrstop
qtitlebar.cpp: In member function `QTitleBar::QTitleBar(QWindow*, const char*,
   QFont*)':
qtitlebar.cpp:43: warning: unused variable `int bWid'
qtitlebar.cpp:43: warning: unused variable `int bHgt'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qeditini.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/label.h:6,
                 from ../../../include/qlib/editini.h:6,
                 from qeditini.cpp:7:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qprop.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/prop.h:6,
                 from qprop.cpp:12:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qbutton.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/button.h:6,
                 from qbutton.cpp:18:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qlabel.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/label.h:6,
                 from qlabel.cpp:11:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qradio.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/radio.h:6,
                 from qradio.cpp:7:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qradio.cpp: In member function `virtual void QRadio::Paint(QRect*)':
qradio.cpp:78: warning: unused variable `int sw'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qcheck.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/check.h:6,
                 from qcheck.cpp:7:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qcheck.cpp: In member function `virtual void QCheck::Paint(QRect*)':
qcheck.cpp:80: warning: unused variable `int sw'
qcheck.cpp:123: warning: label `skip_text' defined but not used
qcheck.cpp:109: warning: label `skip_shadow2' defined but not used
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qcedit.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/edit.h:6,
                 from ../../../include/qlib/cedit.h:6,
                 from qcedit.cpp:9:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qcedit.cpp: In member function `void QCEdit::MacroHeader(const char*)':
qcedit.cpp:309: warning: unused variable `char*ptr'
qcedit.cpp: In function `bool IsWordChar(char)':
qcedit.cpp:330: warning: comparison is always false due to limited range of
   data type
qcedit.cpp: In member function `virtual bool QCEdit::EvKeyPress(int, int, int)
   ':
qcedit.cpp:482: warning: unused variable `bool fExpandExpr'
qcedit.cpp:406: warning: unused variable `bool refresh'
qcedit.cpp:407: warning: unused variable `char c'
qcedit.cpp:408: warning: unused variable `int len'
qcedit.cpp: In member function `virtual bool QCEdit::EvButtonPress(int, int,
   int)':
qcedit.cpp:694: warning: unused variable `char*sOpts[2]'
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qedit.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/edit.h:6,
                 from qedit.cpp:19:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qedit.cpp:30: warning: ignoring #pragma hdrstop
qedit.cpp: In function `const char* ExtractToPreviousLine(const char*, const
   char*)':
qedit.cpp:189: warning: unused variable `int i'
qedit.cpp: In function `void PaintCursor(QCanvas*, QRect*, char*, int, int,
   QFont*)':
qedit.cpp:242: warning: unused variable `int i'
qedit.cpp:243: warning: unused variable `char c'
qedit.cpp: In member function `const char* QEdit::PaintLine(int)':
qedit.cpp:376: warning: unused variable `char*d'
qedit.cpp:377: warning: unused variable `int i'
qedit.cpp: In member function `virtual void QEdit::Paint(QRect*)':
qedit.cpp:460: warning: unused variable `int sw'
qedit.cpp: In member function `bool QEdit::CursorUp()':
qedit.cpp:945: warning: unused variable `char*s'
qedit.cpp: In member function `bool QEdit::CursorRight()':
qedit.cpp:972: warning: comparison between signed and unsigned integer
   expressions
qedit.cpp: In member function `bool QEdit::InsertChar(char)':
qedit.cpp:1100: warning: comparison between signed and unsigned integer
   expressions
qedit.cpp:1091: warning: unused variable `int i'
qedit.cpp: In member function `virtual bool QEdit::EvKeyPress(int, int, int)':
qedit.cpp:1239: warning: unused variable `int len'
qedit.cpp:1524: warning: label `skip_keys' defined but not used
qedit.cpp:1303: warning: label `leaveit' defined but not used
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qprogress.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from ../../../include/qlib/progress.h:6,
                 from qprogress.cpp:7:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qprogress.cpp: In member function `virtual void QProgress::Paint(QRect*)':
qprogress.cpp:174: warning: label `skip_text' defined but not used
qprogress.cpp:133: warning: label `do_text' defined but not used
qprogress.cpp:145: warning: `int a' might be used uninitialized in this
   function
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qwinmgr.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from qwinmgr.cpp:14:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qwinmgr.cpp: In member function `bool QWindowManager::ProcessEvent(QEvent*)':
qwinmgr.cpp:137: warning: unused variable `int skip'
qwinmgr.cpp: In member function `QWindow* QWindowManager::WhichWindowAt(int,
   int, int, long unsigned int)':
qwinmgr.cpp:712: warning: unused variable `QWindow*w'
qwinmgr.cpp: In member function `QWindow* QWindowManager::FindXWindow(long
   unsigned int)':
qwinmgr.cpp:837: warning: unused variable `QWindow*xw'
qwinmgr.cpp: In member function `QWindow* QWindowManager::FindOSWindow(long
   unsigned int, int, int)':
qwinmgr.cpp:751: warning: `int bestArea' might be used uninitialized in this
   function
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qwindow.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from qwindow.cpp:19:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
g++ -O2 -Wno-deprecated -DQ_USE_FMOD -O3 -I../../../include -I../../../include/linux -Wall  -c qxwindow.cpp
In file included from ../../../include/qlib/object.h:6,
                 from ../../../include/qlib/drawable.h:10,
                 from ../../../include/qlib/window.h:8,
                 from qxwindow.cpp:21:
../../../include/qlib/os.h:17:1: warning: "Q_USE_FMOD" redefined
<command line>:5:1: warning: this is the location of the previous definition
qxwindow.cpp:31:38: X11/extensions/xf86vmode.h: No such file or directory
qxwindow.cpp: In function `bool VidModeSwitch(int, int, int)':
qxwindow.cpp:91: error: `XF86VidModeModeInfo' undeclared (first use this
   function)
qxwindow.cpp:91: error: (Each undeclared identifier is reported only once for
   each function it appears in.)
qxwindow.cpp:91: error: `ppModeInfo' undeclared (first use this function)
qxwindow.cpp:96: error: `mode' undeclared (first use this function)
qxwindow.cpp:100: error: `XF86VidModeGetAllModeLines' undeclared (first use
   this function)
qxwindow.cpp:109: error: `XF86VidModeSwitchToMode' undeclared (first use this
   function)
qxwindow.cpp:112: error: `XF86VidModeSetViewPort' undeclared (first use this
   function)
qxwindow.cpp: In member function `virtual bool QXWindow::Create()':
qxwindow.cpp:770: warning: unused variable `int attribListDV[3]'
make[1]: *** [qxwindow.o] Error 1
make[1]: Leaving directory `/home/rjarrrpcgp/rr050src/src/libs/qlib'
make: *** [_subdir_src/libs/qlib] Error 2
rjarrrpcgp@ubuntu:~/rr050src$


Is there any workaround?

---

### Post by mcduck on 2005-07-18
Well, I just installed latest Racer beta with loki installer (link from racer web site), and it works ok. Have you tried the easy way?

---

### Post by RJARRRPCGP on 2005-07-18
[QUOTE=mcduck]Well, I just installed latest Racer beta with loki installer (link from racer web site), and it works ok. Have you tried the easy way?[/QUOTE]

Where is it? I can't find it.

---

### Post by buellman on 2005-07-18
[QUOTE=RJARRRPCGP]Where is it? I can't find it.[/QUOTE]

[http://www.liflg.org/?catid=6&gameid=13](http://www.liflg.org/?catid=6&gameid=13)

hth. buellman

---

### Post by RJARRRPCGP on 2005-07-18
[QUOTE=buellman][http://www.liflg.org/?catid=6&gameid=13](http://www.liflg.org/?catid=6&gameid=13)

hth. buellman[/QUOTE]

How would I run it? Because I'm not familiar with the file format. :|

---

### Post by Caboto on 2005-07-18
[QUOTE=RJARRRPCGP]How would I run it? Because I'm not familiar with the file format. :|[/QUOTE]
Just make it executable with chmod +x racer_0.5.0-englisch.run and then run the installer with ./racer_0.5.0-englisch.run.

---

### Post by RJARRRPCGP on 2005-07-18
It installed, but now this error message:

./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory


How can I fix that? Because I just ran Synaptic Package Manager and installed a libstdc++ package, but still the same error message.

---

### Post by mcduck on 2005-07-19
I have propably installed that with some other software then, as I didn't have any problems with Racer. Try to find those files from your machine and copy them to racer directory. That might help.

---

### Post by RJARRRPCGP on 2005-07-19
[QUOTE=mcduck]I have propably installed that with some other software then, as I didn't have any problems with Racer. Try to find those files from your machine and copy them to racer directory. That might help.[/QUOTE]

I don't know how to do that, because I'm a newbie from Windows. 

I also can't find the file that it seems to be looking for. :mad:

---

### Post by duffman25 on 2005-07-20
[QUOTE=RJARRRPCGP]I don't know how to do that, because I'm a newbie from Windows. 

I also can't find the file that it seems to be looking for. :mad:[/QUOTE]

Hi

I had the same problem. Installing libstdc++2.10-glibc2.2 made it work, BUT when the game loads, I only see a dark screen. This is as far as I've got.

---

### Post by RJARRRPCGP on 2005-07-20
[QUOTE=duffman25]Hi

I had the same problem. Installing libstdc++2.10-glibc2.2 made it work, BUT when the game loads, I only see a dark screen. This is as far as I've got.[/QUOTE]

Can that be fixed? If not, then I'm forced to get another Linux distro, or else, back to Windows!!!  :mad:

---

### Post by graabein on 2005-07-22
Why is this? Are you some kind of driving teacher/instructor?  ;-)

---

### Post by RJARRRPCGP on 2005-07-22
[QUOTE=graabein]Why is this? Are you some kind of driving teacher/instructor?  ;-)[/QUOTE]

LOL. No, but I have never been able to get this game running and did shit just hit the fan now, because of not using XFree86? 

Looks like that the fact of using Xorg instead of XFree86 possibly came back to bite.  :mad:

---

### Post by mcduck on 2005-07-22
Which version did you try? I'n now playing the latest beta under Hoary (with xorg), so not using xfree86 can't be the problem..

And duffman25, start racer from terminal. Does it give any errors? Are you using hardware 3D and do other 3D-games work? Try to sudo racer.

---

### Post by RJARRRPCGP on 2005-07-22
I have a strange problem. No error messages now and it starts, but it's unplayable, because when I want to load a game, it repeatedly bounces me back to the menus!!!

I can only get to as far as the menus!!! WTF!!!  :mad:

---

### Post by RJARRRPCGP on 2005-07-26
***BUMP*** :mad:

---

### Post by charlieg on 2005-07-27
Any output to the console when run from a terminal?

---

### Post by RJARRRPCGP on 2005-07-27
Yes, with the following:

rjarrrpcgp@ubuntu:~$ racer
--- session separator ---
** [racer/8224] Can't open log file (QLOG)
  local host: 'ubuntu'/127.0.0.1
** [racer/8224] Can't open log file (QLOG)
RTime:Reset()
RChair:Enable()
Chair control to localhost:25010
** [racer/8224] Can't open log file (QLOG)
RAudio ctor
RAudio:Load(); enable=1
FMOD initializing
RAudio:GetSample(data/audio/heli_inside.wav)
Setting sample loop
FMOD Playing channel: 0
RMenuDestroy()
RMenu Destroy(); count=8
RAudio dtor
  producers=0, samples=0
QApp::Destroy()
QFont dtor
QFont dtor
QApp::Destroy()
rjarrrpcgp@ubuntu:~$

---

### Post by RJARRRPCGP on 2005-07-28
[COLOR=Red]***BUMP*** It's been 48 hours.  :mad:[/COLOR]

---

### Post by RJARRRPCGP on 2005-07-31
[COLOR=Red]***BUMP*** It's been 48 hours.  :mad:[/COLOR]

---

### Post by nookadum on 2005-07-31
[QUOTE=RJARRRPCGP][COLOR=Red]***BUMP*** It's been 48 hours.  :mad:[/COLOR][/QUOTE]
 Hmm.. it should work out of the box for you though.. I'll check around...

My only problem with Racer is the fact I can't bind my SHIFT, CTRL, and ALT keys on my keyboard. I know the game was meant for a wheel use, but I can't keep using my Logitech wheel (my brother uses it for the PS2)... :( Anyone know how I can bind those keys?

---

### Post by RJARRRPCGP on 2005-07-31
I can't play it, because it won't load any levels!!!  :mad:  Is there anything I did wrong?

---

### Post by RJARRRPCGP on 2005-10-26
Has anybody been able to play this game? Also, the problem may be caused by a bug with apt-get. The video card drivers may not be getting installed properly. :mad: 

I have that feeling that the video card drivers may not be getting installed properly, even when using Nvidia.

---

### Post by tnq13 on 2005-11-04
i'm trying to run racer, but i'm not being happy :s

at first, it said that i need the fmod api, i get it, bu i think i didn't installed it right, i just copied the one lib to /usr/lib, is it right?

after coping the lib, i just tried  to run, but now it just says:
 
```
$ ./bin/racer
./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: 
cannot open shared object file: No such file or directory
```

but i cannot find this libs at my pc...

---

### Post by RoByLy on 2005-12-06
if it's any use to anybody now try installing libstdc++2.10-glibc2.2 worked for me with the loky installer

---

### Post by thomasleveil on 2006-02-25
I had errors as well, and I couldn't start the game at all.
But after editing the racer.ini file, it was loading. Try that:
```
sudo gedit /usr/local/games/racer/racer.ini
```
Find the '**audio**' section and set 
```
enable=0
```
Of course, you won't have sound. But in my case, I have sound problem with other software as well. (One day I will find some time to ask _politely_:rolleyes:  on the forum )

---

### Post by RJARRRPCGP on 2006-07-08
Nooooooo! I must have audio! :(

---

### Post by RJARRRPCGP on 2006-07-13
It's fine with the latest version of Racer at the time of this post with a Loki installer and Breezy Badger. Just was required to install two more more packages, a couple of dependencies. 


Racer ran and ran properly for the first time!  Horray!!!! :cool: 

Unlike with Hoary, there don't seem to be problems with the loopback IP address.

What a major relief, because after I installed the first dependency it was looking for with Synaptic, I saw it just terminate on me without an error message on the screen. Then after I typed ./racer again, it was just giving me the no such file or directory error message again for a library, thus I was able to resolve it with Synaptic.

The problem looked more serious then it was when it got terminated after clicking on the Loki installer run button. :(

---

