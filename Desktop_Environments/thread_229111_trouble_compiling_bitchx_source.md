---
title: "trouble compiling bitchx source"
date: 2006-08-04
forum: Desktop Environments
---

### Post by fooey on 2006-08-04
i installed the server cd,
and i want to install the bitchx source so i can use cypress theme.
because forsome reason it won't work with the binary.
anyway i keep getting this error on my 'make'
(yes it compiles fine)

```

cd source \
          && make 'local_dir=/root' 'INSTALL_IRC=/usr/local/bin/BitchX' 'IRCLIB=/usr/local/lib/bx' 'CC=gcc' 'CFLAGS=-g -O2 -Wall' 'HELPDIR=/usr/local/lib/bx/help' 'INSTALL_WSERV=/usr/local/lib/bx/wserv' 'IRCPATH=~/.BitchX:~/.BitchX/plugins:.:/usr/local/lib/bx/plugins:/usr/local/lib/bx/script:/usr/local/lib/bx' 'TRANSLATION_PATH=/usr/local/lib/bx/translation' 'LDFLAGS=' 'LIBS=-lncurses -lm -lcrypt -lresolv' 'LN=ln -s' 'RM=rm -f' 'TCL_SRCS=' 'TCL_OBJS=' 'CD_PLAY=' 'CD_SRCS=' 'CD_OBJS=' 'TCL_LIBS=' 'PLUGINDIR=/usr/local/lib/bx/plugins' '_VERSION_=BitchX' 'VERSION=BitchX-1.1-final' 'INSTALL_DATA=/usr/bin/install -c -m 644' 'INSTALL_SCRIPT=/usr/local/lib/bx/script' 'EXEEXT=' 'SHLIB_CFLAGS=' 'SHLIB_SUFFIX=.so' all
make[1]: Entering directory `/root/BitchX/source'
gcc -I. -I/root/BitchX/include -I../include -I. -I./include -g -O2 -Wall -c ctcp.c
ctcp.c:179: error: static declaration of &#915;Çÿctcp_type&#915;ÇÖ follows non-static declaration
/root/BitchX/include/ctcp.h:59: error: previous declaration of &#915;Çÿctcp_type&#915;ÇÖ was here
ctcp.c: In function &#915;Çÿdo_version&#915;ÇÖ:
ctcp.c:896: warning: pointer targets in passing argument 1 of &#915;Çÿstripansicodes&#915;ÇÖ differ in signedness
ctcp.c: In function &#915;Çÿdo_notice_ctcp&#915;ÇÖ:
ctcp.c:1367: warning: pointer targets in passing argument 1 of &#915;Çÿstripansi&#915;ÇÖ differ in signedness
make[1]: *** [ctcp.o] Error 1
make[1]: Leaving directory `/root/BitchX/source'
make: *** [BitchX] Error 2

```

by the way. all the weird looking characters displayed on my terminal should be in english. not sure why it's in 'jibberish' 

any idea? i think i have everything installed for it that i should

---

### Post by cantormath on 2006-08-04
> **fooey said:**
> i installed the server cd,
and i want to install the bitchx source so i can use cypress theme.
because forsome reason it won't work with the binary.
anyway i keep getting this error on my 'make'
(yes it compiles fine)

```

cd source \
          && make 'local_dir=/root' 'INSTALL_IRC=/usr/local/bin/BitchX' 'IRCLIB=/usr/local/lib/bx' 'CC=gcc' 'CFLAGS=-g -O2 -Wall' 'HELPDIR=/usr/local/lib/bx/help' 'INSTALL_WSERV=/usr/local/lib/bx/wserv' 'IRCPATH=~/.BitchX:~/.BitchX/plugins:.:/usr/local/lib/bx/plugins:/usr/local/lib/bx/script:/usr/local/lib/bx' 'TRANSLATION_PATH=/usr/local/lib/bx/translation' 'LDFLAGS=' 'LIBS=-lncurses -lm -lcrypt -lresolv' 'LN=ln -s' 'RM=rm -f' 'TCL_SRCS=' 'TCL_OBJS=' 'CD_PLAY=' 'CD_SRCS=' 'CD_OBJS=' 'TCL_LIBS=' 'PLUGINDIR=/usr/local/lib/bx/plugins' '_VERSION_=BitchX' 'VERSION=BitchX-1.1-final' 'INSTALL_DATA=/usr/bin/install -c -m 644' 'INSTALL_SCRIPT=/usr/local/lib/bx/script' 'EXEEXT=' 'SHLIB_CFLAGS=' 'SHLIB_SUFFIX=.so' all
make[1]: Entering directory `/root/BitchX/source'
gcc -I. -I/root/BitchX/include -I../include -I. -I./include -g -O2 -Wall -c ctcp.c
ctcp.c:179: error: static declaration of &#915;Çÿctcp_type&#915;ÇÖ follows non-static declaration
/root/BitchX/include/ctcp.h:59: error: previous declaration of &#915;Çÿctcp_type&#915;ÇÖ was here
ctcp.c: In function &#915;Çÿdo_version&#915;ÇÖ:
ctcp.c:896: warning: pointer targets in passing argument 1 of &#915;Çÿstripansicodes&#915;ÇÖ differ in signedness
ctcp.c: In function &#915;Çÿdo_notice_ctcp&#915;ÇÖ:
ctcp.c:1367: warning: pointer targets in passing argument 1 of &#915;Çÿstripansi&#915;ÇÖ differ in signedness
make[1]: *** [ctcp.o] Error 1
make[1]: Leaving directory `/root/BitchX/source'
make: *** [BitchX] Error 2

```

by the way. all the weird looking characters displayed on my terminal should be in english. not sure why it's in 'jibberish' 

any idea? i think i have everything installed for it that i should

bitchx is in the repositories.

open a terminal
cantormath-laptop:~$ sudo apt-get update
cantormath-laptop:~$ sudo apt-get install bitchx

if you dont find it, open up the Universe repo and it should show up.
There is also a bitchx-gtk, but you are on server install.

---

### Post by fooey on 2006-08-04
thankyou. that worked w/ the universe repositories. :D

---

