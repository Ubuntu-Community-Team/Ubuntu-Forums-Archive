---
title: "Octave - Gnuplot TikZ terminal"
date: 2010-02-05
forum: Education &amp; Science
---

### Post by gerion on 2010-02-05
Though it's not a specific Ubuntu issue, I hope someone can help me with it: 

I was trying to use the tikz terminal. unfortunately, I haven't been able to get the terminal running. 
I'm using Ubuntu 9.10 and have installed lua5.1.

Following the instructions in the gnuplot tikz terminal archive, I edited the lua.trm, added the term.h file and the LIBS variable. Not sure how to adapt the include path for lua, it's installed in the default directory.

Having done this, the make command gives the following errors

In file included from term.h:376,
                 from term.c:1308:
../term/post.trm: In function ‘PS_graphics’:
../term/post.trm:1668: warning: format not a string literal and no format arguments
In file included from term.h:459,
                 from term.c:1308:
../term/lua.trm:98:17: error: lua.h: No such file or directory
../term/lua.trm:99:21: error: lauxlib.h: No such file or directory
In file included from term.h:459,
                 from term.c:1308:
../term/lua.trm: At top level:
../term/lua.trm:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
../term/lua.trm:113: error: expected ‘)’ before ‘*’ token
[...]

I also tried gnuplot-4.4.0-rc1 which seems to include the tikz terminal, but it's not available after installation.

Many thanks for any suggestions!

---

### Post by gerion on 2010-02-06
after more reading, I found out that for gnuplot4.4-rc1 lua-paths have to be set. So the configure command reads like

LUA_CFLAGS="-I /usr/include/lua5.1/lua.h" LUA_LIBS="-L /usr/lib/liblua5.1.a" ./configure --with-lua=yes

The command gives the following output:

...
checking for LUA... yes
checking for library containing luaL_openlibs... no
...
=== configuring in lisp (/home/christian/Desktop/gnuplot-4.4.0-rc1/lisp)
configure: running /bin/bash ./configure --disable-option-checking '--prefix=/usr/local'  '--with-lua=yes' 'LUA_CFLAGS=-I /usr/include/lua5.1/lua.h' 'LUA_LIBS=-L /usr/lib/liblua5.1.a' --cache-file=/dev/null --srcdir=.
..
** Configuration summary for gnuplot 4.4.0-rc1:

gnuplot will be compiled with the following terminals:
...
lua/TikZ terminal: no 
...

Any ideas how to make this work? cheers

---

### Post by gerion on 2010-02-09
The problem is actually already described and solved here:
[http://ubuntuforums.org/showthread.php?t=1127979](http://ubuntuforums.org/showthread.php?t=1127979)

just a hint: the terminal is called "tikz" in gnuplot4.4-rc1, not "lua" as it was earlier.

---

