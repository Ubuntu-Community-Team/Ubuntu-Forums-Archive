---
title: "make is broken"
date: 2006-03-09
forum: Desktop Environments
---

### Post by %hMa@?b&lt;C on 2006-03-09
when i try to do the usual make, make install stuff, i get this output
```
crowell@ubuntu:~/ops-for-linux$ make
cc -c -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -fno-common -ffast-math -W -Wall -Wshadow -Wcast-align -Wredundant-decls -Wbad-function-cast -Wcast-qual -Wwrite-strings -Waggregate-return -Wstrict-prototypes -Wmissing-prototypes -O2 -s       file_dialog.c -o file_dialog.o
In file included from /usr/include/gtk-2.0/gtk/gtkactiongroup.h:34,
                 from /usr/include/gtk-2.0/gtk/gtk.h:38,
                 from ops-linux.h:55,
                 from file_dialog.c:1:
/usr/include/gtk-2.0/gtk/gtkitemfactory.h:50: warning: function declaration isn’t a prototype
In file included from file_dialog.c:1:
ops-linux.h:56:17: error: usb.h: No such file or directory
In file included from file_dialog.c:1:
ops-linux.h:210: error: syntax error before ‘*’ token
ops-linux.h:210: warning: type defaults to ‘int’ in declaration of ‘m_p_handle’
ops-linux.h:210: warning: data definition has no type or storage class
file_dialog.c:12: warning: no previous prototype for ‘file_selection_ok’
file_dialog.c: In function ‘file_selection_ok’:
file_dialog.c:11: warning: unused parameter ‘widget’
file_dialog.c: At top level:
file_dialog.c:21: warning: no previous prototype for ‘store_filename’
file_dialog.c: In function ‘get_filename_from_dialog’:
file_dialog.c:32: warning: unused variable ‘ret_val’
file_dialog.c: At top level:
file_dialog.c:108: warning: function declaration isn’t a prototype
make: *** [file_dialog.o] Error 1

```

---

### Post by lamego on 2006-03-09
You are missing some library required for the program you are trying to compile.
Just read the documentation that comes with it....

---

