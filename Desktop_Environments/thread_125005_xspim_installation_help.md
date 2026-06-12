---
title: "xspim installation help"
date: 2006-02-02
forum: Desktop Environments
---

### Post by RavenndudE on 2006-02-02
I'm trying to compile the graphical version of [spim]("http://www.cs.wisc.edu/~larus/spim.html") (named xspim) (its a MIPS asslmbly language simulator for those who don't know) on my ubuntu laptop so I can take it to class instead of using the shitty lab PCs (plus homework).

I downloaded the source and followed the instructions at the bottom of the page and I get this error when I $sudo make

```
$ sudo make
make[1]: Entering directory `/home/ravenndude/.spim/spim-7.2.1/xspim'
bison -y -d ../CPU/parser.y
conflicts: 25 shift/reduce
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o spim-utils.o ../CPU/spim-utils.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o run.o ../CPU/run.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o mem.o ../CPU/mem.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o inst.o ../CPU/inst.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o data.o ../CPU/data.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o sym-tbl.o ../CPU/sym-tbl.c
gcc -m32  -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                              -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""   -c y.tab.c
flex -I -8 ../CPU/scanner.l
gcc -m32  -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                              -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""  -O -c lex.yy.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o syscall.o ../CPU/syscall.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o display-utils.o ../CPU/display-utils.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o string-stream.o ../CPU/string-stream.c
gcc -m32 -g    -I. -I../CPU  -I/usr/X11R6/include    -Dlinux -D__i386__ -D_POSIX_C_SOURCE=199309L                               -D_POSIX_SOURCE -D_XOPEN_SOURCE-D_BSD_SOURCE -D_SVID_SOURCE  -DFUNCPROTO=15 -DNARROWPROTO   `cat configuration` -DTEXT_SIZE=65536 -DDATA_SIZE=131072 -DK_TEXT_SIZE=65536 -DDEFAULT_EXCEPTION_HANDLER=\"home/ravenndude/.spim/exceptions.s\" -DSPIM_VERSION="\"`cat ../VERSION`\""    -c -o xspim.o xspim.c
xspim.c:35:31: error: X11/Xaw/Cardinals.h: No such file or directory
xspim.c:36:27: error: X11/Xaw/Paned.h: No such file or directory
xspim.c:37:31: error: X11/Xaw/AsciiText.h: No such file or directory
xspim.c:38:26: error: X11/Xaw/Text.h: No such file or directory
xspim.c:39:28: error: X11/Xaw/Dialog.h: No such file or directory
xspim.c: In function ‘create_console_display’:
xspim.c:387: error: ‘XawtextAppend’ undeclared (first use in this function)
xspim.c:387: error: (Each undeclared identifier is reported only once
xspim.c:387: error: for each function it appears in.)
xspim.c:388: error: ‘XtNscrollVertical’ undeclared (first use in this function)
xspim.c:388: error: ‘XawtextScrollWhenNeeded’ undeclared (first use in this function)
xspim.c:389: error: ‘XtNpreferredPaneSize’ undeclared (first use in this function)
xspim.c:391: error: ‘asciiTextWidgetClass’ undeclared (first use in this function)
xspim.c: In function ‘main’:
xspim.c:419: error: ‘ZERO’ undeclared (first use in this function)
xspim.c:444: error: ‘panedWidgetClass’ undeclared (first use in this function)
xspim.c: In function ‘show_running’:
xspim.c:612: error: ‘ONE’ undeclared (first use in this function)
xspim.c: In function ‘display_registers’:
xspim.c:641: error: ‘TWO’ undeclared (first use in this function)
xspim.c: In function ‘redisplay_text’:
xspim.c:664: error: ‘TWO’ undeclared (first use in this function)
xspim.c: In function ‘center_text_at_PC’:
xspim.c:677: error: ‘XawTextBlock’ undeclared (first use in this function)
xspim.c:677: error: syntax error before ‘text’
xspim.c:678: error: ‘XawTextPosition’ undeclared (first use in this function)
xspim.c:687: error: ‘text’ undeclared (first use in this function)
xspim.c:690: error: ‘FMT8BIT’ undeclared (first use in this function)
xspim.c:693: error: ‘start’ undeclared (first use in this function)
xspim.c:693: error: ‘XawsdRight’ undeclared (first use in this function)
xspim.c:693: error: ‘XawsdLeft’ undeclared (first use in this function)
xspim.c:696: error: ‘XawTextSearchError’ undeclared (first use in this function)xspim.c:713: error: ‘finish’ undeclared (first use in this function)
xspim.c: In function ‘display_data_seg’:
xspim.c:741: error: ‘TWO’ undeclared (first use in this function)
xspim.c: In function ‘write_text_to_window’:
xspim.c:971: error: ‘XawTextBlock’ undeclared (first use in this function)
xspim.c:971: error: syntax error before ‘textblock’
xspim.c:972: error: ‘XawTextPosition’ undeclared (first use in this function)
xspim.c:976: error: ‘textblock’ undeclared (first use in this function)
xspim.c:979: error: ‘FMT8BIT’ undeclared (first use in this function)
xspim.c:981: error: ‘ip’ undeclared (first use in this function)
make[1]: *** [xspim.o] Error 1
make[1]: Leaving directory `/home/ravenndude/.spim/spim-7.2.1/xspim'
make: *** [xspim] Error 2
```

I tried to use the RPM, but when I made the .deb file it was locked, and I have no idea what to do about that and could not %dpkg -i the file.

any help?

---

### Post by RavenndudE on 2006-02-03
bump

anyone?

---

### Post by jermor on 2006-02-20
I had a similar problem.  ./configure isn't really adequate for xspim, so you might be missing some dependencies.  I'm not sure if this will completely solve the problem, but it's easy so probably worth a try.  This is a list of what I had to install to build xspim:

byacc
flex
bison
libx11-dev
libxaw7-dev

You can use the search function in the synaptic package manager to find everything.

---

### Post by firest0rm on 2007-02-20
Thanks a million, jermor.  Installing those packages worked for me ^_^

---

