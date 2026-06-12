---
title: "[SOLVED] idesk installation - unknown dependencies?"
date: 2007-11-03
forum: Desktop Environments
---

### Post by charlesreid1 on 2007-11-03
I'm installing idesk for fluxbox on Ubuntu Gutsy.  the fluxbox wiki says that idesk has the following dependencies:

```
pkg-config
librsvg-2.0.1
gdk-pixbuf2
```

So I downloaded & installed each package for my corresponding OS & architecture.  I cd into the idesk directory and run ./config and everything runs fine.  However, when I run the make command, I get this error:

```
charles@laptop:~/Software/idesk-0.7.5$ make
make: Circular aclocal.m4 <- aclocal.m4 dependency dropped.
make  all-recursive
make[1]: Entering directory `/home/charles/Software/idesk-0.7.5'
make[1]: Circular aclocal.m4 <- aclocal.m4 dependency dropped.
Making all in src
make[2]: Entering directory `/home/charles/Software/idesk-0.7.5/src'
make[2]: Circular defaults.h <- Makefile dependency dropped.
g++ -DHAVE_CONFIG_H -I. -I. -I.. -I..    -g -O2  -DSHAPE     -c XDesktopContainer.cpp
In file included from XImlib2Image.h:31,
                 from XIcon.h:30,
                 from XIconWithShadow.h:28,
                 from XDesktopContainer.cpp:26:
XImlib2ToolTip.h:29:25: error: X11/Xft/Xft.h: No such file or directory
XImlib2ToolTip.h:39: error: ISO C++ forbids declaration of ‘XftFont’ with no type
XImlib2ToolTip.h:39: error: expected ‘;’ before ‘*’ token
XImlib2ToolTip.h:52: error: ‘XGlyphInfo’ does not name a type
XImlib2ToolTip.h:53: error: ‘XftColor’ does not name a type
XImlib2ToolTip.h:54: error: ISO C++ forbids declaration of ‘XftDraw’ with no type
XImlib2ToolTip.h:54: error: expected ‘;’ before ‘*’ token
XImlib2Caption.h:42: error: ‘XGlyphInfo’ does not name a type
XImlib2Caption.h:43: error: ISO C++ forbids declaration of ‘XftDraw’ with no type
XImlib2Caption.h:43: error: expected ‘;’ before ‘*’ token
XImlib2Caption.h:45: error: ISO C++ forbids declaration of ‘XftFont’ with no type
XImlib2Caption.h:45: error: expected ‘;’ before ‘*’ token
XImlib2Caption.h:46: error: ‘XftColor’ does not name a type
XImlib2Caption.h:61: error: ISO C++ forbids declaration of ‘XftFont’ with no type
XImlib2Caption.h:61: error: expected ‘;’ before ‘*’ token
XImlib2Caption.h:62: error: ‘XftColor’ does not name a type
XDesktopContainer.cpp: In member function ‘void XDesktopContainer::initXWin()’:
XDesktopContainer.cpp:98: error: ‘XTextProperty’ was not declared in this scope
XDesktopContainer.cpp:98: error: expected `;' before ‘prop’
XDesktopContainer.cpp:101: error: ‘prop’ was not declared in this scope
XDesktopContainer.cpp:105: error: ‘XSetTextProperty’ was not declared in this scope
XDesktopContainer.cpp: In member function ‘void XDesktopContainer::parseNonIconEvents()’:
XDesktopContainer.cpp:340: error: ‘XTextProperty’ was not declared in this scope
XDesktopContainer.cpp:340: error: expected `;' before ‘prop’
XDesktopContainer.cpp:341: error: ‘prop’ was not declared in this scope
XDesktopContainer.cpp:341: error: ‘XGetTextProperty’ was not declared in this scope
XDesktopContainer.cpp:359: error: ‘XTextProperty’ was not declared in this scope
XDesktopContainer.cpp:359: error: expected `;' before ‘prop’
XDesktopContainer.cpp:360: error: ‘prop’ was not declared in this scope
XDesktopContainer.cpp:360: error: ‘XGetTextProperty’ was not declared in this scope
XDesktopContainer.cpp:371: error: ‘XSetTextProperty’ was not declared in this scope
make[2]: *** [XDesktopContainer.o] Error 1
make[2]: Leaving directory `/home/charles/Software/idesk-0.7.5/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/charles/Software/idesk-0.7.5'
make: *** [all-recursive-am] Error 2
```


I re-installed all three packages, plus I re-installed the package libxft2, since it looks like something with that package is creating the problem.  I also tried logging off and restarting, all to no avail.  Any suggestions?  Thanks.

---

### Post by mrvertigo on 2007-11-03
glad you solved the problem, mind telling us how you did it for others that encounter the problem?

---

