---
title: "Help installing Pushover."
date: 2010-03-30
forum: Gaming &amp; Leisure
---

### Post by blackdalek on 2010-03-30
I am trying to install this game on Ubuntu 9.10.

./configure didn't show up any errors. But when I try to run make,
I get this output from make -
```

dalek@dalek-laptop:~/Downloads/pushover-0.0.2$ make
make  all-recursive
make[1]: Entering directory `/home/dalek/Downloads/pushover-0.0.2'
Making all in po
make[2]: Entering directory `/home/dalek/Downloads/pushover-0.0.2/po'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dalek/Downloads/pushover-0.0.2/po'
make[2]: Entering directory `/home/dalek/Downloads/pushover-0.0.2'
g++ -DHAVE_CONFIG_H -I.   -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT -I/usr/include/lua5.1   -Wall -DPKGDATADIR=\"/usr/local/share/pushover\" -DLOCALEDIR=\"/usr/local/share/locale\" -g -O2 -MT pushover-ant.o -MD -MP -MF .deps/pushover-ant.Tpo -c -o pushover-ant.o `test -f 'src/ant.cpp' || echo './'`src/ant.cpp
In file included from src/ant.cpp:4:
src/soundsys.h:4:23: error: SDL_mixer.h: No such file or directory
In file included from src/ant.cpp:4:
src/soundsys.h:60: error: ISO C++ forbids declaration of ‘Mix_Chunk’ with no type
src/soundsys.h:60: error: expected ‘;’ before ‘*’ token
src/soundsys.h:78: error: ISO C++ forbids declaration of ‘Mix_Music’ with no type
src/soundsys.h:78: error: expected ‘;’ before ‘*’ token
make[2]: *** [pushover-ant.o] Error 1
make[2]: Leaving directory `/home/dalek/Downloads/pushover-0.0.2'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dalek/Downloads/pushover-0.0.2'
make: *** [all] Error 2
dalek@dalek-laptop:~/Downloads/pushover-0.0.2$ 

```

Source was downloaded from [http://pushover.sourceforge.net/](http://pushover.sourceforge.net/)
I had this running back on an Ubuntu 5.10 machine a few years back. Had no problems with install back then (might have been a different version of Pushover).
I am not sure how to get it to install on Ubuntu 9.10
Any help appreciated.

---

### Post by Naiki Muliaina on 2010-03-30
Cant realy help but OMG i loved this on the amiga! Gonna have to download when i get home and try compilin meself ^^

---

### Post by Perfect Storm on 2010-03-30
```
src/soundsys.h:4:23: error: SDL_mixer.h: No such file or directory
```

Check if libsdl_mixer-dev is installed.

---

### Post by DoktorSeven on 2010-03-30
Actual package you'll probably be wanting is **libsdl-mixer1.2-dev**

General rule of thumb: if "make" or "configure" complains about **something.h** missing, do a search in your repositories (via synaptic or **apt-cache search *search terms here***) for that something, generally removing any characters such as _ or -, then finding the most likely candidate that ends with **-dev** and installing it.

---

### Post by Rustybolts on 2010-03-30
Or just install using deb located here
[http://ftp.riken.go.jp/Linux/ubuntu/pool/universe/p/pushover/](http://ftp.riken.go.jp/Linux/ubuntu/pool/universe/p/pushover/)
Or
Just tried the windows version works very nice using wine.

---

