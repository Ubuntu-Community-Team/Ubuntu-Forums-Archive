---
title: "rhythmbox wont compile - dbus error?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by puccaso on 2006-09-28
ok, i actually use edgy, but i thought more people would respond on this forum, and i wonder if others have the same issue.

i'm trying to compile rhythmbox, because i want to see how fast the bg database will opperate with sqlite/libgda as apposed to tree...

but i get this error..

my compile args are as follows

```
mahir@jt:~/Documents/Downloads/rhythmbox-0.9.5$ CC=gcc-4.1 ./configure --prefix=/usr --with-database=libgda --enable-ipod-writing --enable-tag-writing --disable-scrollkeeper

```

and the output

(alot of previous xterm output has been left out
it'd be too long)

```
    Successfully remade target file `rb-metadata-dbus-service.o'.
  Must remake target `rhythmbox-metadata'.
/bin/sh ../libtool --mode=link gcc-4.1  -g -O2   -o rhythmbox-metadata  rb-metadata-dbus-service.o ../metadata/librbmetadatasvc.la ../lib/librb.la -pthread -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnome-keyring -lgnomecanvas-2 -lgnome-2 -lpopt -lart_lgpl_2 -lpangoft2-1.0 -lbonobo-2 -lbonobo-activation -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgnomevfs-2 -lgconf-2 -lgobject-2.0 -lORBit-2 -lm -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0   -Wl,--export-dynamic -pthread -lgstbase-0.10 -lgstreamer-0.10 -lgobject-2.0 -lgmodule-2.0 -ldl -lgthread-2.0 -lxml2 -lglib-2.0   -lmusicbrainz   -ldbus-glib-1 -ldbus-1 -lglib-2.0   -L/usr/X11R6/lib
gcc-4.1 -g -O2 -o rhythmbox-metadata rb-metadata-dbus-service.o -pthread -Wl,--export-dynamic -pthread  ../metadata/.libs/librbmetadatasvc.a -L/usr/X11R6/lib ../lib/.libs/librb.a /usr/lib/libgnomeui-2.so -lSM -lICE /usr/lib/libbonoboui-2.so /usr/lib/libgnome-keyring.so /usr/lib/libgnomecanvas-2.so /usr/lib/libgnome-2.so /usr/lib/libpopt.so /usr/lib/libart_lgpl_2.so /usr/lib/libpangoft2-1.0.so /usr/lib/libbonobo-2.so /usr/lib/libbonobo-activation.so /usr/lib/libglade-2.0.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so -lX11 /usr/lib/libgnomevfs-2.so /usr/lib/libgconf-2.so /usr/lib/libORBit-2.so -lm /usr/lib/libgstbase-0.10.so /usr/lib/libgstreamer-0.10.so /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libgthread-2.0.so /usr/lib/libxml2.so /usr/lib/libmusicbrainz.so -ldbus-glib-1 -ldbus-1 /usr/lib/libglib-2.0.so
rb-metadata-dbus-service.o: In function `main':
/home/mahir/Documents/Downloads/rhythmbox-0.9.5/metadata/rb-metadata-dbus-service.c:497: undefined reference to `dbus_connection_disconnect'
collect2: ld returned 1 exit status
make[4]: *** [rhythmbox-metadata] Error 1
make[4]: Leaving directory `/home/mahir/Documents/Downloads/rhythmbox-0.9.5/metadata'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/mahir/Documents/Downloads/rhythmbox-0.9.5/metadata'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/mahir/Documents/Downloads/rhythmbox-0.9.5/metadata'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mahir/Documents/Downloads/rhythmbox-0.9.5'
make: *** [all] Error 2

```



what could this problem be?

---

### Post by marcantonio on 2006-12-26
It should be as simple as replacing any occur occurrence of:

```
dbus_connection_disconnect
```

with:
```
dbus_connection_close
```

in the code.

-Marc

---

