---
title: "dungeon crawl stone soup"
date: 2012-01-10
forum: Gaming &amp; Leisure
---

### Post by Kwho on 2012-01-10
Very nearly all the help I needed was in a thread that got deleted, and I was advised to make a new thread. So here it is. I went off the following guide:

```
1. download the stone soup code from, [http://sourceforge.net/project/downl...-0.4.5-src.zip]("http://sourceforge.net/project/downloading.php?group_id=143991&filename=stone_soup-0.4.5-src.zip").  Remember where it is! 
2. install the following prerequisites before we compile 
3. sudo apt-get install libpng3  
4. sudo apt-get install bison  
5. sudo apt-get install libpng12-dev 
6. sudo apt-get install g++  
7. sudo apt-get install libx11-dev  
8. sudo apt-get install flex  
9. navigate to the directory where you saved the stone_soup-0.4.5-src.zip file you downloaded in step #1.  
10. unzip stone_soup-0.4.5-src.zip  
11. cd stone_soup-0.4.5-src.zip  
12. cd source  
13. gedit makefile, at the start of the file change it from  
MAKEFILE ?= makefile.unix  
#MAKEFILE ?= makefile.dos  
#MAKEFILE ?= makefile.osx 
#MAKEFILE ?= makefile.mgw  
#MAKEFILE ?= makefile_tiles.mgw  
#MAKEFILE ?= makefile.x11   
to look like  
#MAKEFILE ?= makefile.unix  
#MAKEFILE ?= makefile.dos 
#MAKEFILE ?= makefile.osx 
#MAKEFILE ?= makefile.mgw 
#MAKEFILE ?= makefile_tiles.mgw 
MAKEFILE ?= makefile.x11   
and save the file.    
14. you should still be in the stone_soup-0.4.5-src/source directory.  Type make.   If everything compiles without error you can run stone soup with tiles by typing ./crawl!   
15. have fun!
```
but at the end make fails in an error 2, does anyone have any ideas?

---

### Post by Kwho on 2012-01-10
60 views, no reply...

no one has any idea what the problem is?

---

### Post by Perfect Storm on 2012-01-11
Please have patience.


1. You need to post the terminal in/output if people are going to help you.
2. If you don't want to compile source codes, Stone Soup have an easy installation: [http://crawl.develz.org/wordpress/downloads#debian](http://crawl.develz.org/wordpress/downloads#debian)

---

### Post by Kwho on 2012-01-11
I need to post what?

---

### Post by Chronon on 2012-01-11
Post the output of "make".  People can't help if you don't show what the error is.

---

### Post by Kwho on 2012-01-11
I don't understand the easy download either

ok I don't understand anything

ok I understood that

---

### Post by Kwho on 2012-01-11
heres what it say's when I input make

make  -f makefile.x11
make[1]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source'
echo Building Lua...
Building Lua...
cd util/lua/src && make crawl_unix
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
make "LUA_A=liblua.a" \
    "MYCFLAGS=" "MYLIBS=" "MYLDFLAGS=" liblua.a
make[3]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
make[3]: `liblua.a' is up to date.
make[3]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
cd rltiles/ && make -f makefile.unix all CFLAGS="" LDFLAGS="" && cd ..
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/rltiles'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/rltiles'
g++  -Iutil -I. -Iutil/lua/src -DUSE_X11 -DUSE_TILE -Iutil/sqlite  -Wall -Wwrite-strings -Wshadow -pedantic -Wuninitialized -fsigned-char -DUNIX  -DCLUA_BINDINGS -O2  -c abl-show.cc
In file included from ./sqldbm.h:26:0,
                 from database.h:27,
                 from abl-show.cc:41:
util/sqlite/sqlite3.h:84:13: error: ‘uint64_t’ does not name a type
util/sqlite/sqlite3.h:574:38: error: ‘sqlite_uint64’ has not been declared
abl-show.cc: In function ‘bool activate_ability()’:
abl-show.cc:860:56: warning: suggest parentheses around ‘&&’ within ‘||’ [-Wparentheses]
make[1]: *** [abl-show.o] Error 1
make[1]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source'
make: *** [all] Error 2

---

### Post by oldrocker99 on 2012-01-11
> **Artificial Intelligence said:**
> Please have patience.


1. You need to post the terminal in/output if people are going to help you.
2. If you don't want to compile source codes, Stone Soup have an easy installation: [http://crawl.develz.org/wordpress/downloads#debian](http://crawl.develz.org/wordpress/downloads#debian)

#2 is the way to go; I had it installed in minutes. Thanks!

---

### Post by Perfect Storm on 2012-01-11
> **Kwho said:**
> heres what it say's when I input make

make  -f makefile.x11
make[1]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source'
echo Building Lua...
Building Lua...
cd util/lua/src && make crawl_unix
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
make "LUA_A=liblua.a" \
    "MYCFLAGS=" "MYLIBS=" "MYLDFLAGS=" liblua.a
make[3]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
make[3]: `liblua.a' is up to date.
make[3]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/util/lua/src'
cd rltiles/ && make -f makefile.unix all CFLAGS="" LDFLAGS="" && cd ..
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/rltiles'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source/rltiles'
g++  -Iutil -I. -Iutil/lua/src -DUSE_X11 -DUSE_TILE -Iutil/sqlite  -Wall -Wwrite-strings -Wshadow -pedantic -Wuninitialized -fsigned-char -DUNIX  -DCLUA_BINDINGS -O2  -c abl-show.cc
In file included from ./sqldbm.h:26:0,
                 from database.h:27,
                 from abl-show.cc:41:
util/sqlite/sqlite3.h:84:13: error: ‘uint64_t’ does not name a type
util/sqlite/sqlite3.h:574:38: error: ‘sqlite_uint64’ has not been declared
abl-show.cc: In function ‘bool activate_ability()’:
abl-show.cc:860:56: warning: suggest parentheses around ‘&&’ within ‘||’ [-Wparentheses]
make[1]: *** [abl-show.o] Error 1
make[1]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.4.5-src/source'
make: *** [all] Error 2

You're trying to compile a old source of Dungeon Soup. The latest is 0.9. That's one of the reason not to follow old guides (amongst other things). Get the latest stable version of Dungeon Soup.

But again, check the link I posted earlier. It's much easier.

---

### Post by Kwho on 2012-01-11
at this point, I want to do it both ways, because I don't understand either of them I click the link that says Debian/Ubuntu download console version, and I don't understand what it shows me

---

### Post by Kwho on 2012-01-12
> **oldrocker99 said:**
> #2 is the way to go; I had it installed in minutes. Thanks!
  I've tried using method 2, but it's not working

---

### Post by Kwho on 2012-01-12
I'm useless, ok you people are gods, help me

I got this when I tried to put this in the source from version 9

[B]make[1]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib'
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/lua/src'
    * rebuilding lua: new build flags or prefix
    CC lapi.o
    CC lcode.o
    CC ldebug.o
    CC ldo.o
    CC ldump.o
    CC lfunc.o
    CC lgc.o
    CC llex.o
    CC lmem.o
    CC lobject.o
    CC lopcodes.o
    CC lparser.o
    CC lstate.o
    CC lstring.o
    CC ltable.o
    CC ltm.o
    CC lundump.o
    CC lvm.o
    CC lzio.o
    CC lauxlib.o
    CC lbaselib.o
    CC ldblib.o
    CC liolib.o
    CC lmathlib.o
    CC loslib.o
    CC ltablib.o
    CC lstrlib.o
    CC loadlib.o
    CC linit.o
    AR liblua.a
    RANLIB liblua.a
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/lua/src'
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/lua/src'
    INSTALL lua.h
    INSTALL luaconf.h
    INSTALL lualib.h
    INSTALL lauxlib.h
    INSTALL liblua.a
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/lua/src'
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/sqlite'
    * rebuilding sqlite: new build flags or prefix
    CC sqlite3.o
    AR libsqlite3.a
    RANLIB libsqlite3.a
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/sqlite'
make[2]: Entering directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/sqlite'
    INSTALL sqlite3.h
    INSTALL libsqlite3.a
make[2]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib/sqlite'
make[1]: Leaving directory `/home/biggerbook/Desktop/stone_soup-0.9.0/source/contrib'
    GEN art-data.h
    GEN dc-unrand.txt
    GEN tiledef-unrand.cc
    CXX abl-show.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
    CXX abyss.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
    CXX acquire.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
    CXX act-iter.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
    CXX actor-los.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
    CXX actor.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
    CXX areas.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
    CXX arena.o
<command-line>:0:0: warning: "_FORTIFY_SOURCE" redefined [enabled by default]
<built-in>:0:0: note: this is the location of the previous definition
[/B]

---

### Post by Perfect Storm on 2012-01-12
It looks okay. It's done compiling. But you might want to add tiles if you don't want ASCII graphics. 


A quick compile guide;
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install build-essential libsdl-image1.2-dev libfreetype6-dev

wget http://sourceforge.net/projects/crawl-ref/files/Stone%20Soup/0.9.1/stone_soup-0.9.1.tar.bz2/download
tar xf stone_soup-0.9.1.tar.bz2
cd stone_soup-0.9.1/source
make TILES=y
./crawl
```

---

### Post by Kwho on 2012-01-13
I don't think I've mentioned but I prefer the ascii layout to tiles

if it's done compiling why when I enter ./crawl doesn't it run? I'm going to try what you suggested (except without tiles=y)

anyways thank you =)

---

### Post by Kwho on 2012-01-13
didn't work =/ was it anything to do with the caps lock FORTIFY SOURCE?

---

### Post by Perfect Storm on 2012-01-13
Lets try with adding Dungeon Soup source to your sourcelist and install via that.

Open Ubuntu Software Center, then click 'edit' and choose ---> 'Software Sources...'

Click 'Other Software' tab, and then press the 'add' button.

put this line into it;

**deb [http://crawl.develz.org/debian](http://crawl.develz.org/debian) crawl 0.9**

close Software sources.
Now search Ubuntu Software Center for 'Dungeon'.

---

### Post by Kwho on 2012-01-13
is there a way to get it in ascii that way? or to change it?

ok, another problem, I'm full of them... once I download something... anything, from the software center, where do I go to find it?

---

### Post by Perfect Storm on 2012-01-13
Click on Ubuntu icon in Unity, and search for dungeon.

If you want ASCII version install the one that is called 'Dungeon Crawl, a text-based roguelike game' instead.

---

### Post by Perfect Storm on 2012-01-13
Did you solve your problem(s)?

---

