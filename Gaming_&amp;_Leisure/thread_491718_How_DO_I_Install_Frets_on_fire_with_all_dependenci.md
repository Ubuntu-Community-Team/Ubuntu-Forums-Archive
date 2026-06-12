---
title: "How DO I Install Frets on fire with all dependencies"
date: 2007-07-03
forum: Gaming &amp; Leisure
---

### Post by mchaggis211 on 2007-07-03
Hi this may be a newb question but ive been having probelms installing the newest version of frets on fire for linux

my OS is ubuntu fiesty 64 bit an i have nvidia drivers 

a .deb would be best other wise a quick how to would be great

---

### Post by hikaricore on 2007-07-04
Renamed thread.

"How to" Threads are for telling others how to do thing.

"How do I" Threads are for asking questions.

You could try the debian packages (not recommended just throwing it out there) linked to in the
comments section of this page: [http://debaday.debian.net/2007/07/01/frets-on-fire-play-the-guitar-with-your-keyboard-rock-em/](http://debaday.debian.net/2007/07/01/frets-on-fire-play-the-guitar-with-your-keyboard-rock-em/)

Otherwise what kinda trouble are you having?  Compiling from source I'm guessing?

---

### Post by Naegling23 on 2007-07-04
I dont think you install Frets on Fire.

Download the linux client and extract it wherever you want.  Just run the frets.sh file and thats it.  

./frets.sh

---

### Post by mchaggis211 on 2007-07-04
when i run ./FretsOnFire i get this error

Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by hardyn on 2007-07-04
it might be a 32/64 bit conflict...
you might have to install 32bit python libs.

---

### Post by hikaricore on 2007-07-04
> **mchaggis211 said:**
> ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

Hmm it seems you may not have libSDL installed.

Try:

```
sudo aptitude install libsdl1.2-all
```

---

### Post by MadleSs on 2013-04-04
I have got the same problem... libraries didn't helped me... This is my error message:
./FretsOnFire
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 23, in ?
  File "/usr/lib/python2.4/site-packages/OpenGL/GL/__init__.py", line 2, in ?
  File "/usr/lib/python2.4/site-packages/OpenGL/raw/GL/__init__.py", line 6, in ?
  File "/usr/lib/python2.4/site-packages/OpenGL/raw/GL/constants.py", line 7, in ?
  File "/usr/lib/python2.4/site-packages/OpenGL/platform/__init__.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/OpenGL/platform/glx.py", line 41, in ?
  File "/usr/lib/python2.4/site-packages/OpenGL/platform/ctypesloader.py", line 37, in loadLibrary
  File "/usr/lib/python2.4/site-packages/ctypes/__init__.py", line 340, in __init__
OSError: glut: cannot open shared object file: No such file or directory

---

### Post by Perfect Storm on 2013-04-04
Very old thread. Please start a new one.


Thread closed.

---

