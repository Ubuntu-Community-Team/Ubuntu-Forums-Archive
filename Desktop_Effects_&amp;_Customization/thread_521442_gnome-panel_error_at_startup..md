---
title: "gnome-panel error at startup."
date: 2007-08-09
forum: Desktop Effects &amp; Customization
---

### Post by ios_base on 2007-08-09
I added Beryl-Manager to startup programs in Sessions.  Now when I log in gnome-panel crashes and I get an error message like this:

> 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "codeshiftster"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/codeshiftster-desktop:/tmp/.ICE-unix/6267
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:55: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:56: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:57: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:55: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:56: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:57: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Initializing nautilus-open-terminal extension
Initializing nautilus-image-converter extension
Initializing gnome-mount extension
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:55: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:56: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:57: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:55: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:56: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:57: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
*** glibc detected *** x-session-manager: malloc(): memory corruption (fast): 0x0823d6d8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76056fc]
/lib/tls/i686/cmov/libc.so.6(__libc_malloc+0x7e)[0xb760660e]
/usr/lib/libglib-2.0.so.0(g_malloc+0x36)[0xb771c2c6]
/usr/lib/libgdk-x11-2.0.so.0[0xb7ab2db0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_region_intersect+0x99)[0xb7ab41e9]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_maybe_recurse+0x10d)[0xb7ab7f2d]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_region+0x40)[0xb7ab81c0]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_invalidate_rect+0xaf)[0xb7ab827f]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_queue_draw_area+0x150)[0xb7d6d440]
x-session-manager[0x805ce05]
/usr/lib/libglib-2.0.so.0[0xb77153c6]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x182)[0xb7714df2]
/usr/lib/libglib-2.0.so.0[0xb7717dcf]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7718179]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb4)[0xb7c4d044]
x-session-manager(main+0x5de)[0x805638e]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75b2ebc]
x-session-manager[0x8051d51]
======= Memory map: ========
08048000-08068000 r-xp 00000000 08:01 6144452    /usr/bin/gnome-session
08068000-08069000 rw-p 00020000 08:01 6144452    /usr/bin/gnome-session
08069000-082aa000 rw-p 08069000 00:00 0          [heap]
b4400000-b4421000 rw-p b4400000 00:00 0 
b4421000-b4500000 ---p b4421000 00:00 0 
b455b000-b4566000 r-xp 00000000 08:01 688192     /lib/libgcc_s.so.1
b4566000-b4567000 rw-p 0000a000 08:01 688192     /lib/libgcc_s.so.1
b457e000-b45de000 rw-s 00000000 00:08 1048582    /SYSV00000000 (deleted)
b45de000-b45df000 ---p b45de000 00:00 0 
b45df000-b4ddf000 rw-p b45df000 00:00 0 
b4ddf000-b4e5c000 r--p 00000000 08:01 6359097    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b4e5c000-b4e5e000 r-xp 00000000 08:01 6275586    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4e5e000-b4e5f000 rw-p 00001000 08:01 6275586    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b4e5f000-b4e65000 r--s 00000000 08:01 10043484   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b4e65000-b4e66000 r--s 00000000 08:01 10044027   /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b4e66000-b4e69000 r--s 00000000 08:01 10044026   /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b4e69000-b4e6a000 r--s 00000000 08:01 10044024   /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b4e6a000-b4e6b000 r--s 00000000 08:01 10044022   /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b4e6b000-b4e6f000 r--s 00000000 08:01 10043481   /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b4e6f000-b4e70000 r--s 00000000 08:01 10044020   /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b4e70000-b4e72000 r--s 00000000 08:01 10044019   /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b4e72000-b4e74000 r--s 00000000 08:01 10044018   /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b4e74000-b4e75000 r--s 00000000 08:01 10044015   /var/cache/fontconfig/75a2cd575a62c63e802c11411fb87c37-x86.cache-2
b4e75000-b4e77000 r--s 00000000 08:01 10044012   /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b4e77000-b4e7d000 r--s 00000000 08:01 10044011   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b4e7d000-b4e7f000 r--s 00000000 08:01 10044010   /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b4e7f000-b4e81000 r--s 00000000 08:01 10044006   /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b4e81000-b4e89000 r--s 00000000 08:01 10044005   /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b4e89000-b4e8f000 r--s 00000000 08:01 10044004   /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b4e8f000-b4e90000 r--s 00000000 08:01 10044003   /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4e90000-b4ea7000 r--s 00000000 08:01 10044002   /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b4ea7000-b4ea9000 r--s 00000000 08:01 10044001   /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b4ea9000-b4eb9000 r--s 00000000 08:01 10044000   /var/cache/fontconfig/62e73dac2d59556d9f67eb1d3123e845-x86.cache-2
b4eb9000-b4ebf000 r--s 00000000 08:01 10043999   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b4ebf000-b4ec3000 r--s 00000000 08:01 10043998   /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b4ec3000-b4ec6000 r--s 00000000 08:01 10043997   /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4ec6000-b4eca000 r--s 00000000 08:01 10043947   /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4eca000-b4ed1000 r--s 00000000 08:01 10043807   /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b4ed1000-b4ed2000 r--s 00000000 08:01 10044073   /var/cache/fontconfig/fcff1cd55d48a2c86a175e9943c3506d-x86.cache-2
b4ed2000-b4ed3000 r--s 00000000 08:01 10044070   /var/cache/fontconfig/e9e44584608a73233979f764b5f9dd81-x86.cache-2
b4ed3000-b4ed4000 r--s 00000000 08:01 10044068   /var/cache/fontconfig/b5a4f3f568a71026ccdc6a3a51afa9b4-x86.cache-2
b4ed4000-b4ed5000 r--s 00000000 08:01 10044066   /var/cache/fontconfig/2561679576a9c7fd2ce41d281d4e00d1-x86.cache-2
b4ed5000-b4ed6000 r--s 00000000 08:01 10044065   /var/cache/fontconfig/bf1f9632594a1fa28e2cf4d7888deffe-x86.cache-2
b4ed6000-b4ed9000 r--s 00000000 08:01 10044063   /var/cache/fontconfig/b8613a33de00eecd32d5a94c3c617829-x86.cache-2
b4ed9000-b4edc000 r--s 00000000 08:01 10044062   /var/cache/fontconfig/b21a91cee725896328b8cee8091cf747-x86.cache-2
b4edc000-b4ee5000 r--s 00000000 08:01 10044061   /var/cache/fontconfig/fd9416c4b92f07c6f59a3a8cf496e9dc-x86.cache-2
b4ee5000-b4ee7000 r--s 00000000 08:01 10044060   /var/cache/fontconfig/059138ec877db160474b4d5de1248d14-x86.cache-2
b4ee7000-b4ee8000 r--s 00000000 08:01 10044058   /var/cache/fontconfig/f5a93ac943883aa0fd9a7bfe0f6ec3c1-x86.cache-2
b4ee8000-b4eea000 r--s 00000000 08:01 10044055   /var/cache/fontconfig/118d8d5311348bbdf5fe3b106d7c13d4-x86.cache-2
b4eea000-b4eeb000 r--s 00000000 08:01 10044054   /var/cache/fontconfig/a1131b7be650f9abae4907495aa5815d-x86.cache-2
b4eeb000-b4ef0000 r--s 00000000 08:01 10044053   /var/cache/fontconfig/8ab5f685cd6d8ba67c37c908faf08172-x86.cache-2
b4ef0000-b4ef4000 r--s 00000000 08:01 10044052   /var/cache/fontconfig/0f32d3adc6a232110812e17374eaa446-x86.cache-2
b4ef4000-b4ef6000 r--s 00000000 08:01 10044051   /var/cache/fontconfig/7b4a97c10f6c0166998ddfa1cf7392fb-x86.cache-2
b4ef6000-b4ef9000 r--s 00000000 08:01 10044050   /var/cache/fontconfig/61c830dfac3fd78a12654da5e9ba3f56-x86.cache-2
b4ef9000-b4efa000 r--s 00000000 08:01 10044049   /var/cache/fontconfig/e0f9e95429e756d56293ed4d63866094-x86.cache-2
b4efa000-b4efb000 r--s 00000000 08:01 10044048   /var/cache/fontconfig/892f88ea27b235637f494d515247eddd-x86.cache-2
b4efb000-b4efd000 r--s 00000000 08:01 10044047   /var/cache/fontconfig/4123634e9c08547d899d0aaff05ebe69-x86.cache-2
b4efd000-b4f03000 r--s 00000000 08:01 10044046   /var/cache/fontconfig/142ecfc435bad6f1fbc2648c1119d5eb-x86.cache-2
b4f03000-b4f09000 r--s 00000000 08:01 10044045   /var/cache/fontconfig/102e5142c2e9e50c5e8ece26694a2dad-x86.cache-2
b4f09000-b4f12000 r--s 00000000 08:01 10044042   /var/cache/fontconfig/a960c40fc9306f090224a04585f8a963-x86.cache-2
b4f12000-b4f17000 r--s 00000000 08:01 10044041   /var/cache/fontconfig/9404ff413c67fc2a1526fd14eb4163a8-x86.cache-2
b4f17000-b5290000 r--p 00000000 08:01 7018213    /usr/share/icons/hicolor/icon-theme.cache
b5290000-b63a3000 r--p 00000000 08:01 8011777    /usr/share/icons/crystalsvg/icon-theme.cache
b63a3000-b6a50000 r--p 00000000 08:01 6475151    /usr/share/icons/gnome/icon-theme.cache
b6a50000-b6ca7000 r--p 00000000 08:01 6475136    /usr/share/icons/Tango/icon-theme.cache
b6ca7000-b6cc3000 r-xp 00000000 08:01 6193561    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6cc3000-b6cc4000 rw-p 0001b000 08:01 6193561    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6cc4000-b6d24000 rw-s 00000000 00:08 1015813    /SYSV00000000 (deleted)
b6d24000-b6d81000 rw-p b6d24000 00:00 0 
b6d81000-b6d88000 r-xp 00000000 08:01 6145474    /usr/lib/libfam.so.0.0.0
b6d88000-b6d89000 rw-p 00006000 08:01 6145474    /usr/lib/libfam.so.0.0.0
b6d89000-b6d8f000 r-xp 00000000 08:01 688155     /lib/libacl.so.1.1.0
b6d8f000-b6d90000 rw-p 00005000 08:01 688155     /lib/libacl.so.1.1.0
b6d92000-b6d96000 r--s 00000000 08:01 10044040   /var/cache/fontconfig/b3fedf7c409f006ca1a6fceffceb77cf-x86.cache-2
b6d96000-b6d9b000 r--s 00000000 08:01 10044038   /var/cache/fontconfig/6330322105e0c4105d7c7a6ea2974107-x86.cache-2
b6d9b000-b6da2000 r--s 00000000 08:01 10043803   /var/cache/fontconfig/beeeeb3dfe132a8a0633a017c99ce0c0-x86.cache-2
b6da2000-b6da6000 r-xp 00000000 08:01 6193596    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6da6000-b6da7000 rw-p 00003000 08:01 6193596    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b6da7000-b6db3000 r-xp 00000000 08:01 6193519    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6db3000-b6db4000 rw-p 0000b000 08:01 6193519    /usr/lib/gnome-vfs-2.0/modules/libfile.so
b6db4000-b6db5000 r-xp 00000000 08:01 7733430    /usr/lib/gconv/ISO8859-1.so
b6db5000-b6db7000 rw-p 00000000 08:01 7733430    /usr/lib/gconv/ISO8859-1.so
b6db7000-b6df2000 r--p 00000000 08:01 6194510    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6df2000-b6ec9000 r--p 00000000 08:01 6194509    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ec9000-b6ed2000 r-xp 00000000 08:01 722195     /lib/tls/i686/cmov/libnss_files-2.5.so
b6ed2000-b6ed4000 rw-p 00008000 08:01 722195     /lib/tls/i686/cmov/libnss_files-2.5.so
b6ed4000-b6edc000 r-xp 00000000 08:01 722199     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6edc000-b6ede000 rw-p 00007000 08:01 722199     /lib/tls/i686/cmov/libnss_nis-2.5.so
b6ede000-b6ee5000 r-xp 00000000 08:01 722191     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ee5000-b6ee7000 rw-p 00006000 08:01 722191     /lib/tls/i686/cmov/libnss_compat-2.5.so
b6ee7000-b6eea000 rw-p b6ee7000 00:00 0 
b6eea000-b6f20000 r-xp 00000000 08:01 688246     /lib/libsepol.so.1
b6f20000-b6f21000 rw-p 00035000 08:01 688246     /lib/libsepol.so.1
b6f21000-b6f2b000 rw-p b6f21000 00:00 0 
b6f2b000-b6f2e000 r-xp 00000000 08:01 6145627    /usr/lib/libgpg-error.so.0.3.0
b6f2e000-b6f2f000 rw-p 00002000 08:01 6145627    /usr/lib/libgpg-error.so.0.3.0
b6f2f000-b6f7e000 r-xp 00000000 08:01 6145515    /usr/lib/libgcrypt.so.11.2.2
b6f7e000-b6f80000 rw-p 0004e000 08:01 6145515    /usr/lib/libgcrypt.so.11.2.2
b6f80000-b6f81000 rw-p b6f80000 00:00 0 
b6f81000-b6f95000 r-xp 00000000 08:01 6145971    /usr/lib/libtasn1.so.3.0.6
b6f95000-b6f96000 rw-p 00013000 08:01 6145971    /usr/lib/libtasn1.so.3.0.6
b6f96000-b6f98000 r-xp 00000000 08:01 722212     /lib/tls/i686/cmov/libutil-2.5.so
b6f98000-b6f9a000 rw-p 00001000 08:01 722212     /lib/tls/i686/cmov/libutil-2.5.so
b6f9a000-b6fae000 r-xp 00000000 08:01 688245     /lib/libselinux.so.1
b6fae000-b6fb0000 rw-p 00013000 08:01 688245     /lib/libselinux.so.1
b6fb0000-b6fbf000 r-xp 00000000 08:01 722206     /lib/tls/i686/cmov/libresolv-2.5.so
b6fbf000-b6fc1000 rw-p 0000f000 08:01 722206     /lib/tls/i686/cmov/libresolv-2.5.so
b6fc1000-b6fc3000 rw-p b6fc1000 00:00 0 
b6fc3000-b6fd1000 r-xp 00000000 08:01 6145353    /usr/lib/libavahi-client.so.3.2.2
b6fd1000-b6fd2000 rw-p 0000e000 08:01 6145353    /usr/lib/libavahi-client.so.3.2.2
b6fd2000-b6fd3000 rw-p b6fd2000 00:00 0 
b6fd3000-b6fdd000 r-xp 00000000 08:01 6145355    /usr/lib/libavahi-common.so.3.4.3
b6fdd000-b6fde000 rw-p 00009000 08:01 6145355    /usr/lib/libavahi-common.so.3.4.3
b6fde000-b6fe0000 r-xp 00000000 08:01 6145359    /usr/lib/libavahi-glib.so.1.0.1
b6fe0000-b6fe1000 rw-p 00001000 08:01 6145359    /usr/lib/libavahi-glib.so.1.0.1
b6fe1000-b704b000 r-xp 00000000 08:01 6145623    /usr/lib/libgnutls.so.13.0.9
b704b000-b7051000 rw-p 0006a000 08:01 6145623    /usr/lib/libgnutls.so.13.0.9
b7051000-b7073000 r-xp 00000000 08:01 6145466    /usr/lib/libpng12.so.0.15.0
b7073000-b7074000 rw-p 00021000 08:01 6145466    /usr/lib/libpng12.so.0.15.0
b7074000-b7092000 r-xp 00000000 08:01 6145470    /usr/lib/libexpat.so.1.0.0
b7092000-b7094000 rw-p 0001d000 08:01 6145470    /usr/lib/libexpat.so.1.0.0
b7094000-b7095000 rw-p b7094000 00:00 0 
b7095000-b70fd000 r-xp 00000000 08:01 6147688    /usr/lib/libfreetype.so.6.3.10
b70fd000-b7100000 rw-p 00068000 08:01 6147688    /usr/lib/libfreetype.so.6.3.10
b7100000-b7113000 r-xp 00000000 08:01 6146029    /usr/lib/libz.so.1.2.3
b7113000-b7114000 rw-p 00012000 08:01 6146029    /usr/lib/libz.so.1.2.3
b7114000-b7127000 r-xp 00000000 08:01 722189     /lib/tls/i686/cmov/libnsl-2.5.so
b7127000-b7129000 rw-p 00012000 08:01 722189     /lib/tls/i686/cmov/libnsl-2.5.so
b7129000-b712b000 rw-p b7129000 00:00 0 
b712b000-b712f000 r-xp 00000000 08:01 6145260    /usr/lib/libORBitCosNaming-2.so.0.1.0
b712f000-b7130000 rw-p 00003000 08:01 6145260    /usr/lib/libORBitCosNaming-2.so.0.1.0
b7130000-b7131000 rw-p b7130000 00:00 0 
b7131000-b7135000 r-xp 00000000 08:01 6145285    /usr/lib/libXdmcp.so.6.0.0
b7135000-b7136000 rw-p 00003000 08:01 6145285    /usr/lib/libXdmcp.so.6.0.0
b7136000-b7154000 r-xp 00000000 08:01 6145752    /usr/lib/libjpeg.so.62.0.0
b7154000-b7155000 rw-p 0001d000 08:01 6145752    /usr/lib/libjpeg.so.62.0.0
b7155000-b715d000 r-xp 00000000 08:01 6145961    /usr/lib/libstartup-notification-1.so.0.0.0
b715d000-b715e000 rw-p 00007000 08:01 6145961    /usr/lib/libstartup-notification-1.so.0.0.0
b715e000-b715f000 rw-p b715e000 00:00 0 
b715f000-b7166000 r-xp 00000000 08:01 722208     /lib/tls/i686/cmov/librt-2.5.so
b7166000-b7168000 rw-p 00006000 08:01 722208     /lib/tls/i686/cmov/librt-2.5.so
b7168000-b716c000 r-xp 00000000 08:01 6145679    /usr/lib/libgthread-2.0.so.0.1200.11
b716c000-b716d000 rw-p 00003000 08:01 6145679    /usr/lib/libgthread-2.0.so.0.1200.11
b716d000-b716f000 r-xp 00000000 08:01 722184     /lib/tls/i686/cmov/libdl-2.5.so
b716f000-b7171000 rw-p 00001000 08:01 722184     /lib/tls/i686/cmov/libdl-2.5.so
b7171000-b7173000 r-xp 00000000 08:01 6145581    /usr/lib/libgmodule-2.0.so.0.1200.11
b7173000-b7174000 rw-p 00002000 08:01 6145581    /usr/lib/libgmodule-2.0.so.0.1200.11
b7174000-b71ca000 r-xp 00000000 08:01 6145615    /usr/lib/libgnomevfs-2.so.0.1800.1
b71ca000-b71cd000 rw-p 00055000 08:01 6145615    /usr/lib/libgnomevfs-2.so.0.1800.1
b71cd000-b723b000 r-xp 00000000 08:01 6145378    /usr/lib/libcairo.so.2.11.1
b723b000-b723d000 rw-p 0006d000 08:01 6145378    /usr/lib/libcairo.so.2.11.1
b723d000-b723e000 rw-p b723d000 00:00 0 
b723e000-b7242000 r-xp 00000000 08:01 6145291    /usr/lib/libXfixes.so.3.1.0
b7242000-b7243000 rw-p 00003000 08:01 6145291    /usr/lib/libXfixes.so.3.1.0
b7243000-b724b000 r-xp 00000000 08:01 6145281    /usr/lib/libXcursor.so.1.0.2
b724b000-b724c000 rw-p 00007000 08:01 6145281    /usr/lib/libXcursor.so.1.0.2
b724c000-b7253000 r-xp 00000000 08:01 6145297    /usr/lib/libXi.so.6.0.0
b7253000-b7254000 rw-p 00006000 08:01 6145297    /usr/lib/libXi.so.6.0.0
b7254000-b7256000 r-xp 00000000 08:01 6145299    /usr/lib/libXinerama.so.1.0.0
b7256000-b7257000 rw-p 00001000 08:01 6145299    /usr/lib/libXinerama.so.1.0.0
b7257000-b725e000 r-xp 00000000 08:01 6145311    /usr/lib/libXrender.so.1.3.0
b725e000-b725f000 rw-p 00006000 08:01 6145311    /usr/lib/libXrender.so.1.3.0
b725f000-b726c000 r-xp 00000000 08:01 6145289    /usr/lib/libXext.so.6.4.0
b726c000-b726d000 rw-p 0000d000 08:01 6145289    /usr/lib/libXext.so.6.4.0
b726d000-b726e000 rw-p b726d000 00:00 0 
b726e000-b7291000 r-xp 00000000 08:01 6145476    /usr/lib/libfontconfig.so.1.2.0
b7291000-b7299000 rw-p 00023000 08:01 6145476    /usr/lib/libfontconfig.so.1.2.0
b7299000-b72a0000 r-xp 00000000 08:01 6145860    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72a0000-b72a1000 rw-p 00007000 08:01 6145860    /usr/lib/libpangocairo-1.0.so.0.1600.2
b72a1000-b72cb000 r-xp 00000000 08:01 6145862    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72cb000-b72cc000 rw-p 0002a000 08:01 6145862    /usr/lib/libpangoft2-1.0.so.0.1600.2
b72cc000-b72e0000 r-xp 00000000 08:01 6145337    /usr/lib/libart_lgpl_2.so.2.3.17
b72e0000-b72e1000 rw-p 00013000 08:01 6145337    /usr/lib/libart_lgpl_2.so.2.3.17
b72e1000-b72e8000 r-xp 00000000 08:01 688235     /lib/libpopt.so.0.0.0
b72e8000-b72e9000 rw-p 00006000 08:01 688235     /lib/libpopt.so.0.0.0
b72e9000-b7312000 r-xp 00000000 08:01 6145597    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7312000-b7313000 rw-p 00029000 08:01 6145597    /usr/lib/libgnomecanvas-2.so.0.1400.0
b7313000-b7314000 rw-p b7313000 00:00 0 
b7314000-b736f000 r-xp 00000000 08:01 6145374    /usr/lib/libbonoboui-2.so.0.0.0
b736f000-b7372000 rw-p 0005a000 08:01 6145374    /usr/lib/libbonoboui-2.so.0.0.0
b7372000-b7489000 r-xp 00000000 08:01 6146023    /usr/lib/libxml2.so.2.6.27
b7489000-b748f000 rw-p 00116000 08:01 6146023    /usr/lib/libxml2.so.2.6.27
b748f000-b754f000 r-xp 00000000 08:01 6145339    /usr/lib/libasound.so.2.0.0
b754f000-b7554000 rw-p 000bf000 08:01 6145339    /usr/lib/libasound.so.2.0.0
b7554000-b7579000 r-xp 00000000 08:01 722186     /lib/tls/i686/cmov/libm-2.5.so
b7579000-b757b000 rw-p 00024000 08:01 722186     /lib/tls/i686/cmov/libm-2.5.so
b757b000-b759b000 r-xp 00000000 08:01 6145351    /usr/lib/libaudiofile.so.0.0.2
b759b000-b759d000 rw-p 00020000 08:01 6145351    /usr/lib/libaudiofile.so.0.0.2
b759d000-b76d8000 r-xp 00000000 08:01 722178     /lib/tls/i686/cmov/libc-2.5.so
b76d8000-b76d9000 r--p 0013b000 08:01 722178     /lib/tls/i686/cmov/libc-2.5.so
b76d9000-b76db000 rw-p 0013c000 08:01 722178     /lib/tls/i686/cmov/libc-2.5.so
b76db000-b76df000 rw-p b76db000 00:00 0 
b76df000-b76e6000 r-xp 00000000 08:01 688266     /lib/libwrap.so.0.7.6
b76e6000-b76e7000 rw-p 00007000 08:01 688266     /lib/libwrap.so.0.7.6
b76e7000-b777b000 r-xp 00000000 08:01 6145571    /usr/lib/libglib-2.0.so.0.1200.11
b777b000-b777c000 rw-p 00093000 08:01 6145571    /usr/lib/libglib-2.0.so.0.1200.11
b777c000-b7788000 r-xp 00000000 08:01 6145587    /usr/lib/libgnome-keyring.so.0.0.1
b7788000-b7789000 rw-p 0000b000 08:01 6145587    /usr/lib/libgnome-keyring.so.0.0.1
b7789000-b77c2000 r-xp 00000000 08:01 6145625    /usr/lib/libgobject-2.0.so.0.1200.11
b77c2000-b77c3000 rw-p 00039000 08:01 6145625    /usr/lib/libgobject-2.0.so.0.1200.11
b77c3000-b77f5000 r-xp 00000000 08:01 6145781    /usr/lib/libdbus-1.so.3.2.0
b77f5000-b77f6000 rw-p 00031000 08:01 6145781    /usr/lib/libdbus-1.so.3.2.0
b77f6000-b7810000 r-xp 00000000 08:01 6145414    /usr/lib/libdbus-glib-1.so.2.1.0
b7810000-b7811000 rw-p 0001a000 08:01 6145414    /usr/lib/libdbus-glib-1.so.2.1.0
b7811000-b7812000 rw-p b7811000 00:00 0 
b7812000-b7825000 r-xp 00000000 08:01 722204     /lib/tls/i686/cmov/libpthread-2.5.so
b7825000-b7827000 rw-p 00013000 08:01 722204     /lib/tls/i686/cmov/libpthread-2.5.so
b7827000-b7829000 rw-p b7827000 00:00 0 
b7829000-b7872000 r-xp 00000000 08:01 6145256    /usr/lib/libORBit-2.so.0.1.0
b7872000-b787c000 rw-p 00048000 08:01 6145256    /usr/lib/libORBit-2.so.0.1.0
b787c000-b78ab000 r-xp 00000000 08:01 6145513    /usr/lib/libgconf-2.so.4.1.2
b78ab000-b78ae000 rw-p 0002e000 08:01 6145513    /usr/lib/libgconf-2.so.4.1.2
b78ae000-b78c1000 r-xp 00000000 08:01 6145372    /usr/lib/libbonobo-activation.so.4.0.0
b78c1000-b78c3000 rw-p 00013000 08:01 6145372    /usr/lib/libbonobo-activation.so.4.0.0
b78c3000-b7915000 r-xp 00000000 08:01 6145370    /usr/lib/libbonobo-2.so.0.0.0
b7915000-b791f000 rw-p 00051000 08:01 6145370    /usr/lib/libbonobo-2.so.0.0.0
b791f000-b7920000 rw-p b791f000 00:00 0 
b7920000-b7a0d000 r-xp 00000000 08:01 6145268    /usr/lib/libX11.so.6.2.0
b7a0d000-b7a11000 rw-p 000ed000 08:01 6145268    /usr/lib/libX11.so.6.2.0
b7a11000-b7a4d000 r-xp 00000000 08:01 6145858    /usr/lib/libpango-1.0.so.0.1600.2
b7a4d000-b7a4f000 rw-p 0003b000 08:01 6145858    /usr/lib/libpango-1.0.so.0.1600.2
b7a4f000-b7a54000 r-xp 00000000 08:01 6145309    /usr/lib/libXrandr.so.2.1.0
b7a54000-b7a55000 rw-p 00005000 08:01 6145309    /usr/lib/libXrandr.so.2.1.0
b7a55000-b7a6b000 r-xp 00000000 08:01 6145535    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a6b000-b7a6c000 rw-p 00015000 08:01 6145535    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a6c000-b7a85000 r-xp 00000000 08:01 6145345    /usr/lib/libatk-1.0.so.0.1809.1
b7a85000-b7a87000 rw-p 00018000 08:01 6145345    /usr/lib/libatk-1.0.so.0.1809.1
b7a87000-b7b0a000 r-xp 00000000 08:01 6145533    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b0a000-b7b0d000 rw-p 00083000 08:01 6145533    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7b0d000-b7b0e000 rw-p b7b0d000 00:00 0 
b7b0e000-b7e5f000 r-xp 00000000 08:01 6145682    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e5f000-b7e65000 rw-p 00351000 08:01 6145682    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7e65000-b7e66000 rw-p b7e65000 00:00 0 
b7e66000-b7e7a000 r-xp 00000000 08:01 6145583    /usr/lib/libgnome-2.so.0.1800.0
b7e7a000-b7e7b000 rw-p 00014000 08:01 6145583    /usr/lib/libgnome-2.so.0.1800.0
b7e7b000-b7e90000 r-xp 00000000 08:01 6145246    /usr/lib/libICE.so.6.3.0
b7e90000-b7e92000 rw-p 00014000 08:01 6145246    /usr/lib/libICE.so.6.3.0
b7e92000-b7e93000 rw-p b7e92000 00:00 0 
b7e93000-b7e9b000 r-xp 00000000 08:01 6145264    /usr/lib/libSM.so.6.0.0
b7e9b000-b7e9c000 rw-p 00007000 08:01 6145264    /usr/lib/libSM.so.6.0.0
b7e9c000-b7f26000 r-xp 00000000 08:01 6145613    /usr/lib/libgnomeui-2.so.0.1788.4
b7f26000-b7f2a000 rw-p 00089000 08:01 6145613    /usr/lib/libgnomeui-2.so.0.1788.4
b7f2a000-b7f3e000 r-xp 00000000 08:01 6145585    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f3e000-b7f3f000 rw-p 00014000 08:01 6145585    /usr/lib/libgnome-desktop-2.so.2.3.5
b7f3f000-b7f40000 rw-p b7f3f000 00:00 0 
b7f40000-b7f49000 r-xp 00000000 08:01 6145461    /usr/lib/libesd.so.0.2.36
b7f49000-b7f4a000 rw-p 00009000 08:01 6145461    /usr/lib/libesd.so.0.2.36
b7f4a000-b7f4c000 r-xp 00000000 08:01 6145274    /usr/lib/libXau.so.6.0.0
b7f4c000-b7f4d000 rw-p 00001000 08:01 6145274    /usr/lib/libXau.so.6.0.0
b7f4e000-b7f4f000 r--s 00000000 08:01 10044044   /var/cache/fontconfig/92a571655fb1c0ec1c4d6f496220600a-x86.cache-2
b7f4f000-b7f52000 r-xp 00000000 08:01 688159     /lib/libattr.so.1.1.0
b7f52000-b7f53000 rw-p 00002000 08:01 688159     /lib/libattr.so.1.1.0
b7f53000-b7f54000 r--p 00000000 08:01 6194515    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b7f54000-b7f55000 r--p 00000000 08:01 6194518    /usr/lib/locale/en_US.utf8/LC_TIME
b7f55000-b7f56000 r--p 00000000 08:01 6194513    /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f56000-b7f57000 r--p 00000000 08:01 6209594    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f57000-b7f58000 r--p 00000000 08:01 6194516    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f58000-b7f59000 r--p 00000000 08:01 6194514    /usr/lib/locale/en_US.utf8/LC_NAME
b7f59000-b7f5a000 r--p 00000000 08:01 6194508    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f5a000-b7f5b000 r--p 00000000 08:01 6194517    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f5b000-b7f5c000 r--p 00000000 08:01 6194512    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f5c000-b7f63000 r--s 00000000 08:01 7733483    /usr/lib/gconv/gconv-modules.cache
b7f63000-b7f64000 r--p 00000000 08:01 6194511    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f64000-b7f66000 rw-p b7f64000 00:00 0 
b7f66000-b7f7f000 r-xp 00000000 08:01 688149     /lib/ld-2.5.so
b7f7f000-b7f81000 rw-p 00019000 08:01 688149     /lib/ld-2.5.so
bfd68000-bfd7e000 rw-p bfd68000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]

(update-notifier:6345): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:2: Unable to find include file: "iconrc"
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:54: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:55: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:56: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/codeshiftster/.themes/T-ish-Brushed/gtk-2.0/gtkrc:57: Clearlooks configuration option "progressbarstyle" is not supported and will be ignored.
Session management error: IO error occured opening connection

(evolution-alarm-notify:6352): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6353): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
evolution-alarm-notify-Message: Setting timeout for 83730 1186722000 1186638270
evolution-alarm-notify-Message:  Fri Aug 10 00:00:00 2007

evolution-alarm-notify-Message:  Thu Aug  9 00:44:30 2007





so...  I know there's a quick fix to this somewhere but I can't even reopen gnome-sessiond (AKA System>Preferences>Sessions)

---

### Post by Kralizec on 2007-08-09
Check out this thread:

[http://ubuntuforums.org/showthread.php?p=1597472]("http://ubuntuforums.org/showthread.php?p=1597472")

It should at least get you back to a usable desktop.

---

