---
title: "Stuck on Last Step of Installing - Tales of Maj'Eyal"
date: 2012-08-25
forum: Gaming &amp; Leisure
---

### Post by quddusaliquddus on 2012-08-25
I am trying to install thr game called - Tales of Maj'Eyal. I have Ubuntu Quantel installed. I am following the steps outlines in - [http://te4.org/wiki/howtocompile](http://te4.org/wiki/howtocompile). I have successfully done all but the last step i.e.

[B]Unpack the source code, cd into the folder you unpacked your code to and run the following:

premake4 gmake
make[/B]

I get:

**No Premake script (premake4.lua) found!**

If someone could help me itd be greatly appreciated. Thanks!

---

### Post by korgoth28 on 2012-10-12
My guess is that you need to copy the executable file you download from:
[http://sourceforge.net/projects/premake/files/Premake/4.3/premake-4.3-linux.tar.gz/download](http://sourceforge.net/projects/premake/files/Premake/4.3/premake-4.3-linux.tar.gz/download)

and instead of
premake4 gmake
run
sudo ./premake4 gmake

That page is rather awful, if I can get it to work I'll rewrite it. And if I like the game I might even fix the lua files in the SVN.

Anyway, I found this because I'm only one step further than OP, after the last command I get:

```
derek@lubuntu:/usr/local/src/t-engine4$ sudo ./premake4 gmake
Building configurations...
Running action 'gmake'...
Generating Makefile...
Generating build/TEngine.make...
Generating build/physfs.make...
Generating build/luajit2.make...
Generating build/luasocket.make...
Generating build/fov.make...
Generating build/lpeg.make...
Generating build/luaprofiler.make...
Generating build/lualanes.make...
Generating build/tcodimport.make...
Generating build/expatstatic.make...
Generating build/lxp.make...
Generating build/luamd5.make...
Generating build/luazlib.make...
Generating build/luabitop.make...
Generating build/utf8proc.make...
Generating build/te4-bzip.make...
Done.
```

Instructions stop here before any sort of executable is generated. You'd think make or make install would be appropriate at this point, but they just give errors:
```

derek@LUBUNTU1:/usr/local/src/t-engine4$ sudo make
[sudo] password for derek: 
==== Building physfs (debug) ====
Creating ../bin/Debug
Creating ../obj/Debug/physfs
physfs.c
../src/physfs/physfs.c:74:5: warning: initialization from incompatible pointer type [enabled by default]
../src/physfs/physfs.c:74:5: warning: (near initialization for ‘supported_types[0]’) [enabled by default]
physfs_unicode.c
physfsrwops.c
In file included from ../src/physfs/physfsrwops.h:27:0,
                 from ../src/physfs/physfsrwops.c:24:
../src/tSDL.h:7:17: fatal error: SDL.h: No such file or directory
compilation terminated.
make[1]: *** [../obj/Debug/physfs/physfsrwops.o] Error 1
make: *** [physfs] Error 2
```

Please help, I'm incredibly bored of ADOM and angband.

---

