---
title: "PyPanel in universe is busted?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by duminas on 2005-12-14
Issued a quick ```
aptitude install pypanel
``` in the terminal, and whenever I try to execute it, this all gets spat out as an error message, and pypanel won't even start. This is on Breezy (5.10), using all official repositories--details of that can be found further in.

The error message when I try **$ pypanel** is:
> Traceback (most recent call last):
  File "/usr/bin/pypanel", line 923, in ?
    PyPanel(display.Display())
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/display.py", line 122, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: rootsMight anyone know what's going on?
This is installed from the Ubuntu official Universe repository, provided by the following lines in my sources.list file:
```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
```The version of pypanel is **2.3-1ubuntu1**. All listed dependencies of pypanel are installed (those which Aptitude shows), to my knowledge.

Thanks for any help.

---

### Post by duminas on 2005-12-14
And when I try to build it locally, I get this error:
```
ppmodule.c:37:25: error: X11/Xft/Xft.h: No such file or directory
ppmodule.c:40: error: syntax error before &#8216;*&#8217; token
ppmodule.c:40: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;draw&#8217;
ppmodule.c:40: warning: data definition has no type or storage class
ppmodule.c:41: error: syntax error before &#8216;*&#8217; token
ppmodule.c:41: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;xf&#8217;
ppmodule.c:41: warning: data definition has no type or storage class
ppmodule.c: In function &#8216;_ppfont&#8217;:
ppmodule.c:71: error: &#8216;XftColor&#8217; undeclared (first use in this function)
ppmodule.c:71: error: (Each undeclared identifier is reported only once
ppmodule.c:71: error: for each function it appears in.)
ppmodule.c:71: error: syntax error before &#8216;xftcol&#8217;
ppmodule.c:72: error: &#8216;XGlyphInfo&#8217; undeclared (first use in this function)
ppmodule.c:73: error: &#8216;XRenderColor&#8217; undeclared (first use in this function)
ppmodule.c:91: warning: implicit declaration of function &#8216;XftTextExtentsUtf8&#8217;
ppmodule.c:91: error: &#8216;ginfo&#8217; undeclared (first use in this function)
ppmodule.c:100: error: request for member &#8216;ascent&#8217; in something not a structure or union
ppmodule.c:100: error: request for member &#8216;ascent&#8217; in something not a structure 
or union
ppmodule.c:100: error: request for member &#8216;descent&#8217; in something not a structure or union
ppmodule.c:101: error: &#8216;rcol&#8217; undeclared (first use in this function)
ppmodule.c:105: warning: implicit declaration of function &#8216;XftColorAllocValue&#8217;
ppmodule.c:105: error: &#8216;xftcol&#8217; undeclared (first use in this function)
ppmodule.c:106: warning: implicit declaration of function &#8216;XftDrawStringUtf8&#8217;
ppmodule.c:107: warning: implicit declaration of function &#8216;XftColorFree&#8217;
ppmodule.c: In function &#8216;_ppfontsize&#8217;:
ppmodule.c:126: error: &#8216;XGlyphInfo&#8217; undeclared (first use in this function)
ppmodule.c:126: error: syntax error before &#8216;ginfo&#8217;
ppmodule.c:136: error: &#8216;ginfo&#8217; undeclared (first use in this function)
ppmodule.c: In function &#8216;_ppicon&#8217;:
ppmodule.c:166: warning: pointer targets in passing argument 6 of &#8216;XGetGeometry&#8217; differ in signedness
ppmodule.c:166: warning: pointer targets in passing argument 7 of &#8216;XGetGeometry&#8217; differ in signedness
ppmodule.c:166: warning: pointer targets in passing argument 8 of &#8216;XGetGeometry&#8217; differ in signedness
ppmodule.c:166: warning: pointer targets in passing argument 9 of &#8216;XGetGeometry&#8217; differ in signedness
ppmodule.c: In function &#8216;_ppinit&#8217;:
ppmodule.c:277: warning: implicit declaration of function &#8216;XftFontOpenXlfd&#8217;
ppmodule.c:277: warning: assignment makes pointer from integer without a cast
ppmodule.c:279: warning: implicit declaration of function &#8216;XftFontOpenName&#8217;
ppmodule.c:279: warning: assignment makes pointer from integer without a cast
ppmodule.c:283: warning: implicit declaration of function &#8216;XftDrawCreate&#8217;
ppmodule.c:283: warning: assignment makes pointer from integer without a cast
error: command 'gcc' failed with exit status 1
```
I've got libimlib2, libimlib2-dev, xlibs-dev, python2.4-xlib, build-essential, and python-xlib (and all their dependencies) installed. What's going on?

---

### Post by obibok on 2006-01-10
*bump*

problem confirmed and still unresolved

---

### Post by andril on 2006-01-10
I noticed that alot of the apps are starting to go unavailable in universe - I had an similar issue :confused:

---

### Post by graabein on 2006-06-15
I got the same problem with pypanel...

```
Traceback (most recent call last):
  File "/usr/bin/pypanel", line 957, in ?
    PyPanel(display.Display())
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/usr/lib/python2.4/site-packages/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/display.py", line 123, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/usr/lib/python2.4/site-packages/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: roots
```

---

### Post by GnuKemist on 2006-08-15
I have managed to find the answer somewhere else:  [http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html](http://www.linuxforums.org/forum/linux-desktop-x-windows/50612-pypanel.html)

Basically, open your /usr/lib/python2.5/site-packages/Xlib/protocol/display.py file, and then change the following line:

```
recv = self.socket.recv(2048
```)

to:

```
recv = self.socket.recv(4096)
```

Cheers,

---

### Post by garren on 2006-11-03
The fix didn't work for me--mostly, I think, because I have no "display.py" in xlib.  I tried using a fix on another thread ([http://www.ubuntuforums.org/showthread.php?t=280236](http://www.ubuntuforums.org/showthread.php?t=280236)) with no luck.  
Here's the error I get: 

[INDENT]PyPanel requires the Python X library -
[http://sourceforge.net/projects/python-xlib/](http://sourceforge.net/projects/python-xlib/)[/INDENT]

even though I already have the most up-to-date Python X library.  My guess is that it thinks I have no X library because I don't have display.py.  

Would it work to just have someone post a funtional display.py file?  I don't really know what's in there...

---

### Post by moore.bryan on 2006-11-21
[I]garren...
it might not be looking for the most recent python x lib, just the right one for pypanel to work properly.  couple of questions:
(1) are you running edgy or dapper?
(2) which wm are you using?
(3) which pypanel were you using?
[/I]

---

### Post by Extreme Coder on 2006-12-17
I'm having the same error as garren(about python-xlib), and what's worse is that pypanel is busted in Edgy repositories. I tried the way moore.bryan posted in another topic, but i get the same python-xlib problem. Hope I find a fix :(

---

### Post by Metallinut on 2007-10-31
I'm having a similar problem.  I'm on Gutsy...
I installed Python X Library and Imlib before trying...and made sure I have python-dev installed.  Here's the output I get:

```
jp@UbuntuBox:~/installs/pypanel/PyPanel-2.4$ sudo python setup.py install
running install
running build
running build_ext
building 'ppmodule' extension
gcc -pthread -fno-strict-aliasing -DNDEBUG -g -O2 -Wall -Wstrict-prototypes -fPIC -DHAVE_XFT=1 -DIMLIB2_FIX=1 -I/usr/X11R6/include -I/usr/include/freetype2 -I/usr/include/python2.5 -c ppmodule.c -o build/temp.linux-i686-2.5/ppmodule.o -Wall
ppmodule.c:37:25: error: X11/Xft/Xft.h: No such file or directory
ppmodule.c:40: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c:41: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
ppmodule.c: In function ‘_ppfont’:
ppmodule.c:71: error: ‘XftColor’ undeclared (first use in this function)
ppmodule.c:71: error: (Each undeclared identifier is reported only once
ppmodule.c:71: error: for each function it appears in.)
ppmodule.c:71: error: expected ‘;’ before ‘xftcol’
ppmodule.c:72: error: ‘XGlyphInfo’ undeclared (first use in this function)
ppmodule.c:72: error: expected ‘;’ before ‘ginfo’
ppmodule.c:73: error: ‘XRenderColor’ undeclared (first use in this function)
ppmodule.c:73: error: expected ‘;’ before ‘rcol’
ppmodule.c:91: warning: implicit declaration of function ‘XftTextExtentsUtf8’
ppmodule.c:91: error: ‘xf’ undeclared (first use in this function)
ppmodule.c:91: error: ‘ginfo’ undeclared (first use in this function)
ppmodule.c:101: error: ‘rcol’ undeclared (first use in this function)
ppmodule.c:105: warning: implicit declaration of function ‘XftColorAllocValue’
ppmodule.c:105: error: ‘xftcol’ undeclared (first use in this function)
ppmodule.c:106: warning: implicit declaration of function ‘XftDrawStringUtf8’
ppmodule.c:106: error: ‘draw’ undeclared (first use in this function)
ppmodule.c:107: warning: implicit declaration of function ‘XftColorFree’
ppmodule.c: In function ‘_ppfontsize’:
ppmodule.c:126: error: ‘XGlyphInfo’ undeclared (first use in this function)
ppmodule.c:126: error: expected ‘;’ before ‘ginfo’
ppmodule.c:136: error: ‘xf’ undeclared (first use in this function)
ppmodule.c:136: error: ‘ginfo’ undeclared (first use in this function)
ppmodule.c: In function ‘_ppicon’:
ppmodule.c:166: warning: pointer targets in passing argument 6 of ‘XGetGeometry’ differ in signedness
ppmodule.c:166: warning: pointer targets in passing argument 7 of ‘XGetGeometry’ differ in signedness
ppmodule.c:166: warning: pointer targets in passing argument 8 of ‘XGetGeometry’ differ in signedness
ppmodule.c:166: warning: pointer targets in passing argument 9 of ‘XGetGeometry’ differ in signedness
ppmodule.c: In function ‘_ppinit’:
ppmodule.c:277: error: ‘xf’ undeclared (first use in this function)
ppmodule.c:277: warning: implicit declaration of function ‘XftFontOpenXlfd’
ppmodule.c:279: warning: implicit declaration of function ‘XftFontOpenName’
ppmodule.c:283: error: ‘draw’ undeclared (first use in this function)
ppmodule.c:283: warning: implicit declaration of function ‘XftDrawCreate’
error: command 'gcc' failed with exit status 1
jp@UbuntuBox:~/installs/pypanel/PyPanel-2.4$ 
```

Any idea why this isn't installing?

---

