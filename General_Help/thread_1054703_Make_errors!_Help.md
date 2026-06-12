---
title: "Make errors! Help?"
date: 2009-01-29
forum: General Help
---

### Post by McTwist724 on 2009-01-29
> cman@cman:~/Desktop/transkode$ make
make  all-recursive
make[1]: Entering directory `/home/cman/Desktop/transkode'
Making all in doc
make[2]: Entering directory `/home/cman/Desktop/transkode/doc'
Making all in .
make[3]: Entering directory `/home/cman/Desktop/transkode/doc'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/cman/Desktop/transkode/doc'
Making all in en
make[3]: Entering directory `/home/cman/Desktop/transkode/doc/en'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/cman/Desktop/transkode/doc/en'
make[2]: Leaving directory `/home/cman/Desktop/transkode/doc'
Making all in po
make[2]: Entering directory `/home/cman/Desktop/transkode/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/cman/Desktop/transkode/po'
Making all in src
make[2]: Entering directory `/home/cman/Desktop/transkode/src'
Making all in common
make[3]: Entering directory `/home/cman/Desktop/transkode/src/common'
if /bin/bash ../../libtool --silent --mode=compile --tag=CXX g++ -DHAVE_CONFIG_H -I. -I. -I../..  -I/usr/include/kde -I/usr/share/qt3/include -I.  -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribute -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common  -MT commondefs.lo -MD -MP -MF ".deps/commondefs.Tpo" \
	  -c -o commondefs.lo `test -f 'commondefs.cpp' || echo './'`commondefs.cpp; \
	then mv -f ".deps/commondefs.Tpo" ".deps/commondefs.Plo"; \
	else rm -f ".deps/commondefs.Tpo"; exit 1; \
	fi
In file included from commondefs.h:28,
                 from commondefs.cpp:21:
/usr/share/qt3/include/qstring.h: In member function 'char QChar::latin1() const':
/usr/share/qt3/include/qstring.h:197: warning: conversion to 'char' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In member function 'void QChar::setCell(uchar)':
/usr/share/qt3/include/qstring.h:222: warning: conversion to 'ushort' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In member function 'void QChar::setRow(uchar)':
/usr/share/qt3/include/qstring.h:223: warning: conversion to 'ushort' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In constructor 'QChar::QChar(uchar, uchar)':
/usr/share/qt3/include/qstring.h:267: warning: conversion to 'ushort' from 'int' may alter its value
/usr/share/qt3/include/qstring.h: In constructor 'QStringData::QStringData(QChar*, uint, uint)':
/usr/share/qt3/include/qstring.h:365: warning: conversion to 'unsigned int:30' from 'uint' may alter its value
/usr/share/qt3/include/qstring.h:365: warning: conversion to 'unsigned int:30' from 'uint' may alter its value
In file included from /usr/share/qt3/include/qobject.h:48,
                 from /usr/share/qt3/include/qwidget.h:46,
                 from /usr/share/qt3/include/qdesktopwidget.h:43,
                 from /usr/share/qt3/include/qapplication.h:45,
                 from /usr/include/kde/kapplication.h:38,
                 from commondefs.cpp:34:
/usr/share/qt3/include/qevent.h: In member function 'void QDropEvent::setAction(QDropEvent::Action)':
/usr/share/qt3/include/qevent.h:523: warning: conversion to 'unsigned char' from 'uint' may alter its value
In file included from /usr/share/qt3/include/qwidget.h:52,
                 from /usr/share/qt3/include/qdesktopwidget.h:43,
                 from /usr/share/qt3/include/qapplication.h:45,
                 from /usr/include/kde/kapplication.h:38,
                 from commondefs.cpp:34:
/usr/share/qt3/include/qsizepolicy.h: In member function 'void QSizePolicy::transpose()':
/usr/share/qt3/include/qsizepolicy.h:125: warning: conversion to 'uchar' from 'uint' may alter its value
/usr/share/qt3/include/qsizepolicy.h:125: warning: conversion to 'uchar' from 'uint' may alter its value
commondefs.cpp: In static member function 'static QString String::title(const QString&)':
commondefs.cpp:151: warning: conversion to 'int' from 'size_t' may alter its value
commondefs.cpp: In static member function 'static QString String::evalTextTransformationExpression(const QString&)':
commondefs.cpp:320: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:320: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:322: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:322: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:324: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:324: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:326: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:326: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:328: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp:328: warning: conversion to 'uint' from 'long unsigned int' may alter its value
commondefs.cpp: In static member function 'static bool System::copy(const QString&, const QString&, bool, bool)':
commondefs.cpp:582: warning: conversion to 'int' from 'Q_LONG' may alter its value
commondefs.cpp:586: warning: conversion to 'int' from 'Q_LONG' may alter its value
commondefs.cpp:587: warning: conversion to 'int' from 'Q_LONG' may alter its value
commondefs.cpp: In static member function 'static QString System::user()':
commondefs.cpp:678: error: 'getenv' was not declared in this scope
make[3]: *** [commondefs.lo] Error 1
make[3]: Leaving directory `/home/cman/Desktop/transkode/src/common'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/cman/Desktop/transkode/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cman/Desktop/transkode'
make: *** [all] Error 2


I am running Ubuntu 8.10 x64 and am trying to install transKode. It said the configure was good but I keep getting these errors. Point me in the right direction this is killing me

---

### Post by halovivek on 2009-01-30
I hope the error with the program itself 
one of the similar [link]("http://blog.jelthure.com/ubuntu/ubuntu-710-gutsy-gibbon-virtualbox-164-compile-error-pass_bldprogs_before-error-2/") like that.

---

### Post by snova on 2009-01-30
All of those are warnings (and not worrisome) except for:

> **McTwist724 said:**
> ```

commondefs.cpp: In static member function 'static QString System::user()':
commondefs.cpp:678: error: 'getenv' was not declared in this scope

```

At the top of this file, add this line:

```
#include <stdlib.h>
```

And try again.

---

### Post by McTwist724 on 2009-01-31
At the top of which file? Sorry I don't understand what you what me to do exactly.

EDIT:: Wow I figured it out. It progresses a lot farther but now I get this:

> processhandler.cpp: In member function 'void ProcessHandler::terminate(long unsigned int)':
processhandler.cpp:100: warning: conversion to 'int' from 'long unsigned int' may alter its value
processhandler.cpp: In member function 'bool ProcessHandler::setPriority(int, bool)':
processhandler.cpp:149: error: '::system' has not been declared
processhandler.cpp: In member function 'bool ProcessHandler::pause()':
processhandler.cpp:169: error: '::system' has not been declared
processhandler.cpp: In member function 'bool ProcessHandler::resume()':
processhandler.cpp:184: error: '::system' has not been declared
make[4]: *** [processhandler.lo] Error 1
make[4]: Leaving directory `/home/cman/Desktop/transkode/src/plugins'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/cman/Desktop/transkode/src/plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/cman/Desktop/transkode/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/cman/Desktop/transkode'
make: *** [all] Error 2


---

### Post by snova on 2009-01-31
Same thing, just in **processhandler.cpp** now.

```
#include <stdlib.h>
```

---

### Post by McTwist724 on 2009-01-31
Thanks a bunch!

---

