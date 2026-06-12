---
title: "Flash 4 Linux"
date: 2009-01-22
forum: General Help
---

### Post by matmatmat on 2009-01-22
I have tried to install f4l-0.2.1:
```

qmake -project
qmake -o Makefile f4l.pro
make

```
The make comes out with this:
```

Makefile:1038: warning: overriding commands for target `main.o'
Makefile:939: warning: ignoring old commands for target `main.o'
Makefile:2540: warning: overriding commands for target `functions.o'
Makefile:1029: warning: ignoring old commands for target `functions.o'
Makefile:2549: warning: overriding commands for target `main.o'
Makefile:1038: warning: ignoring old commands for target `main.o'
g++ -c -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++ -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -Isrc -Isrc/flagStonePort/transform-cxx-bsd/examples -Isrc/flagStonePort/transform-cxx-bsd/transform -Isrc/flagStonePort/transform-util-cxx/examples -Isrc/flagStonePort/transform-util-cxx/transform-util -Isrc/flagStonePort/translate-as1/examples -Isrc/flagStonePort/translate-as1/translate-asl -I. -I. -o canvasItem.o src/canvasItem.cpp
In file included from src/canvasItem.cpp:18:
src/canvasItem.h:21:21: error: qcanvas.h: No such file or directory
src/canvasItem.h:22:25: error: qpointarray.h: No such file or directory
src/canvasItem.cpp:65:8: warning: "/*" within comment
In file included from src/canvasItem.cpp:18:
src/canvasItem.h:29: error: expected class-name before ‘{’ token
src/canvasItem.h:32: error: expected `)' before ‘*’ token
src/canvasItem.h:39: error: expected class-name before ‘{’ token
src/canvasItem.h:42: error: ‘QPointArray’ has not been declared
src/canvasItem.h:43: error: expected `)' before ‘*’ token
src/canvasItem.h:44: error: ISO C++ forbids declaration of ‘QPtrList’ with no type
src/canvasItem.h:44: error: expected ‘;’ before ‘<’ token
src/canvasItem.h:45: error: ‘QPointArray’ does not name a type
src/canvasItem.h:51: error: ‘QPointArray’ does not name a type
src/canvasItem.h:55: error: ‘QPainter’ has not been declared
src/canvasItem.h:56: error: ‘QPointArray’ does not name a type
src/canvasItem.h:42: error: ‘TRUE’ was not declared in this scope
src/canvasItem.h:62: error: expected class-name before ‘{’ token
src/canvasItem.h:64: error: expected ‘,’ or ‘...’ before ‘&’ token
src/canvasItem.h:64: error: ISO C++ forbids declaration of ‘QRect’ with no type
src/canvasItem.h: In constructor ‘CSceneRect::CSceneRect(int)’:
src/canvasItem.h:64: error: class ‘CSceneRect’ does not have any field named ‘QCanvasRectangle’
src/canvasItem.h:64: error: ‘r’ was not declared in this scope
src/canvasItem.h:64: error: ‘canvas’ was not declared in this scope
src/canvasItem.h: At global scope:
src/canvasItem.h:64: warning: unused parameter ‘QRect’
src/canvasItem.h:74: error: expected class-name before ‘{’ token
src/canvasItem.h:76: error: expected ‘,’ or ‘...’ before ‘&’ token
src/canvasItem.h:76: error: ISO C++ forbids declaration of ‘QRect’ with no type
src/canvasItem.h: In constructor ‘CtmpRect::CtmpRect(int)’:
src/canvasItem.h:76: error: class ‘CtmpRect’ does not have any field named ‘QCanvasRectangle’
src/canvasItem.h:76: error: ‘r’ was not declared in this scope
src/canvasItem.h:76: error: ‘canvas’ was not declared in this scope
src/canvasItem.h: At global scope:
src/canvasItem.h:76: warning: unused parameter ‘QRect’
src/canvasItem.cpp:21: error: expected `)' before ‘*’ token
src/canvasItem.cpp:27: error: expected `)' before ‘*’ token
src/canvasItem.cpp:37: error: prototype for ‘void CPenTool::drawShape(QPainter&)’ does not match any in class ‘CPenTool’
src/canvasItem.h:55: error: candidate is: void CPenTool::drawShape(int&)
src/canvasItem.cpp:78: error: ‘QPointArray’ does not name a type
src/canvasItem.cpp:83: error: variable or field ‘setControlPoints’ declared void
src/canvasItem.cpp:83: error: ‘QPointArray’ was not declared in this scope
src/canvasItem.cpp:83: error: expected primary-expression before ‘bool’
make: *** [canvasItem.o] Error 1


```
What's wrong?

---

### Post by gjoellee on 2009-01-22
why don'y you try this instead: 
```
sudo apt-get install cvs
```
```
cvs -z9 -d:pserver:anonymous@f4l.cvs.sf.net:/cvsroot/f4l co f4l-0.2

```
```
cd f4l-0.2 
```
```
make
```

---

### Post by matmatmat on 2009-01-22
Then I get this error:
```

make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.

```
Does that mean use qmake?

---

### Post by gjoellee on 2009-01-22
> **matmatmat said:**
> Then I get this error:
```

make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.

```Does that mean use qmake?

I am not sure about how to solve this, but see if you have qmake installed:
```
sudo apt-get install qmake
```

you might want to check this website: [http://f4l.sourceforge.net/](http://f4l.sourceforge.net/)

---

### Post by matmatmat on 2009-01-22
The website doesn't help.

---

### Post by matmatmat on 2009-01-22
bump

---

### Post by theOtherMarino on 2009-01-22
If you get this error:
Code:

make: *** No rule to make target `/usr/share/qt3/mkspecs/default/qmake.conf', needed by `Makefile'. Stop.

That means that you have to install qt3. qt4 will just not work.

Be also aware of the following: there's a patch to apply. Read this page to know why and what : [http://aur.archlinux.org/packages.php?ID=5805](http://aur.archlinux.org/packages.php?ID=5805)

And oh, BTW and for my part, it does not work even with the patch. Any advice welcome.

---

### Post by theOtherMarino on 2009-01-22
Wow.... It works with the patch. You also need libqt3-mt-dev and qt3-dev-tools along with qt3.

When its done, you will find the f4l command in the bin directory:

arino@marino-desktop:~/apps/f4l-0.2.1$ cd bin
marino@marino-desktop:~/apps/f4l-0.2.1/bin$ ./f4l

But do not chant any "alleluyah". On the page [http://f4l.sourceforge.net/?q=node/23](http://f4l.sourceforge.net/?q=node/23), it's written "After that I could not find enough time to finish the work for F4L."

Well, well... Sounded promising, but does not seems usable as is.

Regards,

Marino Ceccotti
[http://markup.fr/](http://markup.fr/)

---

### Post by matmatmat on 2009-01-24
Now I get this:
```

cd src/flagStonePort/transform-cxx-bsd/transform && make -f Makefile
make[1]: Entering directory `/home/matio/Desktop/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
g++ -c -pipe -g -w -O0 -D_REENTRANT  -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -DQT_NO_DEBUG -I/usr/share/qt3/mkspecs/default -I. -I. -I/usr/include/qt3 -o FSButtonEvent.o FSButtonEvent.cpp
In file included from FSButtonEvent.h:34,
                 from FSButtonEvent.cpp:22:
FSVector.h:35:17: error: new.h: No such file or directory
FSVector.h: In constructor ‘transform::FSVector<T>::FSVector(int) [with T = transform::FSActionObject*]’:
FSButtonEvent.h:152:   instantiated from here
FSVector.h:174: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]’:
FSButtonEvent.h:196:   instantiated from here
FSVector.h:275: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In constructor ‘transform::FSVector<T>::FSVector(int) [with T = transform::FSShapeObject*]’:
FSShape.h:75:   instantiated from here
FSVector.h:174: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]’:
FSShape.h:97:   instantiated from here
FSVector.h:275: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSShapeObject*]’:
FSShape.h:115:   instantiated from here
FSVector.h:204: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘const transform::FSVector<T>& transform::FSVector<T>::operator=(const transform::FSVector<T>&) [with T = transform::FSActionObject*]’:
FSButtonEvent.cpp:104:   instantiated from here
FSVector.h:204: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::reserve(int) [with T = transform::FSActionObject*]’:
FSVector.h:271:   instantiated from ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSActionObject*]’
FSButtonEvent.h:196:   instantiated from here
FSVector.h:246: error: no matching function for call to ‘operator new(unsigned int, transform::FSActionObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
FSVector.h: In member function ‘void transform::FSVector<T>::reserve(int) [with T = transform::FSShapeObject*]’:
FSVector.h:271:   instantiated from ‘void transform::FSVector<T>::push_back(const T&) [with T = transform::FSShapeObject*]’
FSShape.h:97:   instantiated from here
FSVector.h:246: error: no matching function for call to ‘operator new(unsigned int, transform::FSShapeObject**&)’
<built-in>:0: note: candidates are: void* operator new(unsigned int)
make[1]: *** [FSButtonEvent.o] Error 1
make[1]: Leaving directory `/home/matio/Desktop/f4l-0.2/src/flagStonePort/transform-cxx-bsd/transform'
make: *** [sub-src-flagStonePort-transform-cxx-bsd-transform] Error 2


```

---

### Post by theOtherMarino on 2009-01-25
> **theOtherMarino said:**
> Be also aware of the following: there's a patch to apply. Read this page to know why and what : [http://aur.archlinux.org/packages.php?ID=5805](http://aur.archlinux.org/packages.php?ID=5805)

There are some lines of code to be corrected through the patch. If yoy don't know how to apply a patch, here is the list of chages

In **/src/f4lmdoc.cpp**
change :
```
#include <iostream.h>
```
for: 
```
#include <iostream>
```

In **/src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h**,
change:
```
FSDefineSound::FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```
for
```
FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```

In **/src/flagStonePort/transform-cxx-bsd/transform/FSVector.h**,
change :
```
#include <new.h>
```
for:
```
#include <new>
```

You should have it. Regards,

Marino ceccotti
[http://markup.fr/](http://markup.fr/)

---

### Post by matmatmat on 2009-01-26
Thanks for the help! Somebody should try and develop this further.

############NOTE############
It is **NOT** usable so  
there is no point in 
downloading it & expecting 
to get anything done!
############################

---

### Post by theOtherMarino on 2009-01-29
Unthinckable. The MAIN PROBLEM is that the f4l GUI is a perfect clone of Macromedia/Adobe Flash and there are serious copyright infringement issues.

The Pixel Image Editor ([http://www.kanzelsberger.com/pixel/?page_id=12](http://www.kanzelsberger.com/pixel/?page_id=12)) using a quasi-clone of the GUI of Adobe Photoshop may not last too. Read the forum first if you intend to purchase a license.

That's why the GIMP developpers have no problems of that kind. Macromedia/Adobe have done a very good job with Flash. They have hired ergonomics-skilled folks, designers, programmers. The GUI and the inner logic is their property.

The ".fla" and ".swf" formats... I don't know. I hope/guess they are free of use, as there are some other open-sources software that handle them like Salasaga ([http://www.salasaga.org/](http://www.salasaga.org/)) which may also interest you.

From my own little POV, Open-Source has to do it it's own way, using published standards, without clonage of commercial software.

Marino
[http://markup.fr/](http://markup.fr/)

---

### Post by Dracoo87 on 2010-04-21
> **theOtherMarino said:**
> There are some lines of code to be corrected through the patch. If yoy don't know how to apply a patch, here is the list of chages

In **/src/f4lmdoc.cpp**
change :
```
#include <iostream.h>
```for: 
```
#include <iostream>
```In **/src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h**,
change:
```
FSDefineSound::FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```for
```
FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```In **/src/flagStonePort/transform-cxx-bsd/transform/FSVector.h**,
change :
```
#include <new.h>
```for:
```
#include <new>
```You should have it. Regards,

Marino ceccotti
[http://markup.fr/](http://markup.fr/)

This helps a lot!
After this modification I can quietly run **make** but... In the end it fails compilation... I got a pile of warning :(

---

### Post by kuro_kid on 2010-08-26
> **theOtherMarino said:**
> There are some lines of code to be corrected through the patch. If yoy don't know how to apply a patch, here is the list of chages

In **/src/f4lmdoc.cpp**
change :
```
#include <iostream.h>
```for: 
```
#include <iostream>
```In **/src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h**,
change:
```
FSDefineSound::FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```for
```
FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```In **/src/flagStonePort/transform-cxx-bsd/transform/FSVector.h**,
change :
```
#include <new.h>
```for:
```
#include <new>
```You should have it. Regards,

Marino ceccotti
[http://markup.fr/](http://markup.fr/)
thank's man, i have serching all over the web and only your solution work for me
thank's again

---

### Post by micklock on 2011-07-17
Thank you **theOtherMarino**, 
your solution was the cherry on top of the cake I needed. 
Here's all the steps I did to get f4l running on my Debian Squeeze:
[LIST=1]
[*]I got f4l-0.2.1 from [SourceForge]("http://sourceforge.net/projects/f4l/files/f4l_beta_swfExport/0.2.1/f4l-0.2.1.tar.bz2/download"), 
[*]installed qt3-dev libraries and followed the steps on[ this page]("http://www.unfreeze.net/?page_id=54"),
[*]and finally applied the 3 code changes you propose below, [*] and finally compiled using:
```
qmake -project
qmake -o Makefile f4l.pro
make

```
[/LIST]

Hope this works for you guys too. 


> **theOtherMarino said:**
> There are some lines of code to be corrected through the patch. If yoy don't know how to apply a patch, here is the list of chages

In **/src/f4lmdoc.cpp**
change :
```
#include <iostream.h>
```
for: 
```
#include <iostream>
```

In **/src/flagStonePort/transform-cxx-bsd/transform/FSDefineSound.h**,
change:
```
FSDefineSound::FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```
for
```
FSDefineSound(int anIdentifier, int encoding, int rate, int channels, int sampleSize, int count, byte* bytes, size_t length);
```

In **/src/flagStonePort/transform-cxx-bsd/transform/FSVector.h**,
change :
```
#include <new.h>
```
for:
```
#include <new>
```

You should have it. Regards,

Marino ceccotti
[http://markup.fr/](http://markup.fr/)

---

