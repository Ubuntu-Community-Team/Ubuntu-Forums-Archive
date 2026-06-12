---
title: "Could somebody please help me figure out what's going wrong with this make?"
date: 2009-05-13
forum: General Help
---

### Post by josephellengar on 2009-05-13
I'm trying to compile notify-osd for ibex, but I keep getting make error 2.  Here is the terminal output when I do it:

ross@ross-laptop:~/notify-osd$ sudo make
make  all-recursive
make[1]: Entering directory `/home/ross/notify-osd'
Making all in src
make[2]: Entering directory `/home/ross/notify-osd/src'
make  all-am
make[3]: Entering directory `/home/ross/notify-osd/src'
gcc -DHAVE_CONFIG_H -I. -I.. -I. -I.    -DDATADIR=\""/usr/local/share"\"   -pthread -DORBIT2=1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libwnck-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/startup-notification-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0    -g -O2 -lm -Wall -Werror -std=c99 -MT notify_osd-bubble.o -MD -MP -MF .deps/notify_osd-bubble.Tpo -c -o notify_osd-bubble.o `test -f 'bubble.c' || echo './'`bubble.c
In file included from /usr/include/gtk-2.0/gtk/gtk.h:68,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:36:25: error: gtk/gtkvbox.h: No such file or directory
In file included from /usr/include/gtk-2.0/gtk/gtk.h:68,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:60: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:68: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:88,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:46: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:53: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:91,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkfontsel.h:69: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkfontsel.h:94: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:93,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkgamma.h:64: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkgamma.h:77: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:150,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:48: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:55: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from bubble.c:3468:
dialog.c: In function 'bubble_show_dialog':
dialog.c:192: error: 'GTK_TYPE_VBOX' undeclared (first use in this function)
dialog.c:192: error: (Each undeclared identifier is reported only once
dialog.c:192: error: for each function it appears in.)
make[3]: *** [notify_osd-bubble.o] Error 1
make[3]: Leaving directory `/home/ross/notify-osd/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ross/notify-osd/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ross/notify-osd'
make: *** [all] Error 2

---

### Post by Fixman on 2009-05-13
```
sudo aptitude install libgtk2.0-dev
```

---

### Post by josephellengar on 2009-05-13
> **Fixman said:**
> ```
sudo aptitude install libgtk2.0-dev
```
Thanks, but it still didn't work:

ross@ross-laptop:~/notify-osd$ sudo make
make  all-recursive
make[1]: Entering directory `/home/ross/notify-osd'
Making all in src
make[2]: Entering directory `/home/ross/notify-osd/src'
make  all-am
make[3]: Entering directory `/home/ross/notify-osd/src'
gcc -DHAVE_CONFIG_H -I. -I.. -I. -I.    -DDATADIR=\""/usr/local/share"\"   -pthread -DORBIT2=1 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -DORBIT2=1 -pthread -I/usr/include/gconf/2 -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -I/usr/include/libwnck-1.0 -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/startup-notification-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0    -g -O2 -lm -Wall -Werror -std=c99 -MT notify_osd-bubble.o -MD -MP -MF .deps/notify_osd-bubble.Tpo -c -o notify_osd-bubble.o `test -f 'bubble.c' || echo './'`bubble.c
In file included from /usr/include/gtk-2.0/gtk/gtk.h:68,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:36:25: error: gtk/gtkvbox.h: No such file or directory
In file included from /usr/include/gtk-2.0/gtk/gtk.h:68,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:60: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkcolorsel.h:68: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:88,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:46: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkfilechooserwidget.h:53: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:91,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkfontsel.h:69: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkfontsel.h:94: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:93,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkgamma.h:64: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkgamma.h:77: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from /usr/include/gtk-2.0/gtk/gtk.h:150,
                 from bubble.c:36:
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:48: error: expected specifier-qualifier-list before 'GtkVBox'
/usr/include/gtk-2.0/gtk/gtkrecentchooserwidget.h:55: error: expected specifier-qualifier-list before 'GtkVBoxClass'
In file included from bubble.c:3468:
dialog.c: In function 'bubble_show_dialog':
dialog.c:192: error: 'GTK_TYPE_VBOX' undeclared (first use in this function)
dialog.c:192: error: (Each undeclared identifier is reported only once
dialog.c:192: error: for each function it appears in.)
make[3]: *** [notify_osd-bubble.o] Error 1
make[3]: Leaving directory `/home/ross/notify-osd/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/ross/notify-osd/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ross/notify-osd'
make: *** [all] Error 2

---

### Post by petrus4 on 2009-05-13
Welcome to Hell, also known as binary subpackaging.

The easiest option would be to simply try and download the dev version of the package you want, and then reboot to ensure it works, even though under a sane distribution you wouldn't need to; you could simply use

```
sudo ldconfig -v
```

to refresh the lib cache.

If that doesn't work, I will give you links to let you download the [source]("ftp://ftp.gnome.org/pub/gimp/gtk/v2.0/") tarball of GTK, and a [deb]("http://mirrors.xmission.com/ubuntu/pool/universe/g/gtk+2.0/gtk2.0-examples_2.16.1-0ubuntu2_i386.deb") package of gtk+-2.0-examples which you can break open with ar in order to use the recipe file from that as a template for compiling a non-subpackaged version of lib-gtk.

Of course, this being the Ubuntu forum, I have no idea whether you're sufficiently competent to be able to do the above or not; you'll have to decide that for yourself.

---

