---
title: "Spectaculum (old school RPG) compiling help (total newb)"
date: 2006-06-27
forum: Gaming &amp; Leisure
---

### Post by Envy on 2006-06-27
So, I found Spectaculum, which is essentially Eye of the Beholder 2 for Linux

But I'm still new to Linux, I have no idea how to install it; I have a .zip of the source, it has a folder in it, in the folder is a bunch of files like configure and makefile (which I understand are important)

I just don't know how I'm supposed to use those to install the game


Is there some sort of basic guide to this kind of stuff that I've simply missed?

EDIT: hey, I'm getting better at this, now I just get a huge error message when I tell it to "make", so huge I'm not going to try to fit it, but it mostly involves:

stuff like this

./mediawrapper.cpp:680: error: &#8216;Mix_HaltChannel&#8217; was not declared in this scope
./mediawrapper.cpp: In member function &#8216;bool MEDIAWrapper::isPlaying(int)&#8217;:
./mediawrapper.cpp:689: error: &#8216;sound&#8217; was not declared in this scope

./SFont.c:122: error: &#8216;SDL_Surface&#8217; was not declared in this scope
./SFont.c:122: error: &#8216;screen&#8217; was not declared in this scope
./SFont.c:122: error: expected primary-expression before &#8216;int&#8217;

and this at the end

make[2]: *** [spectalum.o] Error 1
make[2]: Leaving directory `/home/mnelson/spectalum/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mnelson/spectalum'
make: *** [all] Error 2

---

### Post by mlind on 2006-06-27
[QUOTE=Envy]So, I found Spectaculum, which is essentially Eye of the Beholder 2 for Linux

But I'm still new to Linux, I have no idea how to install it; I have a .zip of the source, it has a folder in it, in the folder is a bunch of files like configure and makefile (which I understand are important)

I just don't know how I'm supposed to use those to install the game


Is there some sort of basic guide to this kind of stuff that I've simply missed?[/QUOTE]

You must install build-essential package to be able to compile programs, it's not
installed by default.
```

sudo aptitude install build-essential

```

Normal drill is
```

./configure && make && make install

```

To see available configuration options, try
```

./configure --help

```

To install this application to safe place without breaking anything
```

./configure --prefix=$HOME

```

or even
```

./configure --prefix=$HOME/games

```

---

### Post by tribaal on 2006-06-27
Well fairly easy steps:

- Make sure you have build-essentials installed. ("sudo apt-get install build-essentials" to make sure).
- Unpack the source in whatever temp directory you want.
- Navigate to that directory, then do: "./configure", and answer any questions that may arise.
- The the allmighty "make" (no "./"). This might take a while, and usually a lot of output is displayed on screen. Don't panic if some lines say "Warning" or look like something nasty is happening, if something is *really* wrong then the compilation will stop.
- And finally "make install".

You should be all set!

- trib'

**EDIT:** Man I'm too slow... again :)

---

### Post by mlind on 2006-06-27
[QUOTE=tribaal]
**EDIT:** Man I'm too slow... again :)[/QUOTE]

My fingers are on fire today :mrgreen:

---

### Post by Envy on 2006-06-27
ok, I understand it now, but the commands seem not to be going well

I get a lot of messages most of which I assume aren't that important when I do make

then when I go make install, I get those errors I edited into my first post namely:

make[1]: *** [spectalum.o] Error 1
make[1]: Leaving directory `/home/mnelson/spectalum/src'
make: *** [install-recursive] Error 1

being the last part of it

so from that I'm stumped because then nothing happens. I don't know whether it's something I'm doing or if it's the source or my machine or what.

I just tried using checkinstall instead and it at least gave me a clear message:

make[1]: *** [spectalum.o] Error 1
make[1]: Leaving directory `/home/mnelson/spectalum/src'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

---

### Post by mlind on 2006-06-27
Usually these are caused by some missing dependencies

when you run ./configure --prefix=$HOME/games

watch the output closely or you can redirect output to a file to view later using
```

./configure --prefix=$HOME/games > /~Desktop/build.log **2>&1**

```
This should create file called build.log file on your desktop.


Does configure complain about any missing libraries?

---

### Post by elmy on 2009-03-22
> **mlind said:**
> Usually these are caused by some missing dependencies

when you run ./configure --prefix=$HOME/games

watch the output closely or you can redirect output to a file to view later using
```

./configure --prefix=$HOME/games > /~Desktop/build.log **2>&1**

```
This should create file called build.log file on your desktop.


Does configure complain about any missing libraries?
Hi everyone,

I can't compile this either, analysis of the config.log shows:

conftest.c:10:28: error: ac_nonexistent.h: No such file or directory

It then goes onto say that the failed program was confdefs.h and it lists a whole bunch if #define 

| /* confdefs.h.  */
| #define PACKAGE_NAME ""
| #define PACKAGE_TARNAME ""
| #define PACKAGE_VERSION ""
| #define PACKAGE_STRING ""
| #define PACKAGE_BUGREPORT ""
| #define PACKAGE "spectalum"
| #define VERSION "0.0.1"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>

This occurs about 4 times in the log, but the list of #define details varies. Not sure what this means. I have compiled this before on an earlier ubuntu build but I may have had dependencies installed from other projects that I can't identify now in order to put themback on again.

I have installed build essentials, g++, libsdl1.2-dev and libtool, each time I got further,but now I'm stuck

---

