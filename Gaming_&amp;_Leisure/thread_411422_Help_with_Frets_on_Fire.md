---
title: "Help with Frets on Fire"
date: 2007-04-16
forum: Gaming &amp; Leisure
---

### Post by zbrooks on 2007-04-16
okay so i downloaded the tar file for frets on fire and then extracted into a folder on my desktop.  when i try to run it though i get this error:

```
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or director
```

does anyone know what this means? and how can i get the game to work?  thanks.

---

### Post by buttons on 2007-04-16
> **zbrooks said:**
> okay so i downloaded the tar file for frets on fire and then extracted into a folder on my desktop.  when i try to run it though i get this error:

```
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or director
```

does anyone know what this means? and how can i get the game to work?  thanks.

"ImportError: libSDL-1.2.so.0: cannot open shared object file: No such file or directory"

Sounds like you're missing libSDL-1.2.so.0.  This is part of the libSDL package.

You could visit synaptic and download libsdl-1.2debian and a libsdl-1.2debian-SOUNDSYSTEM package, or you can simply use the line I've provided which installs the alsa version.  I'm assuming you're using Edgy or later.

The other two libraries were dependencies of previous frets versions and likely no longer required.  Better safe than sorry though, eh?

```
apt-get install libsdl-ttf2.0-0 libsdl-mixer1.2 libsdl1.2debian libsdl1.2debian-alsa
```

Be sure and also have direct rendering enabled for your card.

---

