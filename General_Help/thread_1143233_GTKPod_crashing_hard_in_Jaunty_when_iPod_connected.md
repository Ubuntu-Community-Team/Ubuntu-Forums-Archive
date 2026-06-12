---
title: "GTKPod crashing hard in Jaunty when iPod connected"
date: 2009-04-29
forum: General Help
---

### Post by grundunkus on 2009-04-29
I have the newest iPod classic 120gb and whenever I try to load it up in gtkpod I get a dialogue saying that checksums don't match and it will have to update the SHA1 of everything, but then that dialogue disappears (quicker than I can transcribe it).

If I run gtkpod from the terminal, I get the following information:
```
*** glibc detected *** gtkpod: corrupted double-linked list: 0x0a46e1c0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb73ab07f]
/lib/tls/i686/cmov/libc.so.6[0xb73acfb2]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0xef)[0xb73ae6ef]
/usr/lib/libglib-2.0.so.0(g_malloc0+0x3c)[0xb77c920c]
gtkpod(gp_track_add_extra+0x54)[0x8080844]
gtkpod(gp_itdb_add_extra_full+0x3d)[0x808166d]
gtkpod(gp_import_itdb+0x1f3)[0x809e3c3]
gtkpod(gp_load_ipod+0x48a)[0x809f08a]
gtkpod[0x8063c01]
/usr/lib/libglib-2.0.so.0[0xb77c12b6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8)[0xb77c0b88]
/usr/lib/libglib-2.0.so.0[0xb77c40eb]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0xb77c45ba]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0xb7ca17d9]
gtkpod(main+0x97)[0x80a27c7]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7351775]
gtkpod[0x8063991]
======= Memory map: ========
08048000-080db000 r-xp 00000000 08:06 83086      /usr/bin/gtkpod
080db000-080dc000 r-xp 00092000 08:06 83086      /usr/bin/gtkpod
080dc000-080de000 rwxp 00093000 08:06 83086      /usr/bin/gtkpod
080de000-080e0000 rwxp 080de000 00:00 0 
09bb6000-0af4c000 rwxp 09bb6000 00:00 0          [heap]
b5e00000-b5e21000 rwxp b5e00000 00:00 0 
b5e21000-b5f00000 ---p b5e21000 00:00 0 
b5f2a000-b5f5b000 rwxp b5f2a000 00:00 0 
b5f5f000-b5fbf000 rwxs 00000000 00:09 13959191   /SYSV00000000 (deleted)
b5fbf000-b5fe0000 r-xp 00000000 08:06 764252     /usr/share/fonts/truetype/ttf-liberation/LiberationSans-Bold.ttf
b5fe0000-b6000000 r-xp 00000000 08:06 764253     /usr/share/fonts/truetype/ttf-liberation/LiberationSans-BoldItalic.ttf
b6000000-b6060000 rwxs 00000000 00:09 13926422   /SYSV00000000 (deleted)
b6060000-b607b000 r-xs 00000000 08:06 172040     /usr/share/mime/mime.cache
b607b000-b608d000 r-xp 00000000 08:06 6316223    /usr/lib/libgvfscommon.so.0.0.0
b608d000-b608e000 r-xp 00012000 08:06 6316223    /usr/lib/libgvfscommon.so.0.0.0
b608e000-b608f000 rwxp 00013000 08:06 6316223    /usr/lib/libgvfscommon.so.0.0.0
b6091000-b6092000 r-xs 00000000 08:06 176492     /usr/local/share/mime/mime.cache
b6092000-b6093000 r-xs 00000000 08:06 795290     /home/blake/.local/share/mime/mime.cache
b6093000-b60ad000 r-xp 00000000 08:06 106916     /usr/lib/gio/modules/libgvfsdbus.so
b60ad000-b60ae000 r-xp 00019000 08:06 106916     /usr/lib/gio/modules/libgvfsdbus.so
b60ae000-b60af000 rwxp 0001a000 08:06 106916     /usr/lib/gio/modules/libgvfsdbus.so
b60af000-b60be000 r-xp 00000000 08:06 106909     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b60be000-b60bf000 r-xp 0000e000 08:06 106909     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b60bf000-b60c0000 rwxp 0000f000 08:06 106909     /usr/lib/gio/modules/libgioremote-volume-monitor.so
b60c0000-b60c1000 ---p b60c0000 00:00 0 
b60c1000-b68c1000 rwxp b60c1000 00:00 0 
b68c1000-b68e2000 r-xp 00000000 08:06 764255     /usr/share/fonts/truetype/ttf-liberation/LiberationSans-Regular.ttf
b68e2000-b68e4000 r-xp 00000000 08:06 155897     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b68e4000-b68e5000 r-xp 00001000 08:06 155897     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b68e5000-b68e6000 rwxp 00002000 08:06 155897     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b68e6000-b68ec000 r-xs 00000000 08:06 7234695    /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b68ec000-b68ee000 r-xs 00000000 08:06 7238546    /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-x86.cache-2
b68ee000-b68f1000 r-xs 00000000 08:06 7238544    /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b68f1000-b68f2000 r-xs 00000000 08:06 7238543    /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b68f2000-b68f3000 r-xs 00000000 08:06 7238542    /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b68f3000-b68f6000 r-xs 00000000 08:06 7238541    /var/cache/fontconfig/6eb3985aa4124903f6ff08ba781cd364-x86.cache-2
b68f6000-b68f7000 r-xs 00000000 08:06 7238540    /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b68f7000-b68f9000 r-xs 00000000 08:06 7238539    /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b68f9000-b68fc000 r-xs 00000000 08:06 7238538    /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b68fc000-b6903000 r-xs 00000000 08:06 7238537    /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b6903000-b6906000 r-xs 00000000 08:06 7238536    /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b6906000-b6908000 r-xs 00000000 08:06 7238535    /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b6908000-b6910000 r-xs 00000000 08:06 7238534    /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b6910000-b691b000 r-xs 00000000 08:06 7238532    /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b691b000-b691d000 r-xs 00000000 08:06 7238531    /var/cache/fontconfig/ddd4086aec35a5275babba44bb759c3c-x86.cache-2
b691d000-b691e000 r-xs 00000000 08:06 7238530    /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b691e000-b6940000 r-xs 00000000 08:06 7238529    /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b6940000-b6942000 r-xs 00000000 08:06 7238528    /var/cache/fontconfig/2c5ba8142dffc8bf0377700342b8ca1a-x86.cache-2
b6942000-b6945000 r-xs 00000000 08:06 7237720    /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b6945000-b694c000 r-xs 00000000 08:06 7238526    /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b694c000-b6959000 r-xs 00000000 08:06 7234281    /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6959000-b6981000 r-xp 00000000 08:06 3022924    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6981000-b6982000 r-xp 00027000 08:06 3022924    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6982000-b6983000 rwxp 00028000 08:06 3022924    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6983000-b698a000 r-xp 00000000 08:06 85422      /usr/lib/libltdl.so.7.2.0
b698a000-b698b000 r-xp 00006000 08:06 85422      /usr/lib/libltdl.so.7.2.0
b698b000-b698c000 rwxp 00007000 08:06 85422      /usr/lib/libltdl.so.7.2.0
b698c000-b6998000 r-xp 00000000 08:06 82281      /usr/lib/libtdb.so.1.1.3
b6998000-b6999000 r-xp 0000b000 08:06 82281      /usr/lib/libtdb.so.1.1.3
b6999000-b699a000 rwxp 0000c000 08:06 82281      /usr/lib/libtdb.so.1.1.3
b699b000-b69a0000 r-xs 00000000 08:06 7238525    /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b69a0000-b69a6000 r-xs 00000000 08:06 7238517    /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b69a6000-b69a8000 r-xs 00000000 08:06 7237280    /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b69a8000-b69b6000 r-xs 00000000 08:06 7238549    /var/cache/fontconfig/865f88548240fee46819705c6468c165-x86.cache-2
b69b6000-b69ba000 r-xs 00000000 08:06 7238548    /var/cache/fontconfig/4c599c202bc5c08e2d34565a40eac3b2-x86.cache-2
b69ba000-b69c4000 r-xp 00000000 08:06 9379912    /lib/tls/i686/cmov/libnss_files-2.9.so
b69c4000-b69c5000 r-xp 00009000 08:06 9379912    /lib/tls/i686/cmov/libnss_files-2.9.so
b69c5000-b69c6000 rwxp 0000a000 08:06 9379912    /lib/tls/i686/cmov/libnss_files-2.9.so
b69c6000-b69cf000 r-xp 00000000 08:06 9379914    /lib/tls/i686/cmov/libnss_nis-2.9.so
b69cf000-b69d0000 r-xp 00008000 08:06 9379914    /lib/tls/i686/cmov/libnss_nis-2.9.so
b69d0000-b69d1000 rwxp 00009000 08:06 9379914    /lib/tls/i686/cmov/libnss_nis-2.9.so
b69d1000-b69e6000 r-xp 00000000 08:06 9379909    /lib/tls/i686/cmov/libnsl-2.9.so
b69e6000-b69e7000 r-xp 00014000 08:06 9379909    /lib/tls/i686/cmov/libnsl-2.9.so
b69e7000-b69e8000 rwxp 00015000 08:06 9379909    /lib/tls/i686/cmov/libnsl-2.9.so
b69e8000-b69ea000 rwxp b69e8000 00:00 0 
b69ea000-b69ee000 r-xp 00000000 08:06 2810156    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b69ee000-b69ef000 r-xp 00003000 08:06 2810156    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b69ef000-b69f0000 rwxp 00004000 08:06 2810156    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b69f0000-b69fd000 r-xp 00000000 08:06 82283      /usr/lib/libcanberra.so.0.1.4
b69fd000-b69fe000 r-xp 0000d000 08:06 82283      /usr/lib/libcanberra.so.0.1.4
b69fe000-b69ff000 rwxp 0000e000 08:06 82283      /usr/lib/libcanberra.so.0.1.4
b69ff000-b6a02000 r-xp 00000000 08:06 6316256    /usr/lib/libcanberra-gtk.so.0.0.4
b6a02000-b6a03000 r-xp 00002000 08:06 6316256    /usr/lib/libcanberra-gtk.so.0.0.4
b6a03000-b6a04000 rwxp 00003000 08:06 6316256    /usr/lib/libcanberra-gtk.so.0.0.4
b6a04000-b6a08000 r-xp 00000000 08:06 3801090    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6a08000-b6a09000 r-xp 00003000 08:06 3801090    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6a09000-b6a0a000 rwxp 00004000 08:06 3801090    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6a0a000-b6a49000 r-xp 00000000 08:06 5177543    /usr/lib/locale/en_AU.utf8/LC_CTYPE
b6a49000-b6b34000 r-xp 00000000 08:06 5177545    /usr/lib/locale/en_Aborted

```

I have searched for ages and I can't find any info about why this is happening. 

Worse still, I can't get floola to recognise the iPod and Songbird's iPod support is so bad that instead of copying the files to it, it copies references to the iPod to the files on my computer!

Please help, I don't want to scrub my iPod and start again because I'm currently abroad and don't want to lose my tunes, but I also need to be able to add stuff to it!

Thanks in advance.

---

### Post by grundunkus on 2009-05-09
I scrubbed my iPod and it crashed with the same error.
I deleted my ~/.gtkpod folder and it still crashed.
I removed and reinstalled gtkpod and it still crashed.
I removed and reinstalled libgpod+gtkpod together and it still crashed.

I am going to have to try to compile the trunk version of gtkpod from source and if that doesn't work, I'm going to have to use iTunes. Yuck.

If anyone has any idea as to what might be the problem, I would be *very* grateful for your insight. I would very much prefer to live as much of an iTunes free existence as possible and gtkpod seems (apart from the fact that it doesn't seem to work at all for me) to be the ideal solution.

---

