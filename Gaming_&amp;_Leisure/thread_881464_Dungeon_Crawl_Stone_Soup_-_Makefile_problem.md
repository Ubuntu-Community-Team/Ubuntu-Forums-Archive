---
title: "Dungeon Crawl Stone Soup - Makefile problem"
date: 2008-08-06
forum: Gaming &amp; Leisure
---

### Post by KarmaticStylee on 2008-08-06
I've been trying to install my favorite laptop game, dungeon crawl stone soup, for the past 2 days.. 

I downloaded the latest version from [http://sourceforge.net/project/showfiles.php?group_id=143991](http://sourceforge.net/project/showfiles.php?group_id=143991)

designated in the make file that I want x11

checked the INSTALL file and I'm pretty sure I have the dependencies mentioned..

when I go to make, I get: 

make  -f makefile.x11
make[1]: Entering directory `/home/eric/Desktop/stonesoup/source'
echo Building Lua...
Building Lua...
cd util/lua/src && make crawl_unix
make[2]: Entering directory `/home/eric/Desktop/stonesoup/source/util/lua/src'
make "LUA_A=liblua.a" \
	"MYCFLAGS=" "MYLIBS=" "MYLDFLAGS=" liblua.a
make[3]: Entering directory `/home/eric/Desktop/stonesoup/source/util/lua/src'
gcc -O2 -Wall    -c -o lapi.o lapi.c
lapi.c:8:20: error: assert.h: No such file or directory
lapi.c:9:18: error: math.h: No such file or directory
lapi.c:11:20: error: string.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:11,
                 from luaconf.h:11,
                 from lua.h:16,
                 from lapi.c:16:
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory
lapi.c: In function &#8216;lua_pushstring&#8217;:
lapi.c:454: warning: implicit declaration of function &#8216;strlen&#8217;
lapi.c:454: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
lapi.c: In function &#8216;lua_getfield&#8217;:
lapi.c:546: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
lapi.c: In function &#8216;lua_setfield&#8217;:
lapi.c:660: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
make[3]: *** [lapi.o] Error 1
make[3]: Leaving directory `/home/eric/Desktop/stonesoup/source/util/lua/src'
make[2]: *** [crawl_unix] Error 2
make[2]: Leaving directory `/home/eric/Desktop/stonesoup/source/util/lua/src'
make[1]: *** [util/lua/srcllua.a] Error 2
make[1]: Leaving directory `/home/eric/Desktop/stonesoup/source'
make: *** [all] Error 2

---

### Post by KarmaticStylee on 2008-08-06
Just had my a breakthrough by installing a recent gcc (and g++).. still getting errors but let me see that I can't figure the rest out now!

---

### Post by prshah on 2008-08-06
> **KarmaticStylee said:**
> 
lapi.c:8:20: error: assert.h: No such file or directory
lapi.c:9:18: error: math.h: No such file or directory
lapi.c:11:20: error: string.h: No such file or directory
/usr/lib/gcc/i486-linux-gnu/4.2.3/include/limits.h:122:61: error: limits.h: No such file or directory


I think you need to install build-essential```
sudo apt-get install build-essential
```

---

