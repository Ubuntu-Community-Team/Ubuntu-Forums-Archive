---
title: "What happened to soundtracker"
date: 2010-12-22
forum: Desktop Environments
---

### Post by jz1977 on 2010-12-22
Is there any way to install this on ubuntu 10?

There is no "soundtracker" in any synaptic package manager repo.

Trying to build the GTK2 port from here
[http://www.soundtracker.org/links.php](http://www.soundtracker.org/links.php)
Fails with

```

    then mv -f ".deps/xm-player.Tpo" ".deps/xm-player.Po"; else rm -f ".deps/xm-player.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\"    -g -O2 -Wall -DORBIT2=1 -pthread -D_REENTRANT -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/libxml2 -I/usr/include/pango-1.0 -I/usr/include/gail-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/gio-unix-2.0/ -I/usr/include/pixman-1 -I/usr/include/directfb -I/usr/include/libpng12   -pthread -D_REENTRANT -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12   -pthread -I/usr/include/gtk-2.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include      -MT entry-workaround.o -MD -MP -MF ".deps/entry-workaround.Tpo" -c -o entry-workaround.o entry-workaround.c; \
    then mv -f ".deps/entry-workaround.Tpo" ".deps/entry-workaround.Po"; else rm -f ".deps/entry-workaround.Tpo"; exit 1; fi
entry-workaround.c: In function ‘gtk_entry_create_layout’:
entry-workaround.c:338: error: ‘GtkEntry’ has no member named ‘n_bytes’
entry-workaround.c:347: error: ‘GtkEntry’ has no member named ‘n_bytes’
entry-workaround.c:382: error: ‘GtkEntry’ has no member named ‘n_bytes’
entry-workaround.c:416: error: ‘GtkEntry’ has no member named ‘n_bytes’
entry-workaround.c: In function ‘wa_entry_set_text’:
entry-workaround.c:749: error: ‘GtkEntry’ has no member named ‘n_bytes’
make[3]: *** [entry-workaround.o] Error 1


```

---

### Post by hhh on 2010-12-22
The software is pretty outdated (last updated in 2006) and it hasn't been in the Ubuntu repositories since Hardy. Still, you can download the deb from that repo (scroll to the bottom and choose your architecture)...
[http://packages.ubuntu.com/en/hardy/soundtracker](http://packages.ubuntu.com/en/hardy/soundtracker)

-edit- You might want to look into this as it's more recent, there is an Ubuntu deb...
[http://milkytracker.org/?about](http://milkytracker.org/?about)
[http://packages.ubuntu.com/search?keywords=milkytracker](http://packages.ubuntu.com/search?keywords=milkytracker)

---

### Post by jz1977 on 2011-01-06
Sorry for the late reply, I've been away.
Milkytracker looks good, I'll give that a try.

---

### Post by jz1977 on 2011-01-06
Despite it's age, soundtracker still had better features :(
Unless I am missing something, I cannot seem to record a sample from within milkytracker. Let alone recording while doing playback.

---

