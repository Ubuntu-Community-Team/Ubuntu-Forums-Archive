---
title: "can't install xfig 3.2.4"
date: 2005-12-30
forum: General Help
---

### Post by bigblop on 2005-12-30
I can only install 3.2.5 through synaptic, but it does not work correct so I am trying to install 3.2.4.

I have downloaded xfig 3.2.4.full.tar.gz from:

[http://xfig.org/art2.html](http://xfig.org/art2.html)

I have then tried to type  "make" in the extracted dir but I get this error:

[email]mos@ubuntu:~/apps/xfig.3.2.4.full[/email]/xfig.3.2.4$ make
rm -f d_text.o
gcc -m32 -c -g -O2 -fno-strict-aliasing     -I/usr/include/X11
-I/usr/local/include   -I/usr/X11R6/include    -Dlinux -D__i386__
-D_POSIX_C_SOURCE=199309L                              -D_POSIX_SOURCE
-D_XOPEN_SOURCE                                 -D_BSD_SOURCE
-D_SVID_SOURCE                                   -DFUNCPROTO=15
-DNARROWPROTO                                                                         
-DUSE_JPEG -DI18N -DSETLOCALE                        d_text.c
In file included from d_text.c:26:
u_fonts.h:35: error: array type has incomplete element type
u_fonts.h:35: error: array type has incomplete element type
u_fonts.h:36: error: array type has incomplete element type
u_fonts.h:37: error: array type has incomplete element type
make: *** [d_text.o] Error 1
[email]mos@ubuntu:~/apps/xfig.3.2.4.full[/email]/xfig.3.2.4$

Any ideas on what is wrong and how to fix it??

---

