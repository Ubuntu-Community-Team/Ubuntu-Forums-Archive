---
title: "HELP!! screensave plugin installation."
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by poo_22 on 2008-01-17
hi. first of all thx in advance for any replies or help given.. i will be very greatfull.
also im sort of a linux noob, so pls if your gonna make me use the terminal tell me exactly what to type.

i wanted to install the additional screensaver plugin for compiz-fusion
(the one that takes your windows for a spin.)
its' not available through synaptic, so i followed this turotial: [http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

everything is good untill i do "make" which gives me this:
```
phil@metalbox:~/compiz/screensaver$ make
compiling : rotatingcube.cpp -> build/rotatingcube.loIn file included from screensaver_internal.h:9,
                 from rotatingcube.h:4,
                 from rotatingcube.cpp:1:
build/screensaver_options.h:15:27: error: compiz-common.h: No such file or directory
build/screensaver_options.h:17: error: 'COMPIZ_BEGIN_DECLS' does not name a type
screensaver_internal.h:37: error: expected constructor, destructor, or type conversion before 'extern'
rotatingcube.cpp: In member function 'virtual void ScreenRotatingCube::preparePaintScreen(int)':
rotatingcube.cpp:75: error: 'displayPrivateIndex' was not declared in this scope
make: *** [build/rotatingcube.lo] Error 1
phil@metalbox:~/compiz/screensaver$ 

```
im runing 32bit on athlon xp with geforce2 mx400 and 3/4gig ram if that helps.

---

### Post by poo_22 on 2008-01-18
can nobody help me?

---

### Post by Espreon on 2008-01-18
You want it that bad? Then look for my CF from GIT installation guide, it should be on the second page on this board... The guide installs the Screensaver plugin when it installs CF from GIT...

---

### Post by poo_22 on 2008-01-19
every time i run the make command i get a long list of errors though!

also can u install extra plugins from synaptic?

---

### Post by Espreon on 2008-01-19
There are no extra plugins in the repos.

Try installing bcop and the Compiz development headers:

```

sudo apt-get install build-essential compiz-bcop compiz-dev

```

Then try running the make command

---

### Post by poo_22 on 2008-01-19
it says i have the latest version.

---

### Post by poo_22 on 2008-01-19
well, i didnt' fix it. but i reinstalled ubuntu because a lot of other stuff broke, and everything works fine..

thx for your help Espreon.

---

