---
title: "Compiling JVGS from Source"
date: 2010-02-23
forum: Gaming &amp; Leisure
---

### Post by beastrace91 on 2010-02-23
Howdy All,

So I am trying to compile [JVGS](http://jvgs.sourceforge.net/) from source on Ubuntu 9.10 32bit and it is dieing on me when I run **make** with the following output: ```
jeff@eeetop:~/Downloads/jvgs-0.5-src$ make
[  0%] Built target swig
[  6%] Built target core
[  8%] Built target input
[ 33%] Built target game
[ 36%] Built target tinyxml
[ 64%] Built target sketch
[ 71%] Built target video
[ 87%] Built target math
[ 88%] Built target audio
[ 90%] Built target font
[ 98%] Built target effect
[ 99%] Building CXX object src/bind/CMakeFiles/bind.dir/jvgslua.cpp.o
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:726:17: error: lua.h: No such file or directory
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:727:21: error: lauxlib.h: No such file or directory
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:745: error: ‘lua_CFunction’ does not name a type
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:746: error: ‘lua_CFunction’ does not name a type
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:761: error: ‘lua_CFunction’ does not name a type
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:766: error: ‘lua_CFunction’ does not name a type
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:767: error: ‘lua_CFunction’ does not name a type
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:773: error: ‘lua_CFunction’ does not name a type
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:850: error: ‘lua_State’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:850: error: ‘L’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:850: error: expected ‘,’ or ‘;’ before ‘{’ token
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:861: error: variable or field ‘SWIG_Lua_SetModule’ declared void
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:861: error: ‘lua_State’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:861: error: ‘L’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:861: error: expected primary-expression before ‘*’ token
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:861: error: ‘module’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:875: error: ‘lua_State’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:875: error: ‘L’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:876: error: expected ‘,’ or ‘;’ before ‘{’ token
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:887: error: ‘lua_State’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:887: error: ‘L’ was not declared in this scope
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:888: error: expected ‘,’ or ‘;’ before ‘{’ token
In file included from /usr/include/c++/4.4/new:40,
                 from /usr/include/c++/4.4/ext/new_allocator.h:33,
                 from /usr/include/c++/4.4/i486-linux-gnu/bits/c++allocator.h:34,
                 from /usr/include/c++/4.4/bits/allocator.h:48,
                 from /usr/include/c++/4.4/string:43,
                 from /home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:1599:
/usr/include/c++/4.4/exception:35: error: expected ‘}’ before end of line
/usr/include/c++/4.4/exception:35: error: expected declaration before end of line
make[2]: *** [src/bind/CMakeFiles/bind.dir/jvgslua.cpp.o] Error 1
make[1]: *** [src/bind/CMakeFiles/bind.dir/all] Error 2
make: *** [all] Error 2

```

I am by no means proficient in C so I am slightly lost as to what the error means. Suggestions?

~Jeff

---

### Post by Perfect Storm on 2010-02-23
> /home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:726:17: error: lua.h: No such file or directory
/home/jeff/Downloads/jvgs-0.5-src/src/bind/jvgslua.cpp:727:21: error: lauxlib.h: No such file or directory

install liblua5.1-0-dev package and see if it helps.

---

### Post by beastrace91 on 2010-02-23
> **Artificial Intelligence said:**
> install liblua5.1-0-dev package and see if it helps.

That did the trick.

Cheers,
~Jeff

---

### Post by Shannon_VanWagner on 2010-02-24
Here's the packages I had to install to get jvgs to pass cmake . and compile with make (for those who may need specifics):

sudo apt-get install build-essential cmake swig libfreetype6-dev zlib1g-dev liblua5.1-0-dev libsdl-mixer1.2-dev libsdl1.2-dev

Cheers!

---

