---
title: "FretsOnFire - cant run"
date: 2013-04-05
forum: Gaming &amp; Leisure
---

### Post by MadleSs on 2013-04-05
Hi guys I have downloaded Frets, but when I try to run it with ./FretsOnFire I'm getting this message - 
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: /usr/lib/i386-linux-gnu/libsndfile.so.1: undefined symbol: vorbis_version_string


Don't know if will it help but, when I try to run FretsOnFire.bin I get this one - 
./FretsOnFire.bin: error while loading shared libraries: libpython2.4.so.1.0: cannot open shared object file: No such file or directory

I'm a newbie to linux, thanks for every response ...

---

### Post by MG&amp;TL on 2013-04-05
You're missing required libraries, or have the wrong ones. Unless you have a very good reason to be downloading the release manually, I'd suggest just installing it via the software centre. If you need a newer version of it, install the software centre version (which will get all of the required libraries), then you can get the release a little easier.

---

### Post by MadleSs on 2013-04-05
Well, I have downloaded all the libraries I found after searching libpython ... and I am still getting this masseage - 
Traceback (most recent call last):
  File "/home/skyostil/src/cx_Freeze-3.0.3/initscripts/Console.py", line 27, in ?
  File "src/FretsOnFire.py", line 36, in ?
  File "src/GameEngine.py", line 24, in ?
  File "/usr/lib/python2.4/site-packages/pygame/__init__.py", line 75, in ?
  File "ExtensionLoader_pygame_base.py", line 12, in ?
ImportError: /usr/lib/i386-linux-gnu/libsndfile.so.1: undefined symbol: vorbis_version_string


I think ist time for manualy search for libraries... Can someone help how to search that library?

//Well after a little bit of searching I have found that library and game is now working :) ... Problem solved... can be locked

---

