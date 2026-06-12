---
title: "libgtk issue - I can no longer open any xwindows that use gtk"
date: 2007-12-11
forum: Desktop Environments
---

### Post by mandark333 on 2007-12-11
For some reason I am not sure of, I can no longer launch any of my installed programs w/o this error message:

abdel@BUSAB-137:~$ vmware
/usr/lib/vmware/bin/vmware: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_threads_add_idle
abdel@BUSAB-137:~$ /usr/lib/vmware/bin/vmware-tray: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_threads_add_idle_full

abdel@BUSAB-137:~$ scatterchat
scatterchat: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_threads_add_idle
abdel@BUSAB-137:~$ pidgin
pidgin: symbol lookup error: /usr/lib/libgtk-x11-2.0.so.0: undefined symbol: gdk_threads_add_idle
abdel@BUSAB-137:~$

this one has be stumped, any ideas?  thanks!

---

### Post by mandark333 on 2007-12-11
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"Gtk\" -DGTK_LIBDIR=\"/usr/local/lib\" -DGTK_DATADIR=\"/usr/local/share\" -DGTK_DATA_PREFIX=\"/usr/local\" -DGTK_SYSCONFDIR=\"/usr/local/etc\" -DGTK_VERSION=\"2.10.9\" -DGTK_BINARY_VERSION=\"2.10.0\" -DGTK_HOST=\"i686-pc-linux-gnu\" -DGTK_COMPILATION -DGTK_PRINT_BACKENDS=\"file,cups\" "-DGTK_PRINT_PREVIEW_COMMAND=\"evince --preview %f\"" -I../gtk -I.. -I../gdk -I../gdk -I../gdk-pixbuf -I../gdk-pixbuf -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_FILE_SYSTEM_ENABLE_UNSUPPORTED -DGTK_PRINT_BACKEND_ENABLE_UNSUPPORTED -DG_DISABLE_CAST_CHECKS -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -g -O2 -Wall -MT gtkiconcache.lo -MD -MP -MF .deps/gtkiconcache.Tpo -c gtkiconcache.c  -fPIC -DPIC -o .libs/gtkiconcache.o
gtkiconcache.c: In function '_gtk_icon_cache_get_icon':
gtkiconcache.c:444: warning: pointer targets in passing argument 3 of 'gdk_pixdata_deserialize' differ in signedness
if /bin/bash ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"Gtk\" -DGTK_LIBDIR=\"/usr/local/lib\" -DGTK_DATADIR=\"/usr/local/share\" -DGTK_DATA_PREFIX=\"/usr/local\" -DGTK_SYSCONFDIR=\"/usr/local/etc\" -DGTK_VERSION=\"2.10.9\" -DGTK_BINARY_VERSION=\"2.10.0\" -DGTK_HOST=\"i686-pc-linux-gnu\" -DGTK_COMPILATION -DGTK_PRINT_BACKENDS=\"file,cups\" -DGTK_PRINT_PREVIEW_COMMAND=\""evince --preview %f"\" -I../gtk -I.. -I../gdk -I../gdk -I../gdk-pixbuf -I../gdk-pixbuf -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_FILE_SYSTEM_ENABLE_UNSUPPORTED -DGTK_PRINT_BACKEND_ENABLE_UNSUPPORTED -DG_DISABLE_CAST_CHECKS -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0          -g -O2 -Wall -MT gtkiconfactory.lo -MD -MP -MF ".deps/gtkiconfactory.Tpo" \
          -c -o gtkiconfactory.lo `test -f 'gtkiconfactory.c' || echo './'`gtkiconfactory.c; \
        then mv -f ".deps/gtkiconfactory.Tpo" ".deps/gtkiconfactory.Plo"; \
        else rm -f ".deps/gtkiconfactory.Tpo"; exit 1; \
        fi
 gcc -DHAVE_CONFIG_H -I. -I. -I.. -DG_LOG_DOMAIN=\"Gtk\" -DGTK_LIBDIR=\"/usr/local/lib\" -DGTK_DATADIR=\"/usr/local/share\" -DGTK_DATA_PREFIX=\"/usr/local\" -DGTK_SYSCONFDIR=\"/usr/local/etc\" -DGTK_VERSION=\"2.10.9\" -DGTK_BINARY_VERSION=\"2.10.0\" -DGTK_HOST=\"i686-pc-linux-gnu\" -DGTK_COMPILATION -DGTK_PRINT_BACKENDS=\"file,cups\" "-DGTK_PRINT_PREVIEW_COMMAND=\"evince --preview %f\"" -I../gtk -I.. -I../gdk -I../gdk -I../gdk-pixbuf -I../gdk-pixbuf -DGDK_PIXBUF_DISABLE_DEPRECATED -DGDK_DISABLE_DEPRECATED -DGTK_FILE_SYSTEM_ENABLE_UNSUPPORTED -DGTK_PRINT_BACKEND_ENABLE_UNSUPPORTED -DG_DISABLE_CAST_CHECKS -pthread -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/atk-1.0 -g -O2 -Wall -MT gtkiconfactory.lo -MD -MP -MF .deps/gtkiconfactory.Tpo -c gtkiconfactory.c  -fPIC -DPIC -o .libs/gtkiconfactory.o
gtkiconfactory.c:2671: error: conflicting types for 'g_hash_table_get_keys'
/usr/include/glib-2.0/glib/ghash.h:81: error: previous declaration of 'g_hash_table_get_keys' was here
make[3]: *** [gtkiconfactory.lo] Error 1
make[3]: Leaving directory `/home/abdel/gtk+-2.10.9/gtk'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/abdel/gtk+-2.10.9/gtk'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/abdel/gtk+-2.10.9/gtk'
make: *** [install-recursive] Error 1
root@BUSAB-137:/home/abdel/gtk+-2.10.9#

---

### Post by mandark333 on 2007-12-11
this link appears relevant, but its for SUSE

[http://www.suseforums.net/index.php?showtopic=25764&mode=linearplus](http://www.suseforums.net/index.php?showtopic=25764&mode=linearplus)

---

