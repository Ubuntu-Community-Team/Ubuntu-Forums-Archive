---
title: "Notion window manager"
date: 2012-07-04
forum: Desktop Environments
---

### Post by linc186 on 2012-07-04
It won't compile and I'm not sure why. Here's some terminal output. Any help is appreciated. Thank you!

```
root@lincoln-Inspiron-537:/home/lincoln/notion# make
set -e; for i in libmainloop libtu libextl mod_tiling mod_query mod_menu mod_dock mod_sp mod_sm mod_statusbar de mod_xinerama mod_xrandr mod_xkbevents mod_notionflux ioncore notion etc utils man po; do make -C $i; done
make[1]: Entering directory `/home/lincoln/notion/libmainloop'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/libmainloop'
make[1]: Entering directory `/home/lincoln/notion/libtu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/libtu'
make[1]: Entering directory `/home/lincoln/notion/libextl'
sed "1s:LUA50:/usr/bin/lua:" libextl-mkexports.in > libextl-mkexports
make[1]: Leaving directory `/home/lincoln/notion/libextl'
make[1]: Entering directory `/home/lincoln/notion/mod_tiling'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_tiling'
make[1]: Entering directory `/home/lincoln/notion/mod_query'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_query'
make[1]: Entering directory `/home/lincoln/notion/mod_menu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_menu'
make[1]: Entering directory `/home/lincoln/notion/mod_dock'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_dock'
make[1]: Entering directory `/home/lincoln/notion/mod_sp'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_sp'
make[1]: Entering directory `/home/lincoln/notion/mod_sm'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_sm'
make[1]: Entering directory `/home/lincoln/notion/mod_statusbar'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_statusbar'
make[1]: Entering directory `/home/lincoln/notion/de'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/de'
make[1]: Entering directory `/home/lincoln/notion/mod_xinerama'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/lincoln/notion/mod_xinerama'
make: *** [subdirs] Error 2
```

---

### Post by msammels on 2012-07-04
> **linc186 said:**
> It won't compile and I'm not sure why. Here's some terminal output. Any help is appreciated. Thank you!

```
root@lincoln-Inspiron-537:/home/lincoln/notion# make
set -e; for i in libmainloop libtu libextl mod_tiling mod_query mod_menu mod_dock mod_sp mod_sm mod_statusbar de mod_xinerama mod_xrandr mod_xkbevents mod_notionflux ioncore notion etc utils man po; do make -C $i; done
make[1]: Entering directory `/home/lincoln/notion/libmainloop'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/libmainloop'
make[1]: Entering directory `/home/lincoln/notion/libtu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/libtu'
make[1]: Entering directory `/home/lincoln/notion/libextl'
sed "1s:LUA50:/usr/bin/lua:" libextl-mkexports.in > libextl-mkexports
make[1]: Leaving directory `/home/lincoln/notion/libextl'
make[1]: Entering directory `/home/lincoln/notion/mod_tiling'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_tiling'
make[1]: Entering directory `/home/lincoln/notion/mod_query'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_query'
make[1]: Entering directory `/home/lincoln/notion/mod_menu'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_menu'
make[1]: Entering directory `/home/lincoln/notion/mod_dock'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_dock'
make[1]: Entering directory `/home/lincoln/notion/mod_sp'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_sp'
make[1]: Entering directory `/home/lincoln/notion/mod_sm'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_sm'
make[1]: Entering directory `/home/lincoln/notion/mod_statusbar'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/mod_statusbar'
make[1]: Entering directory `/home/lincoln/notion/de'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/lincoln/notion/de'
make[1]: Entering directory `/home/lincoln/notion/mod_xinerama'
**make[1]: *** No targets specified and no makefile found.  Stop.**
make[1]: Leaving directory `/home/lincoln/notion/mod_xinerama'
make: *** [subdirs] Error 2
```

The line in bold is your biggest clue. Which operating system are using to compile this? Normally, errors like this indicate a problem with the makefile itself, though, and not an actual toolchain.

---

### Post by AopicieR on 2012-07-29
Hi, how did you obtain the source? Looks like something went pretty wrong there. Also let me say that Notion will be part of quantal[1].

[1] [http://packages.ubuntu.com/quantal/notion](http://packages.ubuntu.com/quantal/notion)

---

