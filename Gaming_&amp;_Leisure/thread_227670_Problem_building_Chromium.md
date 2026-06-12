---
title: "Problem building Chromium"
date: 2006-08-02
forum: Gaming &amp; Leisure
---

### Post by ScottFW on 2006-08-02
Maybe this type of question belongs in the newb forum, but maybe somebody in here has had this problem as well? I'm trying to install Chromium.
**./configure** seems to go okay. Here's the output:

> scott@ubuntu:~/src/chromium/Chromium-0.9$ ./configure
------------------------------------------------------------
**  This is a script to determine what options
**  should be built into Chromium B.S.U.
**  It is not an autoconf configure script.
------------------------------------------------------------

    Verify SDL install:
    ------------------
    found /usr/bin/sdl-config
    SDL version (1.2.9) ok.

    Verify smpeg install:
    --------------------
    found /usr/bin/smpeg-config
    smpeg version (0.4.5) ok.

**  WARNING: QTDIR environment variable not set!
**  If you want to build the chromium-setup app, you need to have
**  Qt 2.x or greater installed, and set the QTDIR environment
**  variable to where it is installed. Common locations for Qt
**  would be /usr/lib/qt2 or /usr/lib/qt-2.x.x.
**  The setup app is *NOT* a requirement to play Chromium B.S.U. -
**  it is merely a convinent way to set game options and create
**  playlists.
**  The setup app will not be built.

------------------------------------------------------------
    wrote ./config.mak
    wrote ./Makefile

    Now, type 'make' to build Chromium B.S.U.!


Then **make** gives me this:
> scott@ubuntu:~/src/chromium/Chromium-0.9$ make
cd support/openal/; make
make[1]: Entering directory `/home/scott/src/chromium/Chromium-0.9/support/openal'
mkdir -p ./lib
cd linux; sh autogen.sh; ./configure --enable-sdl --enable-smpeg; make
autoheader: WARNING: Using auxiliary files such as `acconfig.h', `config.h.bot'
autoheader: WARNING: and `config.h.top', to define templates for `config.h.in'
autoheader: WARNING: is deprecated and discouraged.
autoheader:
autoheader: WARNING: Using the third argument of `AC_DEFINE' and
autoheader: WARNING: `AC_DEFINE_UNQUOTED' allows to define a template without
autoheader: WARNING: `acconfig.h':
autoheader:
autoheader: WARNING:   AC_DEFINE([NEED_FUNC_MAIN], 1,
autoheader:             [Define if a function `main' is needed.])
autoheader:
autoheader: WARNING: More sophisticated templates can also be produced, see the
autoheader: WARNING: documentation.
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking how to run the C preprocessor... gcc -E
checking whether byte ordering is bigendian... no
checking for sin in -lm... yes
checking for dlopen in -ldl... yes
./configure: line 3732: syntax error near unexpected token `newline'
./configure: line 3732: `  yes:no:'
make[2]: Entering directory `/home/scott/src/chromium/Chromium-0.9/support/openal/linux'
make[2]: *** No targets specified and no makefile found.  Stop.
make[2]: Leaving directory `/home/scott/src/chromium/Chromium-0.9/support/openal/linux'
make[1]: *** [linux] Error 2
make[1]: Leaving directory `/home/scott/src/chromium/Chromium-0.9/support/openal'
make: *** [support/openal/] Error 2

I'm kind of new at trying to decipher all these warnings and errors. Can anybody help me get this installed?

---

### Post by Perfect Storm on 2006-08-02
You don't need to compile Chromium. It's in your repo. if you enable universe in your sourcelist. Then you can do this:

```
sudo apt-get install chromium
```

Any other reason why you want to compile it?

---

### Post by ScottFW on 2006-08-02
Oh. Ummmm... yeah. That worked.:-\" 
Thanks!

The text in the game is kind of screwy though (pic attached). I can figure out the top option is "new game" and the bottom one is "exit" which I suppose is all I need to get in a quick shoot-em-up fix. Any idea how to fix this? If not, no biggie, it mostly works.

---

