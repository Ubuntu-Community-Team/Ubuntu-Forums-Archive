---
title: "Dark Oberon - Warcraft 2 from plasticine :)"
date: 2005-06-22
forum: Gaming &amp; Leisure
---

### Post by dolny on 2005-06-22
EDIT: I made a quick HOWTO, just look down :)

[http://dark-oberon.sourceforge.net/screenshots/2004-11-01_5_1024x768.jpg](http://dark-oberon.sourceforge.net/screenshots/2004-11-01_5_1024x768.jpg)
[http://dark-oberon.sourceforge.net/screenshots/2004-11-01_2_1024x768.jpg](http://dark-oberon.sourceforge.net/screenshots/2004-11-01_2_1024x768.jpg)

Looks great! Gonna check it out now. I hope it compiles :/

[http://dark-oberon.sourceforge.net/](http://dark-oberon.sourceforge.net/)

---

### Post by dolny on 2005-06-22
```
dolny@milkshake:~/gry/dark-oberon-1.0/dark-oberon$ make
cd src && make
make[1]: Wej&#347;cie do katalogu `/home/dolny/gry/dark-oberon-1.0/dark-oberon/src'
exctags * 2> /dev/null || ctags * 2> /dev/null
make[1]: [tags] B&#322;&#261;d 127 (zignorowany)
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doalloc.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doberon.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dobuildings.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c docomputer.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doconfig.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dodata.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dodepend.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dodraw.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doengine.cpp
doengine.cpp: In function `void ProcessChatMessage(TNET_MESSAGE*)':
doengine.cpp:2955: warning: suggest parentheses around assignment used as truth
   value
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doevents.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofactories.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofight.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofile.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofollower.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doforces.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dohost.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doipc.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dolayout.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doleader.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dologs.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c domap.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c domapunits.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c domouse.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c donet.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doperceptron.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doplayers.cpp
doplayers.cpp: In member function `void
   TACTIVITY_COUNTER::Move(TCOMPUTER_PLAYER*)':
doplayers.cpp:925: warning: suggest parentheses around assignment used as truth
   value
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doraces.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doschemes.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doselection.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dosimpletypes.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dosound.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dosources.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dounits.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dowalk.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doworkers.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c glfont.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c glgui.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c tga.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c utils.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 doalloc.o doberon.o dobuildings.o docomputer.o doconfig.o dodata.o dodepend.o dodraw.o doengine.o doevents.o dofactories.o dofight.o dofile.o dofollower.o doforces.o dohost.o doipc.o dolayout.o doleader.o dologs.o domap.o domapunits.o domouse.o donet.o doperceptron.o doplayers.o doraces.o doschemes.o doselection.o dosimpletypes.o dosound.o dosources.o dounits.o dowalk.o doworkers.o glfont.o glgui.o tga.o utils.o -L/usr/X11R6/lib -L/usr/lib -L../libs -pthread -lglfw -lGL -lX11 -lXxf86vm -lGLU -lXext -o doberon
/usr/bin/ld: cannot find -lglfw
collect2: ld returned 1 exit status
make[1]: *** [doberon] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/dolny/gry/dark-oberon-1.0/dark-oberon/src'
make: *** [build] B&#322;&#261;d 2
dolny@milkshake:~/gry/dark-oberon-1.0/dark-oberon$ make clean
cd src && make clean
make[1]: Wej&#347;cie do katalogu `/home/dolny/gry/dark-oberon-1.0/dark-oberon/src'
rm -f doalloc.o doberon.o dobuildings.o docomputer.o doconfig.o dodata.o dodepend.o dodraw.o doengine.o doevents.o dofactories.o dofight.o dofile.o dofollower.o doforces.o dohost.o doipc.o dolayout.o doleader.o dologs.o domap.o domapunits.o domouse.o donet.o doperceptron.o doplayers.o doraces.o doschemes.o doselection.o dosimpletypes.o dosound.o dosources.o dounits.o dowalk.o doworkers.o glfont.o glgui.o tga.o utils.o doberon *core core.* tags
make[1]: Opuszczenie katalogu `/home/dolny/gry/dark-oberon-1.0/dark-oberon/src'
rm -f doberon
dolny@milkshake:~/gry/dark-oberon-1.0/dark-oberon$ sudo make
Password:
cd src && make
make[1]: Wej&#347;cie do katalogu `/home/dolny/gry/dark-oberon-1.0/dark-oberon/src'
exctags * 2> /dev/null || ctags * 2> /dev/null
make[1]: [tags] B&#322;&#261;d 127 (zignorowany)
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doalloc.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doberon.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dobuildings.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c docomputer.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doconfig.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dodata.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dodepend.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dodraw.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doengine.cpp
doengine.cpp: In function `void ProcessChatMessage(TNET_MESSAGE*)':
doengine.cpp:2955: warning: suggest parentheses around assignment used as truth
   value
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doevents.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofactories.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofight.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofile.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dofollower.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doforces.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dohost.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doipc.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dolayout.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doleader.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dologs.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c domap.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c domapunits.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c domouse.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c donet.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doperceptron.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doplayers.cpp
doplayers.cpp: In member function `void
   TACTIVITY_COUNTER::Move(TCOMPUTER_PLAYER*)':
doplayers.cpp:925: warning: suggest parentheses around assignment used as truth
   value
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doraces.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doschemes.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doselection.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dosimpletypes.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dosound.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dosources.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dounits.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c dowalk.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c doworkers.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c glfont.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c glgui.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c tga.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 -c utils.cpp
g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 doalloc.o doberon.o dobuildings.o docomputer.o doconfig.o dodata.o dodepend.o dodraw.o doengine.o doevents.o dofactories.o dofight.o dofile.o dofollower.o doforces.o dohost.o doipc.o dolayout.o doleader.o dologs.o domap.o domapunits.o domouse.o donet.o doperceptron.o doplayers.o doraces.o doschemes.o doselection.o dosimpletypes.o dosound.o dosources.o dounits.o dowalk.o doworkers.o glfont.o glgui.o tga.o utils.o -L/usr/X11R6/lib -L/usr/lib -L../libs -pthread -lglfw -lGL -lX11 -lXxf86vm -lGLU -lXext -o doberon
/usr/bin/ld: cannot find -lglfw
collect2: ld returned 1 exit status
make[1]: *** [doberon] B&#322;&#261;d 1
make[1]: Opuszczenie katalogu `/home/dolny/gry/dark-oberon-1.0/dark-oberon/src'
make: *** [build] B&#322;&#261;d 2

```

HELP!

---

### Post by afonic on 2005-06-22
This looks nice!

I am downloading, I'll tell you my luck with compiling!

---

### Post by afonic on 2005-06-22
Is this broken or what?


It doesn't ask for another lib or something it just fills like 4 console screens with programming-like errors like these:

```
glgui.h:1103: error: 'GLfloat' is used as a type, but is not defined as a type.
glgui.h:1131: error: 'TGUI_COLOR' is used as a type, but is not defined as a
   type.
glgui.h:1136: error: 'GLfloat' is used as a type, but is not defined as a type.
glgui.h:1137: error: 'GLfloat' is used as a type, but is not defined as a type.
glgui.h:1144: error: type/value mismatch at argument 1 in template parameter
   list for `template<class T> class TSAVE_LIST'
glgui.h:1144: error:   expected a type, got `TCALLBACK'
glgui.h:1144: error: ISO C++ forbids declaration of `callback_list' with no
   type
glgui.h:1156: error: parse error before `,' token
glgui.h:1157: error: parse error before `)' token
glgui.h:1159: error: semicolon missing after declaration of `TGUI'
glgui.h:1159: error: ISO C++ forbids defining types within return type
glgui.h:1159: error: two or more data types in declaration of `SetCursorHeight'
glgui.h:1159: error: semicolon missing after declaration of `class TGUI'
glgui.h: In function `int SetCursorHeight(int)':
glgui.h:1159: error: `cursor_height' undeclared (first use this function)
glgui.h: In function `TGUI_LABEL* GetDefTooltip()':
glgui.h:1162: error: `def_tooltip' undeclared (first use this function)
glgui.h: In function `TGUI_MESSAGE_BOX* GetMessageBox()':
glgui.h:1165: error: `message_box' undeclared (first use this function)
glgui.h: At global scope:
glgui.h:1170: error: `GLfloat' was not declared in this scope
glgui.h:1170: error: parse error before `,' token
glgui.h:1170: error: virtual outside class declaration
glgui.h:1171: error: `GLfloat' was not declared in this scope
glgui.h:1171: error: parse error before `,' token
glgui.h:1171: error: virtual outside class declaration
glgui.h:1172: error: `GLfloat' was not declared in this scope
glgui.h:1172: error: parse error before `,' token
glgui.h:1172: error: virtual outside class declaration
glgui.h:1173: error: virtual outside class declaration
glgui.h: In function `void Lock()':
glgui.h:1178: error: `rlock' undeclared (first use this function)
``` 

I think I'll wait for a package.

---

### Post by dolny on 2005-06-22
Sucks :( Maybe someone will make a package soon.

---

### Post by dolny on 2005-06-22
1. Download the game and unpack it.
2. After unpacking it go to the game's directory and write:

```
sudo make
```

in the console.
3. You'll probably get an error. Download GLFW 2.5 - [http://glfw.sf.net/](http://glfw.sf.net/) and after installing it, copy libglfw.a into /usr/X11R6/lib or dark-oberon/libs
4. Issue this command:

```
./doberon
```

Enjoy :)

Edit: I checked it. The graphics looks ubercool but they have a long path before them :) They shouldn't call this version 1.0

---

### Post by afonic on 2005-06-22
Hi,

I get errors even when compiling GLFW. Did you do anything special to make it work?

```

afonic@Athlon64:~/Desktop/glfw-2.5$ sudo make x11
Checking for X11 libraries location...
 X11 libraries location: /usr/X11R6/lib

Checking whether we are using GNU C...
 Using GNU C: yes

Checking for XFree86 VidMode support...
 XFree86 VidMode extension: no

Checking for pthread support...
 pthread support: no

Checking for glXGetProcAddress support...
 glXGetProcAddress extension:    no
 glXGetProcAddressARB extension: no
 glXGetProcAddressEXT extension: no

Checking for dlopen support...
 dlopen support: no

Checking for sysconf support...
 sysconf support: no

Checking for sysctl support...
 sysctl support: no

Creating ./lib/x11/Makefile.x11...

Creating ./examples/Makefile.x11...

make[1]: Entering directory `/home/afonic/Desktop/glfw-2.5/lib/x11'
gcc -c -I. -I..  -I/usr/X11R6/include -Os -Wall -o enable.o ../enable.c
In file included from ../internal.h:65,
                 from ../enable.c:36:
platform.h:48:22: X11/Xlib.h: No such file or directory
platform.h:49:24: X11/keysym.h: No such file or directory
platform.h:50:23: X11/Xatom.h: No such file or directory
platform.h:51:20: GL/glx.h: No such file or directory
In file included from platform.h:52,
                 from ../internal.h:65,
                 from ../enable.c:36:
../../include/GL/glfw.h:167:20: GL/gl.h: No such file or directory
../../include/GL/glfw.h:168:21: GL/glu.h: No such file or directory
In file included from ../internal.h:65,
                 from ../enable.c:36:
platform.h:202: error: syntax error before "Window"
platform.h:202: warning: no semicolon at end of struct or union
platform.h:204: error: syntax error before '*' token
platform.h:204: warning: type defaults to `int' in declaration of `VI'
platform.h:204: warning: data definition has no type or storage class
platform.h:205: error: syntax error before "CX"
platform.h:205: warning: type defaults to `int' in declaration of `CX'
platform.h:205: warning: data definition has no type or storage class
platform.h:206: error: syntax error before "WMDeleteWindow"
platform.h:206: warning: type defaults to `int' in declaration of `WMDeleteWindow'
platform.h:206: warning: data definition has no type or storage class
platform.h:219: error: syntax error before '}' token
platform.h:269: error: syntax error before "Display"
platform.h:269: warning: no semicolon at end of struct or union
platform.h:273: error: syntax error before '}' token
platform.h:273: warning: type defaults to `int' in declaration of `_glfwDisplay'platform.h:273: warning: data definition has no type or storage class
platform.h:406: error: syntax error before "_glfwCreateNULLCursor"
platform.h:406: error: syntax error before '*' token
platform.h:406: warning: type defaults to `int' in declaration of `_glfwCreateNULLCursor'
platform.h:406: warning: data definition has no type or storage class
platform.h:413: error: syntax error before "keysym"
In file included from ../enable.c:36:
../internal.h:175: warning: type defaults to `int' in declaration of `GLubyte'
../internal.h:175: error: syntax error before '*' token
../enable.c: In function `_glfwEnableMouseCursor':
../enable.c:50: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:50: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:59: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:59: error: `GL_FALSE' undeclared (first use in this function)
../enable.c:59: error: (Each undeclared identifier is reported only once
../enable.c:59: error: for each function it appears in.)
../enable.c: In function `_glfwDisableMouseCursor':
../enable.c:64: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:64: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:73: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:74: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:77: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:77: error: `GL_TRUE' undeclared (first use in this function)
../enable.c: In function `_glfwEnableSystemKeys':
../enable.c:142: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:150: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:150: error: `GL_FALSE' undeclared (first use in this function)
../enable.c: In function `_glfwDisableSystemKeys':
../enable.c:155: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:163: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c:163: error: `GL_TRUE' undeclared (first use in this function)
../enable.c: In function `_glfwEnableAutoPollEvents':
../enable.c:190: error: invalid use of incomplete typedef `_GLFWwin'
../enable.c: In function `_glfwDisableAutoPollEvents':
../enable.c:195: error: invalid use of incomplete typedef `_GLFWwin'
make[1]: *** [enable.o] Error 1
make[1]: Leaving directory `/home/afonic/Desktop/glfw-2.5/lib/x11'
make: *** [x11] Error 2
afonic@Athlon64:~/Desktop/glfw-2.5$

```

---

### Post by dolny on 2005-06-22
:( It worked flawlessly on my penguin...

---

### Post by afonic on 2005-06-22
Is this file all the games needs to run or you need to install this thing correctly as well?

If it is, maybe you can send it to me?

---

### Post by dolny on 2005-06-22
[http://www.echostar.pl/~dolny/ubu/libglfw.a](http://www.echostar.pl/~dolny/ubu/libglfw.a)

:)

---

### Post by afonic on 2005-06-22
OK I got it working. Thanks a lot!

However you are right. This is not 1.0 nor stable (crashed 2-3 times). Also it needs a better installation system :-)
I am looking forward for the next versions, if any!

---

### Post by jdodson on 2005-06-22
i got it to compile.  i am on a fairly buggy laptop though.  the game did work though.

beyond the terse build proccess because of some strange libraries, it is a really cool game.  the graphics are really well done, i hope they continue the game, it will be a very good game.

---

### Post by skoal on 2005-06-22
Great game. Great potential.  Now, can somebody tell me where in the game I get the shotgun?  I keep getting these duck symbols over my buildings and I can't build any more units, so I assume I'm supposed to go duck hunting.  I'm all for that.  Anybody know where I get the shotgun?

\\//_

---

### Post by ericsp on 2005-06-23
If anyone would be able to make a deb file..... Installation is too complicated for the average ubuntu user, I think.

---

### Post by skoal on 2005-06-23
[QUOTE=ericsp]If anyone would be able to make a deb file..... Installation is too complicated for the average ubuntu user, I think.[/QUOTE]
I actually made 3 deb files, but don't have anywhere to host them.  I got sound working on it too.  This game is really 1.0 and very playable with a friend.  I have.  I'm just currently trying to translate the documentation into english.  I've been poking inside the code, and somewhere around there you can actually use an map/game editor, I think.

Anyways, I've made 3 deb files: for libglfw, libfmod, and then dark-oberon.  I just don't have anyway to host ~60MB.

If anyone else wants to try this game out with sound, throw libfmod-3.74.so in /usr/lib or update ld.so.conf (if you put it somewhere else), and in dark-oberon/src/Makefile, link in 'libfmod' at the end:

LIBRARIES = -pthread -lglfw -lGL -lX11 -lXxf86vm -lGLU -lXext -lfmod-3.74

and run make with 'make SOUND=1'.  I'll be durned if these guys ain't using the *exact* same sounds from warcraft 2.  Someone else compile in sound and tell me if I'm not imagining things...

\\//_

---

### Post by afonic on 2005-06-23
Hi,
I can host them, I have plenty of space. PM me for details.

---

### Post by skoal on 2005-06-23
afonic, I'm ripping the lib packages into separate ones and converting 'glfw' static lib to a shareable one.  'libglfw' is actually pretty cool and I've been tinkering around with some GL tests, since they have some cool examples you build with the source (which I'll drop in the -dev package).

Also, I'm going to bust the dark-oberon package into 3 more manageable ones: dark-oberon (6 MB), dark-oberon-data (48 MB), and dark-oberon-docs (4 MB) (or just leave the last one out entirely).  I'll see what I can do by this weekend.  I'll pm you later today and see about getting you these 3 packages as they are, so you can test them out until I spit and polish 'em this weekend.

\\//_

---

### Post by Burgundavia on 2005-06-23
Those packages can probably find there way into Ubuntu. List them on MOTUNewPackages on the wiki.

Also, this monday the MOTU's are going to be looking at the various packages on NewPackages, so now is good time to list.

Corey

---

### Post by glasscleaner on 2005-06-24
any news of these package?

---

### Post by skoal on 2005-06-24
Oops! Didn't know that many people wanted to try 'em out.  Been working on other side projects while coming back to fix these.  I'll see if I can't upload them to someone somewhere by tomorrow, or maybe sooner.  I'll see what I can do...

In the meantime, you should be able to compile them from the steps in these threads.

\\//_

---

### Post by glasscleaner on 2005-06-24
[QUOTE=skoal]Oops! Didn't know that many people wanted to try 'em out.  Been working on other side projects while coming back to fix these.  I'll see if I can't upload them to someone somewhere by tomorrow, or maybe sooner.  I'll see what I can do...

In the meantime, you should be able to compile them from the steps in these threads.

\\//_[/QUOTE]

since 1 hour i try to compile that crap :)

---

### Post by skoal on 2005-06-24
Tell me where you're stuck compiling.  Maybe I can help...

\\//_

---

### Post by glasscleaner on 2005-06-24
[QUOTE=skoal]Tell me where you're stuck compiling.  Maybe I can help...

\\//_[/QUOTE]


well this is compiling now. error of me when i copy the file libglfw.a 

i forgot the sudo command :)

EDIT:

im stuck here  ](*,) 

```

g++ -g -Wall -O -I/usr/X11R6/include -I/usr/X11R6/include/GL -I../libs -DDATA_DIR='""' -DUNIX=1 -DSOUND=0 -DDEBUG=0 doalloc.o doberon.o dobuildings.o docomputer.o doconfig.o dodata.o dodepend.o dodraw.o doengine.o doevents.o dofactories.o dofight.o dofile.o dofollower.o doforces.o dohost.o doipc.o dolayout.o doleader.o dologs.o domap.o domapunits.o domouse.o donet.o doperceptron.o doplayers.o doraces.o doschemes.o doselection.o dosimpletypes.o dosound.o dosources.o dounits.o dowalk.o doworkers.o glfont.o glgui.o tga.o utils.o -L/usr/X11R6/lib -L/usr/lib -L/usr/local/lib -L../libs -pthread -lglfw -lGL -lX11 -lXxf86vm -lGLU -lXext -o ../doberon
/usr/bin/ld: cannot find -lXxf86vm
collect2: ld returned 1 exit status
make[1]: *** [../doberon] Error 1
make[1]: Leaving directory `/home/amphore/files/jeuxlinux/dark-oberon-1.0.1/src'
make: *** [build] Error 2
```

---

### Post by skoal on 2005-06-24
copy 'libglfw.a' into '<some-path>/dark-oberon/libs' and compile it again.

You actually don't need to use sudo (or root) to just test this game out.  I built everything in my /tmp directory and launched ./oberon from there before I made a package.

/edit! oops! stupid me. that's not what's causing that error.  just a sec...

'sudo apt-get install libxxf86vm1' *should fix it*.

\\//_

---

### Post by glasscleaner on 2005-06-24
](*,) 


libxxf86vm1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

i think is not that

---

### Post by skoal on 2005-06-24
```
skoal@morpheus:///tmp/dark-oberon/libs $ dpkg -S libXxf86vm
libxxf86vm-dev: /usr/X11R6/lib/libXxf86vm.a
libxxf86vm-dev: /usr/X11R6/lib/libXxf86vm.so
libxxf86vm1: /usr/X11R6/lib/libXxf86vm.so.1.0
libxxf86vm1: /usr/X11R6/lib/libXxf86vm.so.1
```
Maybe you need the -dev package.  Install 'libxxf86vm-dev' and see what happens.

\\//_

---

### Post by glasscleaner on 2005-06-24
[QUOTE=skoal]```
skoal@morpheus:///tmp/dark-oberon/libs $ dpkg -S libXxf86vm
libxxf86vm-dev: /usr/X11R6/lib/libXxf86vm.a
libxxf86vm-dev: /usr/X11R6/lib/libXxf86vm.so
libxxf86vm1: /usr/X11R6/lib/libXxf86vm.so.1.0
libxxf86vm1: /usr/X11R6/lib/libXxf86vm.so.1
```
Maybe you need the -dev package.  Install 'libxxf86vm-dev' and see what happens.

\\//_[/QUOTE]

work :)

---

### Post by skoal on 2005-06-24
sweet...

now, if you really want to enjoy the game, go back to page 2 in this thread and read my prior post on how to add sound to the game, or click [here](http://www.ubuntuforums.org/showpost.php?p=225697&postcount=15).  You'll have to recompile the whole gizmo from the start again.  But it's worth it...

Maybe I'll get these packages done tonite.  We'll see.  I just hate to release it as is.  I've already had to redo one package library, recompile another library that is generic to all video cards, not just my Nvidia.  So, I'll get the packages out there when I feel they're more "reliable" so as not to get swamped by "having problems with your packages..." type messages.

\\//_

---

### Post by stamy on 2005-07-15
A French guy (Sebastien Ducoulombier) has published a DEBIAN package fot this game, thank's to him.

First copy the .deb file anywhere on the disk ([http://www.lesdeveloppementsdurables.org/debian/dists/unstable/dark-oberon/dark-oberon_1.0.1-1_i386.deb](http://www.lesdeveloppementsdurables.org/debian/dists/unstable/dark-oberon/dark-oberon_1.0.1-1_i386.deb)) and as **root** (in a root console or with the sudo command) type this command:
dpkg --install --force-depends dark-oberon_1.0.1-1_i386.deb

Now it is installed, so you can add a launcher on your Desktop by right clicking on it and choose add new launcher, so browse the disk and choose the application "dark-oberon" under "/usr/games/dark-oberon".

If you wish you can also choose an icon.

This version is unfortunately compiled without "sound" support :-( but you are only missing the song in the game because there are no sound effects in the game yet.

---

### Post by jlapier on 2005-08-14
I tried this package and got:

```

The following packages have unmet dependencies:
  dark-oberon: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu14 is installed.
```

---

### Post by stamy on 2005-08-15
Sorry, but i write it down in the rest of my post, it works only if you install the package by hand.

First download the .deb file on you harddrive:
[http://www.lesdeveloppementsdurables.org/debian/dists/unstable/dark-oberon/dark-oberon_1.0.1-1_i386.deb](http://www.lesdeveloppementsdurables.org/debian/dists/unstable/dark-oberon/dark-oberon_1.0.1-1_i386.deb)

Go to the location you have downloaded the file (in a console with root privileges).

Then as **root** type this command:
dpkg --install --force-depends dark-oberon_1.0.1-1_i386.deb

Now it is installed, so you can add a launcher on your Desktop by right clicking on it and choose add new launcher, so browse the disk and choose the application "dark-oberon" under "/usr/games/dark-oberon".

---

### Post by blackant on 2005-08-15
hmm... I installed it but I am not getting any sound from it...
Any help?

Thanks.

---

### Post by stamy on 2005-08-15
It is normal.

Compiling Dark Oberon with sound is a little bit complicated, so this person has compiled it without sound. I have compiled it on my old PC, but there is only music, no sound effects ...

But, even with sound support, the only thing you can hearing is music, no sound effect implemented right now in the game. The game is not finished and the sound support need to be integrated.

You can look for the project at sourceforge at this place:
[http://sourceforge.net/forum/forum.php?thread_id=1307521&forum_id=227592](http://sourceforge.net/forum/forum.php?thread_id=1307521&forum_id=227592)

or:
[http://dark-oberon.sourceforge.net](http://dark-oberon.sourceforge.net)

---

### Post by H4rm0ny on 2005-09-17
I had a few problems compiling this which no-one else seems to have run into. I'm also having one final problem running it. 

On running **./dark-oberon** , I get the following:
```

harmony/dark-oberon-1.0.2-RC1:$ ./dark-oberon
Crit: Could not create mutex
Info: Loading configuration from '/home/taliesin/.dark-oberon/config.cfg'
Info: Loading data
Info: Loading textures from 'dat/fonts.dat'
Info: Loading textures from 'dat/gui.dat'
Info: Loading textures from 'dat/cursors.dat'
Aborted

```

As I understand it, failure to create mutex is some hideous threading problem, so any help with this is much appreciated. 

I had some problems compiling this which weren't covered in this thread, so in order to make this a bit more newby-friendly, I've stated what I've done so far. Also, if I've made a cock-up, then maybe someone can point it out to me. :)

Using Kynaptic, I installed the following packages (may not need all of them, just being impatient):
libxxf86dga-dev
libxxf86misc1-dev
libxxf86vm1-dev

I downloaded glfw2.5 and compiled this. Then copied **libglfw.a** from **glfw-2.5/lib/x11/[b] to [b]/usr/lib/** and copied **glfw.h** from **glfw-2.5/include/GL/** to **/usr/X11R6/include/GL/**. 

I then downloaded the source for Dark Oberon1.02 and untarred. There was something screwy in the make file preventing it from finding a header file, so I added the bold to the line near the beginning of the make file in **/dark-oberon/src/**
```
LIBRARIES = -pthread -lglfw -lGL -lX11 -lGLU **-lXxf86vm**
```

It then successfully compiled.

And that's as far as I've got... anyone, please?

(oh yes - the config file in the home directory specifies "1024x768" display regardless of your actual monitor settings. Don't know if this is a problem on others as I haven't got this far, yet).

---

### Post by juantxorena on 2005-09-18
Greetings.

I've managed to compile and play Dark Oberon with sound. However, I don't know how to play. I mean, it's quite simple, it's very similar to Warcraft II (without archers :( ). But there are some guys called moleman, which i don't know what they do. Also there are three "layers", the "normal" layer, with buildings, people, and the like; other layer in which you can see the moleman, but anything more (moleman can pass through water!); and a third layer, only with dirt. 

There aren't any complete english manual, only in slovak, which i don't understand.

Anyone?

---

### Post by juantxorena on 2005-09-18
Never mind, I discovered it playing. The 2nd layer is the underground. Only molemen can walk around there. There are rocks of coal, and the molemen can mine them. The 3rd layer I don't know what it is.
The graphics are cool, the idea is nice, however, the game is very simple: Only 5 units: Catapult, footmen, peasant, zeppelin, molemen. Only 2 attacking units: footmen and catapult. No ships, no flying attacks, no archers, no horsemen...
Buildings: farms, barracks, workshop, manufactury (workshop's upgrade), tower, cannon tower, wall, citadel (watch tower), town hall, fort (1st town hall's upgrade), castle (2st town hall's upgrade). Only that.
Hope the game will growth in the future, but for now, it's too small.

---

