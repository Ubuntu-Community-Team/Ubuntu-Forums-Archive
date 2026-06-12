---
title: "how to install documentation of standard C function?"
date: 2006-09-19
forum: Desktop Environments
---

### Post by damien.yep on 2006-09-19
Hi everybody!

I would like to install documentation of standard C function (like printf, fopen, ....), but I can't find on which package it is.
:?: Can you tel me which one I should install?

I also want to install GTK, but I can't compile, I had some strange error like as if it was looking into the wrong folder: It was searching for /usr/include/gtk and /usr/include/gdk. But I didn't had those folder, I have /usr/include/gtk-2.0/gtk/ and /usr/include/gtk-2.0/gdk/. So I made some links to those folder via "ln -s ...".

And now, when I compile, I have some more errors, but different:
```

Dans le fichier inclus à partir de /usr/include/gdk/gdkcairo.h:23,
          à partir de /usr/include/gdk/gdk.h:30,
          à partir de /usr/include/gtk/gtk.h:31,
          à partir de MyProg.c:2:
/usr/include/gdk/gdkcolor.h:30:19: erreur: cairo.h : Aucun fichier ou répertoire de ce type
Dans le fichier inclus à partir de /usr/include/gdk/gdkcolor.h:31,
          à partir de /usr/include/gdk/gdkcairo.h:23,
          à partir de /usr/include/gdk/gdk.h:30,
          à partir de /usr/include/gtk/gtk.h:31,
          à partir de MyProg.c:2:
/usr/include/gdk/gdktypes.h:32:18: erreur: glib.h : Aucun fichier ou répertoire de ce type
/usr/include/gdk/gdktypes.h:33:25: erreur: pango/pango.h : Aucun fichier ou répertoire de ce type
/usr/include/gdk/gdktypes.h:34:25: erreur: glib-object.h : Aucun fichier ou répertoire de ce type
/usr/include/gdk/gdktypes.h:51:23: erreur: gdkconfig.h : Aucun fichier ou répertoire de ce type
In file included from /usr/include/gdk/gdkcolor.h:31,
                 from /usr/include/gdk/gdkcairo.h:23,
                 from /usr/include/gdk/gdk.h:30,
                 from /usr/include/gtk/gtk.h:31,
                 from MyProg.c:2:
/usr/include/gdk/gdktypes.h:64: erreur: syntax error before «typedef»
/usr/include/gdk/gdktypes.h:74: erreur: syntax error before «GdkWChar»
/usr/include/gdk/gdktypes.h:87: erreur: syntax error before «GdkNativeWindow»
[...]

```

inside /usr/include/gdk/gdkcolor.h I have:
```

#ifndef __GDK_COLOR_H__
#define __GDK_COLOR_H__

#include <cairo.h>
#include <gdk/gdktypes.h>

```

but cairo.h is not inside /usr/include/gdk/ nor /usr/include/ but in /usr/include/cairo/
It seams all my paths are wrong, :?: what whould I do to correct this??


Thanks for your help!
Damien.

---

### Post by tatimmer on 2006-09-19
apt-get install manpages-dev

---

### Post by damien.yep on 2006-09-19
Thanks tatimmer for the package name, at last I have man for standard C function!! :D

:?: Does anybody have some ideas about my Gtk problem (how to setup path / make a clean install)?

Thanks!
Damien.

---

