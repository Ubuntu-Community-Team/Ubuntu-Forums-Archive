---
title: "Errors when compiling openvrml on Ubuntu 11.04"
date: 2011-06-07
forum: Desktop Environments
---

### Post by matse on 2011-06-07
Hi everybody. 
I got stuck now for a long time having problems to compile the openvrml software on my Ubuntu 11.04. I donwloaded openvrml 0.18.8, configured it successfully. But when I try to make it, it comes up with these error messages:

libtool: link: g++ -pthread -DORBIT2=1 -D_REENTRANT -I/usr/local/include/libxml2 -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -I/usr/include/pango-1.0 -I/usr/include/freetype2 -I/usr/include/atk-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/libpng12 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-keyring-1 -I/usr/include/libgnome-2.0 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gtk-2.0 -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/orbit-2.0 -I/usr/include/libbonobo-2.0 -I/usr/include/bonobo-activation-2.0 -I/usr/include/gail-1.0 -I/usr/lib/gtk-2.0/include -I/usr/include/cairo -I/usr/include/pixman-1 -pthread -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -pthread -I/usr/include/dbus-1.0 -I/usr/lib/x86_64-linux-gnu/dbus-1.0/include -I/usr/include/glib-2.0 -I/usr/lib/x86_64-linux-gnu/glib-2.0/include -g -O2 -pthread -pthread -pthread -o openvrml-player/openvrml-player openvrml-player/openvrml_player_openvrml_player-filechooserdialog.o openvrml-player/openvrml_player_openvrml_player-player.o openvrml-player/openvrml_player_openvrml_player-curlbrowserhost.o -Wl,--export-dynamic  -L/usr/lib/x86_64-linux-gnu /usr/lib/libgnomeui-2.so -lSM -lICE /usr/lib/libbonoboui-2.so /usr/lib/libgnomevfs-2.so /usr/lib/libgnomecanvas-2.so /usr/lib/libart_lgpl_2.so /usr/lib/libgconf-2.so /usr/lib/libgnome-2.so /usr/lib/libpopt.so /usr/lib/libbonobo-2.so /usr/lib/libbonobo-activation.so /usr/lib/libORBit-2.so /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/x86_64-linux-gnu/libatk-1.0.so /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so -lgdk_pixbuf-2.0 -lm /usr/lib/libcairo.so /usr/lib/x86_64-linux-gnu/libpango-1.0.so /usr/lib/x86_64-linux-gnu/libfreetype.so -lfontconfig /usr/lib/x86_64-linux-gnu/libgio-2.0.so /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so -ldbus-glib-1 -ldbus-1 -lpthread /usr/lib/x86_64-linux-gnu/libgobject-2.0.so /usr/lib/x86_64-linux-gnu/libgthread-2.0.so -lrt /usr/lib/x86_64-linux-gnu/libglib-2.0.so /usr/lib/libcurl-gnutls.so -pthread
/usr/lib/libbonoboui-2.so: undefined reference to `xmlFree@LIBXML2_2.4.30'
/usr/lib/libbonoboui-2.so: undefined reference to `xmlStrdup@LIBXML2_2.4.30'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlTextReaderRead@LIBXML2_2.4.30'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlTextReaderConstName@LIBXML2_2.6.0'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlTextReaderGetAttribute@LIBXML2_2.5.0'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlTextReaderDepth@LIBXML2_2.4.30'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlTextReaderConstXmlLang@LIBXML2_2.6.0'
/usr/lib/libbonoboui-2.so: undefined reference to `xmlParseDocument@LIBXML2_2.4.30'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlNewTextReaderFilename@LIBXML2_2.4.30'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlTextReaderNodeType@LIBXML2_2.4.30'
/usr/lib/libbonoboui-2.so: undefined reference to `xmlCreateMemoryParserCtxt@LIBXML2_2.4.30'
/usr/lib/libbonoboui-2.so: undefined reference to `xmlFreeParserCtxt@LIBXML2_2.4.30'
/usr/lib/libbonoboui-2.so: undefined reference to `xmlCreateFileParserCtxt@LIBXML2_2.4.30'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlFreeTextReader@LIBXML2_2.4.30'
/usr/lib/libgnomevfs-2.so: undefined reference to `xmlTextReaderConstValue@LIBXML2_2.6.0'
collect2: ld returned 1 exit status
make[4]: *** [openvrml-player/openvrml-player] Error 1
make[4]: Leaving directory `/home/matse/Documents/Software-System/openvrml-0.18.8/src'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/matse/Documents/Software-System/openvrml-0.18.8/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/matse/Documents/Software-System/openvrml-0.18.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matse/Documents/Software-System/openvrml-0.18.8'
make: *** [all] Error 2

Until now I wasn't able to figure out what's wrong. I know it has to do something with the LIBXML2 package, but this is installed correctly.

Any hints on how to solve this problem appreciated.

---

### Post by mc4man on 2011-06-07
You may wish to consider requesting a move to this subforum if nothing arises here
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

Did you build/install a source of libxml2 instead of using 11.04's? (and if you did, how?

> -I/usr/local/include/libxml2

If so, I'd try using 11.04's, sort of a shame to fail a long build near the end. (unless it's not suitable for some reason? -

---

### Post by matse on 2011-06-08
Hi mc4man,

first I used the 11.04's but after that problem arrises I tried with the libxml2 package. To me the error message sounds like an unresolved link from libbonoboui.so somewhere but I don't like to fix this manually.

Any other suggestions are very welcome .

---

### Post by mc4man on 2011-06-08
> **matse said:**
> Hi mc4man,

first I used the 11.04's but after that problem arrises I tried with the libxml2 package. To me the error message sounds like an unresolved link from libbonoboui.so somewhere but I don't like to fix this manually.

Any other suggestions are very welcome .

You might want to address whatever "problem arrises" when using 11.04's lib's - saw no issue here in building this source
(even though it configured in I disabled 'script-node-java' for build

While only guessing it would seem to be issue with the version of libxml2 you used and  current libbonoboui in place which does depend on libxml2
(did you use an older version of libxml2 than what is in 11.04?

Again it may serve you better to click on the 'report abuse' button and request moving to subforum I linked previously
(it isn't just limited to "abuse" situations

---

### Post by matse on 2011-06-10
Hey, finally got it work!!!!!

I found the hint on this page:

[http://git.gnome.org/browse/libxml2/commit/?id=00819877651b87842ed878898ba17dba489820f0](http://git.gnome.org/browse/libxml2/commit/?id=00819877651b87842ed878898ba17dba489820f0)

So all I had to do is to edit the ./configure.in file and change the line:
AM_CONDITIONAL([USE_VERSION_SCRIPT], [test -z "$VERSION_SCRIPT_FLAGS"])
to
AM_CONDITIONAL([USE_VERSION_SCRIPT], [test -n "$VERSION_SCRIPT_FLAGS"])

Hope this helps also others who had this problem!

---

