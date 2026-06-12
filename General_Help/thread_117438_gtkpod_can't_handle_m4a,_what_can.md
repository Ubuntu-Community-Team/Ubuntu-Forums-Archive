---
title: "gtkpod can't handle m4a, what can?"
date: 2006-01-14
forum: General Help
---

### Post by o_fortuna on 2006-01-14
I have a huge collection of aac/m4a files that I'd like to be able to sync with my iPod. I occassionally buy music from the iTunes Music Store, which is always in m4a format. I don't want to convert m4a to another format. I just want it on my iPod. How can I do that? (The files aren't DRM'ed).

In Hoary, I always used gtkpod-aac. This is no longer available in Breezy, and it has become painfully apparent. Is there another application that can properly send m4a files to my iPod?

I did a forum search, and I never found a simple solution to getting gtkpod to work with aac. If someone knows where such a solution is, please tell me!

---

### Post by shadesfox on 2006-01-14
I think the problem is that gtkpod has had issues compiling against the faac libraries.  I usually grab the latest sources from [http://www.gtkpod.org/](http://www.gtkpod.org/) then compile it

CFLAGS="-fno-inline" ./configure
make
make install

Make sure you get all the dev libraries.

---

### Post by IDavidson on 2006-10-18
Ummmm, I think that I have the same problem as he does but I don't know. Whenever I try to upload a .m4a file into gtkpod it gives me this error 

m4a/m4p/m4b not supported without the mp4v2 library. You must compile the gtkpod source together with the mp4v2 library.

how do I compile it

---

### Post by Ba66e77 on 2007-05-20
I'm trying to compile, per the instructions above and getting make errors.  Anyone know what these mean?

barrett@barrett-desktop:~/Desktop/gtkpod-0.99.8$ make
make  all-recursive
make[1]: Entering directory `/home/barrett/Desktop/gtkpod-0.99.8'
Making all in src
make[2]: Entering directory `/home/barrett/Desktop/gtkpod-0.99.8/src'
make  all-am
make[3]: Entering directory `/home/barrett/Desktop/gtkpod-0.99.8/src'
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2 -I/usr/include/gpod-1.0 -DMOUNT_BIN=\""/bin/mount\"" -DUMOUNT_BIN=\""/bin/umount\"" -DEJECT_BIN=\""@EJECT@\"" -DPACKAGE_DATA_DIR=\""/usr/local/share"\" -DPACKAGE_LOCALE_DIR=\""/usr/local//locale"\"    -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2 -I/usr/include/gpod-1.0   -fno-inline -Wall -Wno-pointer-sign -MT file.o -MD -MP -MF ".deps/file.Tpo" \
          -c -o file.o `test -f 'file.c' || echo './'`file.c; \
        then mv -f ".deps/file.Tpo" ".deps/file.Po"; \
        else rm -f ".deps/file.Tpo"; exit 1; \
        fi
file.c: In function ‘copy_new_info’:
file.c:854: error: ‘Track’ has no member named ‘unk208’
file.c:854: error: ‘Track’ has no member named ‘unk208’
file.c: In function ‘get_track_info_from_file’:
file.c:1073: error: ‘Track’ has no member named ‘unk208’
file.c:1082: error: ‘Track’ has no member named ‘unk208’
file.c:1090: error: ‘Track’ has no member named ‘unk208’
file.c:1102: error: ‘Track’ has no member named ‘unk208’
file.c:1113: error: ‘Track’ has no member named ‘unk208’
make[3]: *** [file.o] Error 1
make[3]: Leaving directory `/home/barrett/Desktop/gtkpod-0.99.8/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/barrett/Desktop/gtkpod-0.99.8/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/barrett/Desktop/gtkpod-0.99.8'
make: *** [all] Error 2

---

### Post by lightmind on 2007-05-25
Hi,
I had the same issue. I installed the package gtkpod-aac; gtkpod worked with m4a after the install completed....

---

