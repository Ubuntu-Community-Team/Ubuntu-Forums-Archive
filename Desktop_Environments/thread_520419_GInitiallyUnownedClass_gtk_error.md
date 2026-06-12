---
title: "GInitiallyUnownedClass gtk error"
date: 2007-08-08
forum: Desktop Environments
---

### Post by arnab.bhaumik on 2007-08-08
hi all,


    everytime i am trying to compile a gtk application with make  i am getting "GInitiallyUnownedClass" error . even with glade generated code. i checked my system and found gtk1 and gtk2 both.


      giving the complete error code........................ looking gor suggestion...........................



arnab@abtelecomm:~/download/pcb-20070208p1$ make
make  all-recursive
make[1]: Entering directory `/home/arnab/download/pcb-20070208p1'
Making all in win32
make[2]: Entering directory `/home/arnab/download/pcb-20070208p1/win32'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/arnab/download/pcb-20070208p1/win32'
Making all in src
make[2]: Entering directory `/home/arnab/download/pcb-20070208p1/src'
make  all-recursive
make[3]: Entering directory `/home/arnab/download/pcb-20070208p1/src'
Making all in icons
make[4]: Entering directory `/home/arnab/download/pcb-20070208p1/src/icons'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/arnab/download/pcb-20070208p1/src/icons'
make[4]: Entering directory `/home/arnab/download/pcb-20070208p1/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I.. -I./icons -I./hid/gtk -I/usr/include -DPREFIXDIR=\"/usr/local\" -DBINDIR=\"/usr/local/bin\" -DHOST=\"x86_64-unknown-linux-gnu\" -DPCBLIBDIR=\"/usr/local/share/pcb\" -DPCBTREEDIR=\"/usr/local/share/pcb/newlib\" -DPCBTREEPATH=\"/usr/local/share/pcb/newlib:/usr/local/share/pcb/pcblib-newlib\" -DNDEBUG -g -O2 -I/usr/include   -DPNG_NO_MMX_CODE -I/usr/local/include/atk-1.0 -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/libpng12   -Wall -MT hid/gtk/libgtk_a-gtkhid-main.o -MD -MP -MF "hid/gtk/.deps/libgtk_a-gtkhid-main.Tpo" -c -o hid/gtk/libgtk_a-gtkhid-main.o `test -f 'hid/gtk/gtkhid-main.c' || echo './'`hid/gtk/gtkhid-main.c; \
        then mv -f "hid/gtk/.deps/libgtk_a-gtkhid-main.Tpo" "hid/gtk/.deps/libgtk_a-gtkhid-main.Po"; else rm -f "hid/gtk/.deps/libgtk_a-gtkhid-main.Tpo"; exit 1; fi
In file included from /usr/include/gtk-2.0/gtk/gtkwidget.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkcontainer.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkbin.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkwindow.h:33,
                 from /usr/include/gtk-2.0/gtk/gtkdialog.h:32,
                 from /usr/include/gtk-2.0/gtk/gtkaboutdialog.h:28,
                 from /usr/include/gtk-2.0/gtk/gtk.h:32,
                 from hid/gtk/gui.h:36,
                 from hid/gtk/gtkhid-main.c:24:
/usr/include/gtk-2.0/gtk/gtkobject.h:85: error: expected specifier-qualifier-list before ‘GInitiallyUnowned’
/usr/include/gtk-2.0/gtk/gtkobject.h:97: error: expected specifier-qualifier-list before ‘GInitiallyUnownedClass’
make[4]: *** [hid/gtk/libgtk_a-gtkhid-main.o] Error 1
make[4]: Leaving directory `/home/arnab/download/pcb-20070208p1/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/arnab/download/pcb-20070208p1/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/arnab/download/pcb-20070208p1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/arnab/download/pcb-20070208p1'
make: *** [all] Error 2
arnab@abtelecomm:~/download/pcb-20070208p1$ 


arnab/vu2bpw

---

### Post by Senthooran Kularajasingha on 2008-01-02
I got this problem while I was compiling goffice under glib 2.9 and after spending numerous hours debugging the source i found out it was due to the glib version.  I downloaded the latest verson of glib 2.12.3 and compiled & installed and that resolved it!

after you updated glib, check if that has been loaded by typing: pkg-config --modversion glib-2.0

I hope this helps

---

