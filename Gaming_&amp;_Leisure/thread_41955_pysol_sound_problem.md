---
title: "pysol sound problem"
date: 2005-06-15
forum: Gaming &amp; Leisure
---

### Post by NewbieEd on 2005-06-15
I love pysol, but there is no sound. I have downloaded and installed pysol-sounds and pysol-sound-server, but no luck. I have an integrated AC '97 sound card using the via82cxxx driver. All other sound applications work fine: CD audio, audio associated with mplayer, game audio (frozen bubble). Any suggestions?

---

### Post by GTvulse on 2005-06-15
You won't unless you recompile the sound server yourself. Those binaries were compiled for Python 2.3.x but Hoary has Python 2.4.x....

---

### Post by NewbieEd on 2005-06-15
How difficult is it to recompile the sound server?

---

### Post by GTvulse on 2005-06-16
Haven't tried it myself yet. But it shouldn't be very difficult, If it uses distutils, it is as easy as typing ```
sudo python setup.py install
``` after you have installed the build-essential metapackage with synaptic (the compiler packages are in the install CD if you don't want to download them from the net, some files are rather big).

If they use the obsolete Makefile.pre method (as used in Python 1.5 and older), the compilation is a bit more elaborate, but it is very easy as well (I haven't done one of those since the last century and I don't recall the details exactly, but they are documented in the python-doc package).

EDIT:
Don't forget to download the src package for the sound server and python-devl, you mey need some other -dev packages as well.

---

