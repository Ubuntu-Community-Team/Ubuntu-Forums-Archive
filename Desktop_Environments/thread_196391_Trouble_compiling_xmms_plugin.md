---
title: "Trouble compiling xmms plugin"
date: 2006-06-14
forum: Desktop Environments
---

### Post by Quoth the raven on 2006-06-14
When I'm trying to compile the xmms musepack plugin on 6.06 I get the following error: (I typed in "./configure && make", and I have build-essential and xmms-dev installed):
```

[about 100 lines of ./configure output]
checking for an ANSI C-conforming const... yes
checking for off_t... yes
checking for size_t... yes
checking for xmms-config... /usr/bin/xmms-config
checking for gawk... (cached) gawk
checking for XMMS - version >= 1.2.10... yes
checking for pkg-config... /usr/bin/pkg-config
checking for gtk+ >= 1.2.2... yes
checking GTK_CFLAGS... -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include
checking GTK_LIBS... -lgtk -lgdk -lXi -lXext -lX11 -lm -lglib
checking for glib >= 1.2.10... yes
checking GLIB_CFLAGS... -I/usr/include/glib-1.2 -I/usr/lib/glib/include
checking GLIB_LIBS... -lglib
checking mpcdec/config_types.h usability... yes
checking mpcdec/config_types.h presence... yes
checking for mpcdec/config_types.h... yes
checking for taglib-config... no
configure: error: *** Taglib not installed - please install first

```
Can anyone tell me what taglib or taglib-config is and how to install it (or how I can get this stupid thing to compile)? Thanks.

---

### Post by dabang on 2006-06-14
I guess you have to install "libtag1-dev" and/or "libtagc0-dev".

---

### Post by Quoth the raven on 2006-06-14
[QUOTE=dabang]I guess you have to install "libtag1-dev" and/or "libtagc0-dev".[/QUOTE]
Problem solved - found the xmms-musepack package in synaptic :rolleyes:.

---

