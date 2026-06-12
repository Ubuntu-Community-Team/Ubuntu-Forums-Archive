---
title: "I accidentally killed my Nautilus"
date: 2011-12-25
forum: Desktop Environments
---

### Post by dopefish124 on 2011-12-25
So my gnome experience isn't very fun now!
I'm missing my panels and icons - I believe this is because Nautilus can't start...

My windows work, that's how I can load windows like Firefox, right now.

So it kind of - and don't laugh - started when I attempted to add some scripts to my /etc/rcX  directory.(think it was rc4... not sure, the incriminating scripts are now removed).

Here is the output from the term when I start Nautilus... 

```
(nautilus:15686): GLib-GObject-CRITICAL **: g_value_dup_boxed: assertion `G_VALUE_HOLDS_BOXED (value)' failed

(nautilus:15686): GLib-GIO-CRITICAL **: g_themed_icon_constructed: assertion `themed->names != NULL && themed->names[0] != NULL' failed
*** glibc detected *** nautilus: free(): invalid next size (fast): 0x081e0040 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6a5bb25]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb6a5f590]
/usr/local/lib/libglib-2.0.so.0(g_free+0x31)[0xb6d9d941]
/usr/local/lib/libgio-2.0.so.0(g_themed_icon_new_from_names+0x8b)[0xb6e9dafb]
/usr/local/lib/libgio-2.0.so.0(g_content_type_get_icon+0xdf)[0xb6e7d9ef]
/usr/local/lib/libgio-2.0.so.0[0xb6eb1328]
/usr/local/lib/libgio-2.0.so.0[0xb6eac4a5]
/usr/local/lib/libgio-2.0.so.0(g_file_query_info+0x90)[0xb6e86c90]
/usr/local/lib/libgio-2.0.so.0[0xb6e881f4]
/usr/local/lib/libgio-2.0.so.0[0xb6e9cd49]
/usr/local/lib/libgio-2.0.so.0[0xb6e96884]
/usr/local/lib/libglib-2.0.so.0[0xb6dbf73b]
/usr/local/lib/libglib-2.0.so.0[0xb6dbdaaf]
/lib/tls/i686/cmov/libpthread.so.0[0xb6b444fb]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xb6ac6f5e]
======= Memory map: ========
08048000-0816f000 r-xp 00000000 08:01 82602      /usr/bin/nautilus
0816f000-08174000 rw-p 00127000 08:01 82602      /usr/bin/nautilus
08174000-081fa000 rw-p 08174000 00:00 0          [heap]
b5800000-b5821000 rw-p b5800000 00:00 0 
b5821000-b5900000 ---p b5821000 00:00 0 
b59cd000-b59ce000 ---p b59cd000 00:00 0 
b59ce000-b61ce000 rw-p b59ce000 00:00 0 
b61ce000-b61f6000 r-xp 00000000 08:01 114806     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b61f6000-b61f7000 rw-p 00028000 08:01 114806     /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b61f7000-b6200000 r-xp 00000000 08:01 1704037    /lib/tls/i686/cmov/libnss_files-2.7.so
b6200000-b6202000 rw-p 00008000 08:01 1704037    /lib/tls/i686/cmov/libnss_files-2.7.so
b6202000-b620a000 r-xp 00000000 08:01 1704039    /lib/tls/i686/cmov/libnss_nis-2.7.so
b620a000-b620c000 rw-p 00007000 08:01 1704039    /lib/tls/i686/cmov/libnss_nis-2.7.so
b620c000-b6213000 r-xp 00000000 08:01 1704035    /lib/tls/i686/cmov/libnss_compat-2.7.so
b6213000-b6215000 rw-p 00006000 08:01 1704035    /lib/tls/i686/cmov/libnss_compat-2.7.so
b6226000-b6265000 r--p 00000000 08:01 115544     /usr/lib/locale/en_NZ.utf8/LC_CTYPE
b6265000-b6346000 r--p 00000000 08:01 115543     /usr/lib/locale/en_NZ.utf8/LC_COLLATE
b6346000-b634a000 rw-p b6346000 00:00 0 
b634a000-b634d000 r-xp 00000000 08:01 3194948    /lib/libgpg-error.so.0.3.0
b634d000-b634e000 rw-p 00002000 08:01 3194948    /lib/libgpg-error.so.0.3.0
b634e000-b634f000 rw-p b634e000 00:00 0 
b634f000-b639a000 r-xp 00000000 08:01 3194946    /lib/libgcrypt.so.11.2.3
b639a000-b639c000 rw-p 0004a000 08:01 3194946    /lib/libgcrypt.so.11.2.3
b639c000-b63ab000 r-xp 00000000 08:01 84031      /usr/lib/libtasn1.so.3.0.12
b63ab000-b63ac000 rw-p 0000e000 08:01 84031      /usr/lib/libtasn1.so.3.0.12
b63ac000-b63c0000 r-xp 00000000 08:01 1704034    /lib/tls/i686/cmov/libnsl-2.7.so
b63c0000-b63c2000 rw-p 00013000 08:01 1704034    /lib/tls/i686/cmov/libnsl-2.7.so
b63c2000-b63c4000 rw-p b63c2000 00:00 0 
b63c4000-b63c8000 r-xp 00000000 08:01 83260      /usr/lib/libXdmcp.so.6.0.0
b63c8000-b63c9000 rw-p 00003000 08:01 83260      /usr/lib/libXdmcp.so.6.0.0
b63c9000-b6488000 r-xp 00000000 08:01 83321      /usr/lib/libasound.so.2.0.0
b6488000-b648c000 rw-p 000be000 08:01 83321      /usr/lib/libasound.so.2.0.0
b648c000-b648d000 rw-p b648c000 00:00 0 
b648d000-b649c000 r-xp 00000000 08:01 3195458    /lib/libbz2.so.1.0.4
b649c000-b649d000 rw-p 0000f000 08:01 3195458    /lib/libbz2.so.1.0.4
b649d000-b649f000 r-xp 00000000 08:01 83249      /usr/lib/libXau.so.6.0.0
b649f000-b64a0000 rw-p 00001000 08:01 83249      /usr/lib/libXau.so.6.0.0
b64a0000-b64a2000 r-xp 00000000 08:01 1704047    /lib/tls/i686/cmov/libutil-2.7.so
b64a2000-b64a4000 rw-p 00001000 08:01 1704047    /lib/tls/i686/cmov/libutil-2.7.so
b64a4000-b64b3000 r-xp 00000000 08:01 1704043    /lib/tls/i686/cmov/libresolv-2.7.so
b64b3000-b64b5000 rw-p 0000f000 08:01 1704043    /lib/tls/i686/cmov/libresolv-2.7.so
b64b5000-b64b8000 rw-p b64b5000 00:00 0 
b64b8000-b64c6000 r-xp 00000000 08:01 82209      /usr/lib/libavahi-client.so.3.2.4
b64c6000-b64c7000 rw-p 0000e000 08:01 82209      /usr/lib/libavahi-client.so.3.2.4
b64c7000-b64d1000 r-xp 00000000 08:01
Aborted

```

How can I get things back to normal so that my Desktop works properly? How do I reinstall Nautilus, if that is necessary? 

Ubuntu 8.04, Hardy btw! Yes, outdated!

Thank you kindly for any help.

---

### Post by BC59 on 2011-12-25
Look if the problem is solved with these commands:
```
nautilus -q
``` or ```
killall nautilus
```

---

### Post by BC59 on 2011-12-25
Or with this:

```
sudo apt-get -- reinstall install ubuntu-desktop
```

and this

```
sudo apt-get install nautilus
```

---

### Post by fdrake on 2011-12-25
nautilus in linux != (is not) explorer in windows ! 
try this end your pannel should restart:
```

gnome-session && gnome-panel &
nautilus

```

---

### Post by dopefish124 on 2011-12-25
Tried your tips - they did not work I'm afraid.

I reinstalled Ubuntu-Desktop as far as apt-get can do it.
Did the same for nautilus, reinstalled with apt-get.

I may have to venture out myself and open the bonnet of my system, for a more robust repair...

If anyone knows how this issue was caused - because it happened because I tried to install those bootscripts - I'd like to know!

---

### Post by fdrake on 2011-12-25
> **dopefish124 said:**
> Tried your tips - they did not work I'm afraid.
did you tried : "gnome-session && gnome-panel & " ?
and what's the output?
also how did you kill nautilus:

---

### Post by dopefish124 on 2011-12-25
> **fdrake said:**
> did you tried : "gnome-session && gnome-panel & " ?
and what's the output?
also how did you kill nautilus:

My bad, I replied to BC59 before I saw your post.

Yes I tried the commands you gave. I see what you mean by (nautilus != explorer.exe). I thought it was like that just by observation, not from old Windows habits.

Anyway, GLib-Gobject is still "critical" when I ran gnome-panel 

```

(gnome-panel:8162): GLib-GObject-CRITICAL **: g_value_dup_boxed: assertion `G_VALUE_HOLDS_BOXED (value)' failed

(gnome-panel:8162): GLib-GIO-CRITICAL **: g_themed_icon_constructed: assertion `themed->names != NULL && themed->names[0] != NULL' failed
*** glibc detected *** gnome-panel: malloc(): memory corruption: 0x083b3108 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb6d023f6]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x8d)[0xb6d03d4d]
/usr/local/lib/libglib-2.0.so.0(g_malloc+0x2d)[0xb6f27aad]
/usr/local/lib/libgobject-2.0.so.0(g_object_new_valist+0x50)[0xb6fc5510]
/usr/local/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb6fc58b0]
/usr/local/lib/libgio-2.0.so.0(g_themed_icon_new_from_names+0x81)[0xb776daf1]
/usr/local/lib/libgio-2.0.so.0(g_content_type_get_icon+0xdf)[0xb774d9ef]
/usr/local/lib/libgio-2.0.so.0[0xb7781328]
/usr/local/lib/libgio-2.0.so.0[0xb777c4a5]
/usr/local/lib/libgio-2.0.so.0(g_file_query_info+0x90)[0xb7756c90]
gnome-panel(panel_util_get_icon_for_uri+0x288)[0x8079088]
gnome-panel[0x8093980]
gnome-panel(panel_place_menu_item_new+0xb9)[0x80942c9]
gnome-panel[0x808f85d]
/usr/local/lib/libgobject-2.0.so.0(g_type_create_instance+0x45e)[0xb6fdf4be]
/usr/local/lib/libgobject-2.0.so.0[0xb6fc4422]
/usr/local/lib/libgobject-2.0.so.0(g_object_newv+0x318)[0xb6fc4be8]
/usr/local/lib/libgobject-2.0.so.0(g_object_new_valist+0x281)[0xb6fc5741]
/usr/local/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb6fc58b0]
gnome-panel(panel_menu_bar_load_from_gconf+0x44)[0x808ef34]
gnome-panel[0x80753f3]
/usr/local/lib/libglib-2.0.so.0[0xb6f1df21]
/usr/local/lib/libglib-2.0.so.0(g_main_context_dispatch+0x176)[0xb6f1fac6]
/usr/local/lib/libglib-2.0.so.0[0xb6f22e83]
/usr/local/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb6f23267]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7312264]
gnome-panel(main+0x1ac)[0x8063eec]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb6cac450]
gnome-panel[0x8063321]
======= Memory map: ========
08048000-080bf000 r-xp 00000000 08:01 84072      /usr/bin/gnome-panel
080bf000-080c2000 rw-p 00076000 08:01 84072      /usr/bin/gnome-panel
080c2000-083b8000 rw-p 080c2000 00:00 0          [heap]
b5f00000-b5f21000 rw-p b5f00000 00:00 0 
b5f21000-b6000000 ---p b5f21000 00:00 0 
b60de000-b60df000 r-xp 00000000 08:01 83245      /usr/lib/libXRes.so.1.0.0
b60df000-b60e0000 rw-p 00001000 08:01 83245      /usr/lib/libXRes.so.1.0.0
b60e0000-b6115000 r-xp 00000000 08:01 83883      /usr/lib/libwnck-1.so.22.3.8
b6115000-b6116000 rw-p 00035000 08:01 83883      /usr/lib/libwnck-1.so.22.3.8
b6116000-b6123000 r-xp 00000000 08:01 83736      /usr/lib/libpanel-applet-2.so.0.2.34
b6123000-b6124000 rw-p 0000c000 08:01 83736      /usr/lib/libpanel-applet-2.so.0.2.34
b6135000-b6140000 r-xp 00000000 08:01 1843527    /usr/lib/gnome-panel/libwnck-applet.so
b6140000-b6141000 rw-p 0000b000 08:01 1843527    /usr/lib/gnome-panel/libwnck-applet.so
b6141000-b61a1000 rw-s 00000000 00:09 3211274    /SYSV00000000 (deleted)
b61a1000-b61a5000 r-xp 00000000 08:01 115416     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b61a5000-b61a6000 rw-p 00003000 08:01 115416     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b61a7000-b6252000 r--p 00000000 08:01 297131     /usr/share/icons/Tangerine/icon-theme.cache
b6252000-b6356000 rw-p b6252000 00:00 0 
b6356000-b6358000 r-xp 00000000 08:01 156219     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6358000-b6359000 rw-p 00001000 08:01 156219     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b6359000-b63ea000 r--p 00000000 08:01 214587     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b63ea000-b63f0000 r--s 00000000 08:01 2002961    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b63f0000-b63f3000 r--s 00000000 08:01 2002956    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b63f3000-b63f4000 r--s 00000000 08:01 2002565    /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b63f4000-b63f8000 r--s 00000000 08:01 2002950    /var/cache/fontconfig/926e794c3d5e5dffcaf2fa83ef8d36c2-x86.cache-2
b63f8000-b63f9000 r--s 00000000 08:01 2002954    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b63f9000-b63fc000 r--s 00000000 08:01 1999408    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b63fc000-b6403000 r--s 00000000 08:01 2002962    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6403000-b6406000 r--s 00000000 08:01 2002958    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6406000-b640e000 r--s 00000000 08:01 2002959    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b640e000-b6416000 r--s 00000000 08:01 2002973    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6416000-b6417000 r--s 00000000 08:01 2002953    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b6417000-b6418000 r--s 00000000 08:01 2002952    /var/cache/fontconfig/393be3659170ead87bc7d2aed521dc5c-x86.cache-2
b6418000-b641b000 r--s 00000000 08:01 2002960    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b641b000-b6422000 r--s 00000000 08:01 2002955    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6422000-b6428000 r--s 00000000 08:01 2002957    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6428000-b642a000 r--s 00000000 08:01 2002519    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b642a000-b642b000 r--p 00000000 08:01 345347     /usr/share/locale-langpack/en_NZ/LC_MESSAGES/gnome-panel-2.0.mo
b642b000-b643c000 r-xp 00000000 08:01 114817     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b643c000-b643d000 rw-p 00011000 08:01 114817     /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b643d000-b647c000 r--p 00000000 08:01 115544     /usr/lib/locale/en_NZ.utf8/LC_CTYPE
b647c000-b655d000 r--p 00000000 08:01 115543     /usr/lib/locale/en_NZ.utf8/LC_COLLATE
b655d000-b6566000 r-xp 00000000 08:01 1704037    /lib/tls/i686/cmov/libnss_files-2.7.so
b6566000-b6568000 rw-p 00008000 08:01 1704037    /lib/tls/i686/cmov/libnss_files-2.7.so
b6568000-b6570000 r-xp 00000000 08:01 1704039    /lib/tls/i686/cmov/libnss_nis-2.7.so
b6570000-b6572000 rw-p 00007000 08:01 1704039    /lib/tls/i686/cmov/libnss_nis-2.7.so
b6572000-b6579000 r-xp 00000000 08:01 1704035    /lib/tls/i686/cmov/libnss_compat-2.7.so
b6579000-b657b000 rw-p 00006000 08:01 1704035    /lib/tls/i686/cmov/libnss_compat-2.7.so
b657b000-b657e000 rw-p b657b000 00:00 0 
b657e000-b6581000 r-xp 00000000 08:01 3194948    /lib/libgpg-error.so.0.3.0
b6581000-b6582000 rw-p 00002000 08:01 3194948    /lib/libgpg-error.so.0.3.0
b6582000-b6583000 rw-p b6582000 00:00 0 
b6583000-b65ce000 r-xp 00000000 08:01 3194946    /lib/libgcrypt.so.11.2.3
b65ce000-b65d0000 rw-p 0004a000 08:01 3194946    /lib/libgcrypt.so.11.2.3
b65d0000-b65df000 r-xp 00000000 08:01 84031      /usr/lib/libtasn1.so.3.0.12
b65df000-b65e0000 rw-p 0000e000 08:01 84031      /usr/lib/libtasn1.so.3.0.12
b65e0000-b65e4000 r-xp 00000000 08:01 83260      /usr/lib/libXdmcp.so.6.0.0
b65e4000-b65e5000 rw-p 00003000 08:01 83260      /usr/lib/libXdmcp.so.6.0.0
b65e5000-b6604000 r-xp 00000000 08:01 82650      /usr/lib/libexpat.so.1.5.2
b6604000-b6606000 rw-p 0001e000 08:01 82650      /usr/lib/libexpat.so.1.5.2
b6606000-b6607000 rw-p b6606000 00:00 0 
b6607000-b66c6000 r-xp 00000000 08:01 83321      /usr/lib/libasound.so.2.0.0
b66c6000-b66ca000 rw-p 000be000 08:01 83321      /usr/lib/libasound.so.2.0.0
b66ca000-b66cc000 r-xp 00000000 08:01 1704047    /lib/tls/i686/cmov/libutil-2.7.so
b66cc000-b66ce000 rw-p 00001000 08:01 1704047    /lib/tls/i686/cmov/libutil-2.7.so
b66ce000-b66dd000 r-xp 00000000 08:01 1704043    /lib/tls/i686/cmov/libresolv-2.7.so
b66dd000-b66df000 rw-p 0000f000 08:01 1704043    /lib/tls/i686/cmov/libresolv-2.7.so
b66df000-b66e1000 rw-p b66df000 00:00 0 
b66e1000-b66ef000 r-xp 00000000 08:01 82209      /usr/lib/libavahi-client.so.3.2.4
b66ef000-b66f0000 rw-p 0000e000 08:01 82209      /usr/lib/libavahi-client.so.3.2.4
b66f0000-b66fa000 r-xp 00000000 08:01 81993      /usr/lib/libavahi-common.so.3.5.0
b66fa000-b66fb000 rw-p 00009000 08:01 81993      /usr/lib/libavahi-common.so.3.5.0
b66fb000-b66fc000 rw-p b66fb000 00:00 0 
b66fc000-b66fe000 r-xp 00000000 08:01 82406      /usr/lib/libavahi-glib.so.1.0.1
b66fe000-b66ff000 rw-p 00001000 08:01 82406      /usr/lib/libavahi-glib.so.1.0.1
b66ff000-b6770000 r-xp 00000000 08:01 82595      /usr/lib/libgnutls.so.13.9.1
b6770000-b6775000 rw-p 00071000 08:01 82595      /usr/lib/libgnutls.so.13.9.1
b6775000-b679b000 r-xp 00000000 08:01 83909      /usr/lib/libpangoft2-1.0.so.0.2002.3
b679b000-b679c000 rw-p 00026000 08:01 83909      /usr/lib/libpangoft2-1.0.so.0.2002.3
b679c000-b67a2000 r-xp 00000000 08:01 83510      /usr/lib/libgailutil.so.18.0.1
b67a2000-b67a3000 rw-p 00006000 08:01 83510      /usr/lib/libgailutil.so.18.0.1
b67a3000-b67ba000 r-xp 00000000 08:01 84090      /usr/lib/libxcb.so.1.0.0
b67ba000-b67bb000 rw-p 00016000 08:01 84090      /usr/lib/libxcb.so.1.0.0
b67bb000-b67bc000 rw-p b67bb000 00:00 0 
b67bc000-b67bd000 r-xp 00000000 08:01 84088      /usr/lib/libxcb-xlib.so.0.0.0
b67bd000-b67be000 rw-p 00000000 08:01 84088      /usr/lib/libxcb-xlib.so.0.0.0
b67be000-b67d2000 r-xp 00000000 08:01 1704034    /lib/tls/i686/cmov/libnsl-2.7.so
b67d2000-b67d4000 rw-p 00013000 08:01 1704034    /lib/tls/i686/cmov/libnsl-2.7.so
b67d4000-b67d6000 rw-p b67d4000 00:00 0 
b67d6000-b680a000 r-xp 00000000 08:01 82601      /usr/lib/libdbus-1.so.3.4.0
b680a000-b680c000 rw-p 00034000 08:01 82601      /usr/lib/libdbus-1.so.3.4.0
b680c000-b6816000 r-xp 00000000 08:01 3195536    /lib/libgcc_s.so.1
b6816000-b6817000 rw-p 0000a000 08:01 3195536    /lib/libgcc_s.so.1
b6817000-b68ff000 r-xp 00000000 08:01 82251      /usr/lib/libstdc++.so.6.0.9
b68ff000-b6902000 r--p 000e8000 08:01 82251      /usr/lib/libstdc++.so.6.0.9
b6902000-b6904000 rw-p 000eb000 08:01 82251      /usr/lib/libstdc++.so.6.0.9
b6904000-b690b000 rw-p b6904000 00:00 0 
b690b000-b6933000 r-xp 00000000 08:01 83918      /usr/lib/libpixman-1.so.0.10.0
b6Aborted

```

EDIT: Oh, and by "kill" I didn't mean the tecnical term of linux, I meant I just "messed it up" lol.

---

### Post by fdrake on 2011-12-25
can you post the out put of :
```

cd ~
ls -al | grep -e '??' -e ".hidden"

```

---

