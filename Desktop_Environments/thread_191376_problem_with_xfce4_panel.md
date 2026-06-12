---
title: "problem with xfce4 panel"
date: 2006-06-07
forum: Desktop Environments
---

### Post by kariopto on 2006-06-07
Hi, I just installed Dapper and I think it's great!, but I have 2 small problems:
1: I'm trying to compile xfce4-xmms-plugin, but I get:
```

checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking for pango >= 1.8.0... yes
checking PANGO_CFLAGS... -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include  
checking PANGO_LIBS... -lpango-1.0 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0  
checking for xfce4-panel-1.0 >= 4.0.0... Package xfce4-panel-1.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `xfce4-panel-1.0.pc' to the PKG_CONFIG_PATH environment variable No package 'xfce4-panel-1.0' found
configure: error: Library requirements (xfce4-panel-1.0 >= 4.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

```
I have xfce4-panel and xfce4-panel-dev installed... any ideas?

2: I added the volume control plugin, and it works fine, but it has the office icon instead of the speaker icon, and I can't find where to change it..

Thanks a lot in advance!

---

### Post by kaamos on 2006-06-07
edit: nevermind. ;)

---

### Post by kariopto on 2006-06-07
Any ideas with 1??
I already installed xfce4-dev and all the libxfce4*.. and still the same error...

---

