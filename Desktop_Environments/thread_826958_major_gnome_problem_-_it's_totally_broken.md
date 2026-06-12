---
title: "major gnome problem - it's totally broken"
date: 2008-06-12
forum: Desktop Environments
---

### Post by jeffspen on 2008-06-12
I have no idea how this happened. I'm using hardy heron and for about a week now i have had no gnome. i can see the background and some desklets (luckily) and have managed to get by in konqueror but i really really need my gnome back. 

I can't right-click on the desktop
I can't backup my evolution settings, it just crashes.
i can't mount a USB drive to copy stuff incase i need to reinstall everything.

Someone on another post suggested typing gnome-panel into terminal and i got this:

```
jeff@jeff-desktop:~$ gnome-panel

(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/actions of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/apps of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/categories of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/devices of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/emblems of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/emotes of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/mimetypes of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/places of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 72x72/status of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/actions of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/apps of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/categories of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/devices of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/emblems of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/emotes of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/mimetypes of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/places of theme CrashBit has no size field


(gnome-panel:7092): Gtk-WARNING **: Theme directory 96x96/status of theme CrashBit has no size field


(gnome-panel:7092): GLib-GObject-CRITICAL **: g_value_dup_boxed: assertion `G_VALUE_HOLDS_BOXED (value)' failed

(gnome-panel:7092): GLib-GIO-CRITICAL **: g_themed_icon_constructed: assertion `themed->names != NULL && themed->names[0] != NULL' failed

(gnome-panel:7092): GLib-GObject-CRITICAL **: g_value_dup_boxed: assertion `G_VALUE_HOLDS_BOXED (value)' failed

(gnome-panel:7092): GLib-GIO-CRITICAL **: g_themed_icon_constructed: assertion `themed->names != NULL && themed->names[0] != NULL' failed

(gnome-panel:7092): GLib-GObject-CRITICAL **: g_value_dup_boxed: assertion `G_VALUE_HOLDS_BOXED (value)' failed

(gnome-panel:7092): GLib-GIO-CRITICAL **: g_themed_icon_constructed: assertion `themed->names != NULL && themed->names[0] != NULL' failed
*** glibc detected *** gnome-panel: free(): invalid next size (fast): 0x08379c38 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb749fa85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb74a34f0]
/usr/local/lib/libglib-2.0.so.0(g_free+0x31)[0xb76c5941]
/usr/local/lib/libgio-2.0.so.0(g_themed_icon_new_from_names+0x8b)[0xb7f0bafb]
/usr/local/lib/libgio-2.0.so.0(g_content_type_get_icon+0xdf)[0xb7eeb9ef]
/usr/local/lib/libgio-2.0.so.0[0xb7f1f328]
/usr/local/lib/libgio-2.0.so.0[0xb7f1a4a5]
/usr/local/lib/libgio-2.0.so.0(g_file_query_info+0x90)[0xb7ef4c90]
gnome-panel(panel_util_get_icon_for_uri+0x288)[0x8078ff8]
gnome-panel[0x8093810]
gnome-panel(panel_place_menu_item_new+0xb9)[0x8094159]
gnome-panel[0x808f6ed]
/usr/local/lib/libgobject-2.0.so.0(g_type_create_instance+0x45e)[0xb777d4be]
/usr/local/lib/libgobject-2.0.so.0[0xb7762422]
/usr/local/lib/libgobject-2.0.so.0(g_object_newv+0x318)[0xb7762be8]
/usr/local/lib/libgobject-2.0.so.0(g_object_new_valist+0x281)[0xb7763741]
/usr/local/lib/libgobject-2.0.so.0(g_object_new+0x40)[0xb77638b0]
gnome-panel(panel_menu_bar_load_from_gconf+0x44)[0x808edc4]
gnome-panel[0x8075363]
/usr/local/lib/libglib-2.0.so.0[0xb76bbf21]
/usr/local/lib/libglib-2.0.so.0(g_main_context_dispatch+0x176)[0xb76bdac6]
/usr/local/lib/libglib-2.0.so.0[0xb76c0e83]
/usr/local/lib/libglib-2.0.so.0(g_main_loop_run+0x1e7)[0xb76c1267]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7ab0264]
gnome-panel(main+0x1ac)[0x8063e5c]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0)[0xb744a450]
gnome-panel[0x8063291]
======= Memory map: ========
08048000-080bf000 r-xp 00000000 08:01 56642849   /usr/bin/gnome-panel
080bf000-080c2000 rw-p 00076000 08:01 56642849   /usr/bin/gnome-panel
080c2000-0838c000 rw-p 080c2000 00:00 0          [heap]
b0100000-b0121000 rw-p b0100000 00:00 0 
b0121000-b0200000 ---p b0121000 00:00 0 
b0290000-b0291000 r-xp 00000000 08:01 56640804   /usr/lib/libXRes.so.1.0.0
b0291000-b0292000 rw-p 00001000 08:01 56640804   /usr/lib/libXRes.so.1.0.0
b0292000-b02c7000 r-xp 00000000 08:01 56641074   /usr/lib/libwnck-1.so.22.3.7
b02c7000-b02c8000 rw-p 00035000 08:01 56641074   /usr/lib/libwnck-1.so.22.3.7
b02c8000-b02d5000 r-xp 00000000 08:01 56639795   /usr/lib/libpanel-applet-2.so.0.2.34
b02d5000-b02d6000 rw-p 0000c000 08:01 56639795   /usr/lib/libpanel-applet-2.so.0.2.34
b02da000-b02e4000 r-xp 00000000 08:01 56656848   /usr/lib/gnome-panel/libfish-applet-2.so
b02e4000-b02e5000 rw-p 00009000 08:01 56656848   /usr/lib/gnome-panel/libfish-applet-2.so
b02e5000-b02e6000 r--p 00000000 08:01 57017798   /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
b02e6000-b02ea000 r-xp 00000000 08:01 34439183   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b02ea000-b02eb000 rw-p 00003000 08:01 34439183   /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b02eb000-b02ec000 r--p 00000000 08:01 57017790   /usr/share/locale-langpack/en_GB/LC_MESSAGES/libwnck.mo
b02ec000-b02f7000 r-xp 00000000 08:01 56656851   /usr/lib/gnome-panel/libwnck-applet.so
b02f7000-b02f8000 rw-p 0000b000 08:01 56656851   /usr/lib/gnome-panel/libwnck-applet.so
b02f8000-b0358000 rw-s 00000000 00:09 3047477    /SYSV00000000 (deleted)
b0358000-b094c000 r--p 00000000 08:01 56950906   /usr/share/icons/hicolor/icon-theme.cache
b094c000-b2440000 r--p 00000000 08:01 56902698   /usr/share/icons/crystalsvg/icon-theme.cache
b2440000-b2bb5000 r--p 00000000 08:01 56951224   /usr/share/icons/gnome/icon-theme.cache
b2bb5000-b68f3000 r--p 00000000 08:01 21614807   /home/jeff/.icons/CrashBit/icon-theme.cache
b68f3000-b69f7000 rw-p b68f3000 00:00 0 
b69f7000-b69f9000 r-xp 00000000 08:01 6275075    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b69f9000-b69fa000 rw-p 00001000 08:01 6275075    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b69fa000-b6a03000 r--p 00000000 08:01 57166849   /usr/local/share/locale/en_GB/LC_MESSAGES/glib20.mo
b6a03000-b6a94000 r--p 00000000 08:01 56821692   /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6a94000-b6a9a000 r--s 00000000 08:01 35390349   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b6a9a000-b6a9d000 r--s 00000000 08:01 35390579   /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b6a9d000-b6a9e000 r--s 00000000 08:01 35390578   /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
b6a9e000-b6aa2000 r--s 00000000 08:01 35390577   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b6aa2000-b6aa3000 r--s 00000000 08:01 35390576   /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b6aa3000-b6aa4000 r--s 00000000 08:01 35390574   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b6aa4000-b6aa7000 r--s 00000000 08:01 35390573   /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b6aa7000-b6aae000 r--s 00000000 08:01 35390572   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6aae000-b6ab1000 r--s 00000000 08:01 35390571   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6ab1000-b6ab9000 r--s 00000000 08:01 35390569   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6ab9000-b6ac1000 r--s 00000000 08:01 35390568   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b6ac1000-b6ae3000 r--s 00000000 08:01 35390414   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6ae3000-b6ae6000 r--s 00000000 08:01 35390404   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6ae6000-b6aed000 r--s 00000000 08:01 35390333   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b6aed000-b6af3000 r--s 00000000 08:01 35389852   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6af3000-b6afa000 r--s 00000000 08:01 35390031   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6afa000-b6b01000 r-xp 00000000 08:01 34324481   /usr/lib/gtk-2.0/2.10.0/engines/libcleanice.so
b6b01000-b6b02000 rw-p 00006000 08:01 34324481   /usr/lib/gtk-2.0/2.10.0/engines/libcleanice.so
b6b02000-b6b03000 r--p 00000000 08:01 57017819   /usr/share/locale-langpack/en_GB/LC_MESSAGES/libbonobo-2.0.mo
b6b03000-b6b06000 r--p 00000000 08:01 57017791   /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20-properties.mo
b6b06000-b6b0b000 r--p 00000000 08:01 57017843   /usr/share/locale-langpack/en_GB/LC_MESSAGES/gtk20.mo
b6b0b000-b6b4a000 r--p 00000000 08:01 56688910   /usr/lib/locale/en_GB.utf8/LC_CTYPE
b6b4a000-b6b4b000 r--p 00000000 08:01 56689846   /usr/lib/locale/en_GB.utf8/LC_NUMERIC
b6b4b000-b6b4c000 r--p 00000000 08:01 56688932   /usr/lib/locale/en_GB.utf8/LC_TIME
b6b4c000-b6c2d000 r--p 00000000 08:01 39895041   /usr/lib/locale/en_GB.utf8/LC_COLLATE
b6c2d000-b6cfa000 r--p 00000000 08:01 37470236   /usr/lib/locale/locale-archive
b6cfa000-b6d03000 r-xp 00000000 08:01 31981623   /lib/tls/i686/cmov/libnss_files-2.7.so
b6d03000-b6d05000 rw-p 00008000 08:01 31981623   /lib/tls/i686/cmov/libnss_files-2.7.so
b6d05000-b6d0d000 r-xp 00000000 08:01 31981625   /lib/tls/i686/cmov/libnss_nis-2.7.so
b6d0d000-b6d0f000 rw-p 00007000 08:01 31981625   /lib/tls/i686/cmov/libnss_nis-2.7.so
b6d0f000-b6d16000 r-xp 00000000 08:01 31981621   /lib/tls/i686/cmov/libnss_compat-2.7.so
b6d16000-b6d18000 rw-p 00006000 08:01 31981621   /lib/tls/i686/cmov/libnss_compat-2.7.so
b6d18000-b6d1b000 rw-p b6d18000 00:00 0 
b6d1b000-b6d1e000 r-xp 00000000 08:01 21266466   /lib/libgpg-error.so.0.3.0
b6d1e000-b6d1f000 rw-p 00002000 08:01 21266466   /lib/libgpg-error.so.0.3.0
b6d1f000-b6d20000 rw-p b6d1f000 00:00 0 
b6d20000-b6d6b000 r-xp 00000000 08:01 21266887   /lib/libgcrypt.so.11.2.3
b6d6b000-b6d6d000 rw-p 0004a000 08:01 21266887   /lib/libgcrypt.so.11.2.3
b6d6d000-b6d7c000 r-xp 00000000 08:01 56640836   /usr/lib/libtasn1.so.3.0.12
b6d7c000-b6d7d000 rw-p 0000e000 08:01 56640836   /usr/lib/libtasn1.so.3.0.12
b6d7d000-b6d81000 r-xp 00000000 08:01 56640819   /usr/lib/libXdmcp.so.6.0.0
b6d81000-b6d82000 rw-p 00003000 08:01 56640819   /usr/lib/libXdmcp.so.6.0.0
b6d82000-b6da1000 r-xp 00000000 08:01 56639676   /usr/lib/libexpat.so.1.5.2
b6da1000-b6da3000 rw-p 0001e000 08:01 56639676   /usr/lib/libexpat.so.1.5.2
b6da3000-b6da4000 rw-p b6da3000 00:00 0 
b6da4000-b6e63000 r-xp 00000000 08:01 56642878   /usr/lib/libasound.so.2.0.0
b6e63000-b6e67000 rw-p 000be000 08:01 56642878   /usr/lib/libasound.so.2.0.0
b6e67000-b6e69000 r-xp 00000000 08:01 31981633   /lib/tls/i686/cmov/libutil-2.7.so
b6e69000-b6e6b000 rw-p 00001000 08:01 31981633   /lib/tls/i686/cmov/libutil-2.7.so
b6e6b000-b6e7a000 r-xp 00000000 08:01 31981629   /lib/tls/i686/cmov/libresolv-2.7.so
b6e7a000-b6e7c000 rw-p 0000f000 08:01 31981629   /lib/tls/i686/cmov/libresolv-2.7.so
b6e7c000-b6e7e000 rw-Aborted

```

Can anyone help?? i'm desperate!!

---

### Post by toster13 on 2008-06-12
did you try to return on default human icon theme?

---

### Post by Xiong Chiamiov on 2008-06-12
When dealing with DE (Desktop Environment) problems, if you're completely stuck, you can move the correct folder in your home directory to force generation of a new one.
```

mv ~/.gnome2 ~/.gnome2_old

```
Restart and you should have a fresh GNOME, as if you just installed it.  You still have all your old configuration files and such in the .gnome2_old folder, so you can copy over things until you find what broke it.

---

### Post by Harpoon on 2008-06-13
I just ran into this after doing an update to Hardy (64 bit).  No desktop icons, no ability to right-click, etc.  Renaming the .gnome2 folder did the trick.  

Strange thing is, none of the "important" directories had been updated, so the cause of the problem lies elsewhere.

Strange

---

