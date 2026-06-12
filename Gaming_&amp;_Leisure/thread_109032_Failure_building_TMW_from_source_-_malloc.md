---
title: "Failure building TMW from source - malloc?"
date: 2005-12-27
forum: Gaming &amp; Leisure
---

### Post by lrmall01 on 2005-12-27
I'm trying to build TMW from source for Ubuntu.

I built the latest Guichan from source - with the modification needed for gcc 4 compatibility.  All the other libs come from the Ubunut repository.

./configure seems ok
================
.
..
...
config.status: config.h is unchanged
config.status: executing depfiles commands

Build with OpenGL: no

configure complete, now type "make"

make doesn't seem to complete though
==========================
.
..
...
gui/char_server.cpp:179: error: ‘rpl_malloc’ was not declared in this scope
make[2]: *** [tmw-char_server.o] Error 1
make[2]: Leaving directory `/usr/src/tmw-0.0.18/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/tmw-0.0.18'
make: *** [all] Error 2
lrmall01@crom:/usr/src/tmw-0.0.18$

There is one suspicious line in the .configure output - I've installed just about anything I can think of that has to do with malloc or compiliation but I can't get this to say 'yes'.

checking for stdlib.h... (cached) yes
**checking for GNU libc compatible malloc... no**
checking for stdlib.h... (cached) yes
checking for GNU libc compatible realloc... no
checking sys/select.h usability... yes

Any help would be greatly appreciated.

Thanks.

---

### Post by mcmuffy on 2005-12-27
I also get an error with malloc during the make stage.

-char_server.o `test -f 'gui/char_server.cpp' || echo './'`gui/char_server.cpp; \
then mv -f ".deps/tmw-char_server.Tpo" ".deps/tmw-char_server.Po"; else rm -f ".deps/tmw-char_server.Tpo"; exit 1; fi
gui/char_server.cpp: In member function ‘void ServerSelectDialog::selectServer(int)’:
gui/char_server.cpp:179: error: ‘rpl_malloc’ was not declared in this scope
make[2]: *** [tmw-char_server.o] Error 1
make[2]: Leaving directory `/media/hdb1/Downloads/From Firefox/tmw-0.0.18/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/media/hdb1/Downloads/From Firefox/tmw-0.0.18'
make: *** [all] Error 2

Any ideas would be welcome as I am just about to give up on this game as it took me all my time to get the damn gui library working.

---

### Post by lrmall01 on 2005-12-27
FWIW, I grabbed the cvs and tried building it.  ./configure seems the same as before, make fails differently though.

lrmall01@crom:/usr/src/tmw$ make
make[1]: Entering directory `/usr/src/tmw'
cd . && autoheader
make[1]: Leaving directory `/usr/src/tmw'
cd . \
  && CONFIG_FILES= CONFIG_HEADERS=[config.h:config.h.in] \
     /bin/sh ./config.status
config.status: creating [config.h
config.status: error: cannot find input file: config.h.in]
make: *** [stamp-h] Error 1

To me, it doesn't seem to be related to the previous error.  Maybe something to do with the CVS checkout.  ??  I dunno.

---

### Post by lrmall01 on 2005-12-27
I was able to fix the first problem by copying the guichan config and header files from /usr/local/include to /usr/include and /usr/local/lib to /usr/lib

After that I was able to compile TMW and install from source, so now it works.

So, now the question becomes more of a system config issue - how can I make it see the libs that I compile manually in /usr/local/....?  I assume I need to set an environment variable - but which variable?

Also, something is still wrong with CVS compile - It gives the same error as shown in the previous post.  Oh well, at least I got the latest released version running - cvs may be broken or something.

Thanks.

---

### Post by mcmuffy on 2005-12-27
Your solution also solved my problem also, although I had errors with the make install until I moved the tmw source folder to the root of my home directory. After that it installed fine.
This program really had better be worth the effort it took to get it working.

---

### Post by lrmall01 on 2005-12-27
mcmuffy - FWIW, they'll probably get the debian repository compatible with Ubuntu at some point, keep your eyes peeled.

---

