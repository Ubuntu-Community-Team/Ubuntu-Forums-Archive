---
title: "Kiba Only loads Under root"
date: 2007-04-30
forum: Desktop Effects &amp; Customization
---

### Post by SableSlayer on 2007-04-30
I've installed Kiba-Dock and got it to work, but the problem is that it will only run under root. I would like to be able to add it to my session. 

This is what i get when i try to do it on my normal user
```

*** glibc detected *** gset-kiba: double free or corruption (fasttop): 0x08312328 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb77007cd]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7703e30]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb780f131]
gset-kiba[0x804bc55]
gset-kiba[0x804dcfe]
gset-kiba[0x804b7bc]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb76aeebc]
gset-kiba[0x804b5b1]
======= Memory map: ========
08048000-08054000 r-xp 00000000 03:01 5511295    /usr/bin/gset-kiba
08054000-08055000 rw-p 0000b000 03:01 5511295    /usr/bin/gset-kiba
08055000-0831e000 rw-p 08055000 00:00 0          [heap]
b3d00000-b3d21000 rw-p b3d00000 00:00 0 
b3d21000-b3e00000 ---p b3d21000 00:00 0 
b3e42000-b3e4d000 r-xp 00000000 03:01 1949760    /lib/libgcc_s.so.1
b3e4d000-b3e4e000 rw-p 0000a000 03:01 1949760    /lib/libgcc_s.so.1
b3e5e000-b4044000 r--p 00000000 03:01 5886691    /usr/share/icons/hicolor/icon-theme.cache
b4044000-b512c000 r--p 00000000 03:01 6099068    /usr/share/icons/crystalsvg/icon-theme.cache
b512c000-b57d3000 r--p 00000000 03:01 5886687    /usr/share/icons/gnome/icon-theme.cache
b57d3000-b5a2a000 r--p 00000000 03:01 5884984    /usr/share/icons/Tango/icon-theme.cache
b5a2a000-b5acb000 r--p 00000000 03:01 5883787    /usr/share/icons/Tangerine/icon-theme.cache
b5acb000-b5c31000 r--p 00000000 03:01 5882241    /usr/share/icons/Human/icon-theme.cache
b5c31000-b5c32000 ---p b5c31000 00:00 0 
b5c32000-b6432000 rw-p b5c32000 00:00 0 
b6432000-b6433000 ---p b6432000 00:00 0 
b6433000-b6c33000 rw-p b6433000 00:00 0 
b6c33000-b6c3a000 r-xp 00000000 03:01 5506749    /usr/lib/libfam.so.0.0.0
b6c3a000-b6c3b000 rw-p 00006000 03:01 5506749    /usr/lib/libfam.so.0.0.0
b6c3b000-b6c41000 r-xp 00000000 03:01 1949723    /lib/libacl.so.1.1.0
b6c41000-b6c42000 rw-p 00005000 03:01 1949723    /lib/libacl.so.1.1.0
b6c42000-b6c45000 r-xp 00000000 03:01 1949727    /lib/libattr.so.1.1.0
b6c45000-b6c46000 rw-p 00002000 03:01 1949727    /lib/libattr.so.1.1.0
b6c56000-b6c8c000 r-xp 00000000 03:01 1949814    /lib/libsepol.so.1
b6c8c000-b6c8d000 rw-p 00035000 03:01 1949814    /lib/libsepol.so.1
b6c8d000-b6c97000 rw-p b6c8d000 00:00 0 
b6c97000-b6c9a000 r-xp 00000000 03:01 5506902    /usr/lib/libgpg-error.so.0.3.0
b6c9a000-b6c9b000 rw-p 00002000 03:01 5506902    /usr/lib/libgpg-error.so.0.3.0
b6c9b000-b6cea000 r-xp 00000000 03:01 5506790    /usr/lib/libgcrypt.so.11.2.2
b6cea000-b6cec000 rw-p 0004e000 03:01 5506790    /usr/lib/libgcrypt.so.11.2.2
b6cec000-b6d00000 r-xp 00000000 03:01 5507246    /usr/lib/libtasn1.so.3.0.6
b6d00000-b6d01000 rw-p 00013000 03:01 5507246    /usr/lib/libtasn1.so.3.0.6
b6d01000-b6dc1000 r-xp 00000000 03:01 5506614    /usr/lib/libasound.so.2.0.0
b6dc1000-b6dc6000 rw-p 000bf000 03:01 5506614    /usr/lib/libasound.so.2.0.0
b6dc6000-b6ddb000 r-xp 00000000 03:01 5506521    /usr/lib/libICE.so.6.3.0
b6ddb000-b6ddd000 rw-p 00014000 03:01 5506521    /usr/lib/libICE.so.6.3.0
b6ddd000-b6dde000 rw-p b6ddd000 00:00 0 
b6dde000-b6de6000 r-xp 00000000 03:01 5506539    /usr/lib/libSM.so.6.0.0
b6de6000-b6de7000 rw-p 00007000 03:01 5506539    /usr/lib/libSM.so.6.0.0
b6de7000-b6e05000 r-xp 00000000 03:01 5507027    /usr/lib/libjpeg.so.62.0.0
b6e05000-b6e06000 rw-p 0001d000 03:01 5507027    /usr/lib/libjpeg.so.62.0.0
b6e06000-b6e12000 r-xp 00000000 03:01 5506862    /usr/lib/libgnome-keyring.so.0.0.1
b6e12000-b6e13000 rw-p 0000b000 03:01 5506862    /usr/lib/libgnome-keyring.so.0.0.1
b6e13000-b6e27000 r-xp 00000000 03:01 5506612    /usr/lib/libart_lgpl_2.so.2.3.17
b6e27000-b6e28000 rw-p 00013000 03:01 5506612    /usr/lib/libart_lgpl_2.so.2.3.17
b6e28000-b6e51000 r-xp 00000000 03:01 5506872    /usr/lib/libgnomecanvas-2.so.0.1400.0
b6e51000-b6e52000 rw-p 00029000 03:01 5506872    /usr/lib/libgnomecanvas-2.so.0.1400.0
b6e52000-b6ead000 r-xp 00000000 03:01 5506649    /usr/lib/libbonoboui-2.so.0.0.0
b6ead000-b6eb0000 rw-p 0005a000 03:01 5506649    /usr/lib/libbonoboui-2.so.0.0.0
b6eb0000-b6eb2000 r-xp 00000000 03:01 1953030    /lib/tls/i686/cmov/libutil-2.5.so
b6eb2000-b6eb4000 rw-p 00001000 03:01 1953030    /lib/tls/i686/cmov/libutil-2.5.so
b6eb4000-b6ec8000 r-xp 00000000 03:01 1949813    /lib/libselinux.so.1
b6ec8000-b6eca000 rw-p 00013000 03:01 1949813    /lib/libselinux.so.1
b6eca000-b6ed9000 r-xp 00000000 03:01 1953024    /lib/tls/i686/cmov/libresolv-2.5.so
b6ed9000-b6edb000 rw-p 0000f000 03:01 1953024    /lib/tls/i686/cmov/libresolv-2.5.so
b6edb000-b6edd000 rw-p b6edb000 00:00 0 
b6edd000-b6eeb000 r-xp 00000000 03:01 5506628    /usr/lib/libavahi-client.so.3.2.2
b6eeb000-b6eec000 rw-p 0000e000 03:01 5506628    /usr/lib/libavahi-client.so.3.2.2
b6eec000-b6ef6000 r-xp 00000000 03:01 5506630    /usr/lib/libavahi-common.so.3.4.3
b6ef6000-b6ef7000 rw-p 00009000 03:01 5506630    /usr/lib/libavahi-common.so.3.4.3
b6ef7000-b6f61000 r-xp 00000000 03:01 5506898    /usr/lib/libgnutls.so.13.0.9
b6f61000-b6f67000 rw-p 0006a000 03:01 5506898    /usr/lib/libgnutls.so.13.0.9
b6f67000-b6f98000 r-xp 00000000 03:01 5506687    /usr/lib/libdbus-1.so.3.2.0
b6f98000-b6f99000 rw-p 00031000 03:01 5506687    /usr/lib/libdbus-1.so.3.2.0
b6f99000-b6fb3000 r-xp 00000000 03:01 5506689    /usr/lib/libdbus-glib-1.so.2.1.0
b6fb3000-b6fb4000 rw-p 0001a000 03:01 5506689    /usr/lib/libdbus-glib-1.so.2.1.0
b6fb4000-b70cb000 r-xp 00000000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b70cb000-b70d1000 rw-p 00116000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b70d1000-b70d5000 r-xp 00000000 03:01 5506535    /usr/lib/libORBitCosNaming-2.so.0.1.0Aborted (core dumped)
sableslayer@XeN-desktop:~$ kiba-dock
*** glibc detected *** kiba-dock: malloc(): memory corruption (fast): 0x08094eb0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76446fc]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0x8d)[0xb764531d]
/usr/lib/libglib-2.0.so.0(g_malloc0+0x3e)[0xb79a922e]
/usr/lib/libgobject-2.0.so.0[0xb7a33e65]
/usr/lib/libgobject-2.0.so.0(g_type_register_static+0x3a0)[0xb7a3bf90]
/usr/lib/libatk-1.0.so.0(atk_implementor_get_type+0x44)[0xb7b45064]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_get_type+0x73)[0xb7e34443]
kiba-dock(kiba_get_type+0x2f)[0x805200f]
kiba-dock(kiba_new+0xc)[0x805205c]
kiba-dock(main+0x235)[0x8051235]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb75f1ebc]
kiba-dock[0x8050f71]
======= Memory map: ========
08048000-0806b000 r-xp 00000000 03:01 5512133    /usr/bin/kiba-dock
0806b000-0806d000 rw-p 00022000 03:01 5512133    /usr/bin/kiba-dock
0806d000-080af000 rw-p 0806d000 00:00 0          [heap]
b6700000-b6721000 rw-p b6700000 00:00 0 
b6721000-b6800000 ---p b6721000 00:00 0 
b690d000-b6916000 r-xp 00000000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b6916000-b6918000 rw-p 00008000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b6918000-b6920000 r-xp 00000000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6920000-b6922000 rw-p 00007000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b6922000-b6935000 r-xp 00000000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b6935000-b6937000 rw-p 00012000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b6937000-b6939000 rw-p b6937000 00:00 0 
b6939000-b6940000 r-xp 00000000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6940000-b6942000 rw-p 00006000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6943000-b694e000 r-xp 00000000 03:01 1949760    /lib/libgcc_s.so.1
b694e000-b694f000 rw-p 0000a000 03:01 1949760    /lib/libgcc_s.so.1
b694f000-b6950000 r-xp 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b6950000-b6952000 rw-p 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b6952000-b698d000 r--p 00000000 03:01 5571581    /usr/lib/locale/en_US.utf8/LC_CTYPE
b698d000-b698e000 r--p 00000000 03:01 5571586    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b698e000-b698f000 r--p 00000000 03:01 5571589    /usr/lib/locale/en_US.utf8/LC_TIME
b698f000-b6a66000 r--p 00000000 03:01 5571580    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6a66000-b6a67000 r--p 00000000 03:01 5571584    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6a67000-b6acc000 rw-p b6a67000 00:00 0 
b6acc000-b6adb000 r-xp 00000000 03:01 1949734    /lib/libbz2.so.1.0.3
b6adb000-b6adc000 rw-p 0000f000 03:01 1949734    /lib/libbz2.so.1.0.3
b6adc000-b6add000 r-xp 00000000 03:01 5571039    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b6add000-b6ade000 rw-p 00000000 03:01 5571039    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b6ade000-b6adf000 rw-p b6ade000 00:00 0 
b6adf000-b732c000 r-xp 00000000 03:01 5505753    /usr/lib/libGLcore.so.1.0.9631
b732c000-b7361000 rwxp 0084d000 03:01 5505753    /usr/lib/libGLcore.so.1.0.9631
b7361000-b7365000 rwxp b7361000 00:00 0 
b7365000-b7369000 r-xp 00000000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b7369000-b736a000 rw-p 00003000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b736a000-b738c000 r-xp 00000000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b738c000-b738d000 rw-p 00021000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b738d000-b74a4000 r-xp 00000000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b74a4000-b74aa000 rw-p 00116000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b74aa000-b74da000 r-xp 00000000 03:01 5506669    /usr/lib/libcroco-0.6.so.3.0.1
b74da000-b74dd000 rw-p 0002f000 03:01 5506669    /usr/lib/libcroco-0.6.so.3.0.1
b74dd000-b74de000 rw-p b74dd000 00:00 0 
b74de000-b750a000 r-xp 00000000 03:01 5506920    /usr/lib/libgsf-1.so.114.0.3
b750a000-b750d000 rw-p 0002b000 03:01 5506920    /usr/lib/libgsf-1.so.114.0.3
b750d000-b750e000 rw-p b750d000 00:00 0 
b750e000-b7538000 r-xp 00000000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7538000-b7539000 rw-p 0002a000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7539000-b753b000 r-xp 00000000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b753b000-b753c000 rw-p 00001000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b753c000-b755a000 r-xp 00000000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b755a000-b755c000 rw-p 0001d000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b755c000-b756f000 r-xp 00000000 03:01 5507304    /usr/lib/libz.so.1.2.3
b756f000-b7570000 rw-p 00012000 03:01 5507304    /usr/lib/libz.so.1.2.3
b7570000-b7571000 rw-p b7570000 00:00 0 
b7571000-b75d9000 r-xp 00000000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b75d9000-b75dc000 rw-p 00068000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b75dc000-b7717000 r-xp 00000000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7717000-b7718000 r--p 0013b000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7718000-b771a000 rw-p 0013c000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b771a000-b771d000 rw-p b771a000 00:00 0 
b771d000-b7742000 r-xp 00000000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b7742000-b7744000 rw-p 00024000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b7744000-b7768000 r-xp 00000000 03:01 5506654    /usr/lib/libglitz.so.1.0.0
b7768000-b7769000 rw-p 00024000 03:01 5506654    /usr/lib/libglitz.so.1.0.0
b7769000-b777c000 r-xp 00000000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b777c000-b777e000 rw-p 00013000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b777e000-b7781000 rw-p b777e000 00:00 0 
b7781000-b77f2000 r-xp 00000000 03:01 5505752    /usr/lib/libGL.so.1.0.9631
b77f2000-b780c000 rwxp 00070000 03:01 5505752    /usr/lib/libGL.so.1.0.9631
b780c000-b780d000 rwxp b780c000 00:00 0 
b780d000-b78fa000 r-xp 00000000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b78fa000-b78fe000 rw-p 000ed000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b78fe000-b7903000 r-xp 00000000 03:01 5506690    /usr/lib/libglitz-glx.so.1.0.0
b7903000-b7904000 rw-p 00004000 03:01 5506690    /usr/lib/libglitz-glx.so.1.0.0
b7904000-b7972000 r-xp 00000000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b7972000-b7974000 rw-p 0006d000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b7974000-b7a08000 r-xp 00000000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b7a08000-b7a09000 rw-p 00093000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b7a09000-b7a0b000 r-xp 00000000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b7a0b000-b7a0d000 rw-p 00001000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b7a0d000-b7a0e000 rw-p b7a0d000 00:00 0 
b7a0e000-b7a10000 r-xp 00000000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b7a10000-b7a11000 rw-p 00002000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b7a11000-b7a4a000 r-xp 00000000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b7a4a000-b7a4b000 rw-p 00039000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b7a4b000-b7a61000 r-xp 00000000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a61000-b7a62000 rw-p 00015000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7a62000-b7a91000 r-xp 00000000 03:01 5507190    /usr/lib/librsvg-2.so.2.16.0
b7a91000-b7a92000 rw-p 0002f000 03:01 5507190    /usr/lib/librsvg-2.so.2.16.0
b7a92000-b7ace000 r-xp 00000000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7ace000-b7ad0000 rw-p 0003b000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7ad0000-b7ad7000 r-xp 00000000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7ad7000-b7ad8000 rw-p 00007000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7ad8000-b7ad9000 rw-p b7ad8000 00:00 0 
b7ad9000-b7add000 r-xp 00000000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7add000-b7ade000 rw-p 00003000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7ade000-b7ae6000 r-xp 00000000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7ae6000-b7ae7000 rw-p 00007000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7ae7000-b7aec000 r-xp 00000000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7aec000-b7aed000 rw-p 00005000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7aed000-b7af4000 r-xp 00000000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7af4000-b7af5000 rw-p 00006000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7af5000-b7af7000 r-xp 00000000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7af7000-b7af8000 rw-p 00001000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7af8000-b7aff000 r-xp 00000000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7aff000-b7b00000 rw-p 00006000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7b00000-b7b01000 rw-p b7b00000 00:00 0 
b7b01000-b7b0e000 r-xp 00000000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7b0e000-b7b0f000 rw-p 0000d000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7b0f000-b7b32000 r-xp 00000000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7b32000-b7b3a000 rw-p 00023000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7b3a000-b7b53000 r-xp 00000000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7b53000-b7b55000 rw-p 00018000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7b55000-b7bd8000 r-xp 00000000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7bd8000-b7bdb000 rw-p 00083000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7bdb000-b7f2c000 r-xp 00000000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f2c000-b7f32000 rw-p 00351000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f32000-b7f33000 rw-p b7f32000 00:00 0 
b7f33000-b7f36000 r-xp 00000000 03:01 5511293    /usr/lib/libakamaru.so.0.0.0
b7f36000-b7f37000 rw-p 00002000 03:01 5511293    /usr/lib/libakamaru.so.0.0.0
b7f37000-b7f38000 rw-p b7f37000 00:00 0 
b7f38000-b7f39000 r--p 00000000 03:01 5571590    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f39000-b7f3a000 r--p 00000000 03:01 5571587    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f3a000-b7f3b000 r--p 00000000 03:01 5571585    /usr/lib/locale/en_US.utf8/LC_NAME
b7f3b000-b7f3c000 r--p 00000000 03:01 5571579    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f3c000-b7f3d000 r--p 00000000 03:01 5571588    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f3d000-b7f3e000 r--p 00000000 03:01 5571583    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f3e000-b7f45000 r--s 00000000 03:01 5508729    /usr/lib/gconv/gconv-modules.cache
b7f45000-b7f46000 r--p 00000000 03:01 5571582    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f46000-b7f48000 rwxp 00000000 00:0d 2701       /dev/zero
b7f48000-b7f49000 rw-p b7f48000 00:00 0 
b7f49000-b7f62000 r-xp 00000000 03:01 1949717    /lib/ld-2.5.so
b7f62000-b7f64000 rw-p 00019000 03:01 1949717    /lib/ld-2.5.so
bf969000-bf97e000 rwxp bf969000 00:00 0          [stack]
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)
sableslayer@XeN-desktop:~$ kiba
bash: kiba: command not found
sableslayer@XeN-desktop:~$ clear

sableslayer@XeN-desktop:~$ kiba-dock
*** glibc detected *** kiba-dock: malloc(): memory corruption (fast): 0x08094dd8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb76916fc]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0x8d)[0xb769231d]
/usr/lib/libglib-2.0.so.0(g_malloc0+0x3e)[0xb79f622e]
/usr/lib/libgobject-2.0.so.0[0xb7a80e65]
/usr/lib/libgobject-2.0.so.0(g_type_register_static+0x3a0)[0xb7a88f90]
/usr/lib/libatk-1.0.so.0(atk_implementor_get_type+0x44)[0xb7b92064]
/usr/lib/libgtk-x11-2.0.so.0(gtk_widget_get_type+0x73)[0xb7e81443]
kiba-dock(kiba_get_type+0x2f)[0x805200f]
kiba-dock(kiba_new+0xc)[0x805205c]
kiba-dock(main+0x235)[0x8051235]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb763eebc]
kiba-dock[0x8050f71]
======= Memory map: ========
08048000-0806b000 r-xp 00000000 03:01 5512133    /usr/bin/kiba-dock
0806b000-0806d000 rw-p 00022000 03:01 5512133    /usr/bin/kiba-dock
0806d000-080af000 rw-p 0806d000 00:00 0          [heap]
b6800000-b6821000 rw-p b6800000 00:00 0 
b6821000-b6900000 ---p b6821000 00:00 0 
b695a000-b6963000 r-xp 00000000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b6963000-b6965000 rw-p 00008000 03:01 1953013    /lib/tls/i686/cmov/libnss_files-2.5.so
b6965000-b696d000 r-xp 00000000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b696d000-b696f000 rw-p 00007000 03:01 1953017    /lib/tls/i686/cmov/libnss_nis-2.5.so
b696f000-b6982000 r-xp 00000000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b6982000-b6984000 rw-p 00012000 03:01 1953007    /lib/tls/i686/cmov/libnsl-2.5.so
b6984000-b6986000 rw-p b6984000 00:00 0 
b6986000-b698d000 r-xp 00000000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b698d000-b698f000 rw-p 00006000 03:01 1953009    /lib/tls/i686/cmov/libnss_compat-2.5.so
b6990000-b699b000 r-xp 00000000 03:01 1949760    /lib/libgcc_s.so.1
b699b000-b699c000 rw-p 0000a000 03:01 1949760    /lib/libgcc_s.so.1
b699c000-b699d000 r-xp 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b699d000-b699f000 rw-p 00000000 03:01 5508676    /usr/lib/gconv/ISO8859-1.so
b699f000-b69da000 r--p 00000000 03:01 5571581    /usr/lib/locale/en_US.utf8/LC_CTYPE
b69da000-b69db000 r--p 00000000 03:01 5571586    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b69db000-b69dc000 r--p 00000000 03:01 5571589    /usr/lib/locale/en_US.utf8/LC_TIME
b69dc000-b6ab3000 r--p 00000000 03:01 5571580    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6ab3000-b6ab4000 r--p 00000000 03:01 5571584    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6ab4000-b6b19000 rw-p b6ab4000 00:00 0 
b6b19000-b6b28000 r-xp 00000000 03:01 1949734    /lib/libbz2.so.1.0.3
b6b28000-b6b29000 rw-p 0000f000 03:01 1949734    /lib/libbz2.so.1.0.3
b6b29000-b6b2a000 r-xp 00000000 03:01 5571039    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b6b2a000-b6b2b000 rw-p 00000000 03:01 5571039    /usr/lib/tls/libnvidia-tls.so.1.0.9631
b6b2b000-b6b2c000 rw-p b6b2b000 00:00 0 
b6b2c000-b7379000 r-xp 00000000 03:01 5505753    /usr/lib/libGLcore.so.1.0.9631
b7379000-b73ae000 rwxp 0084d000 03:01 5505753    /usr/lib/libGLcore.so.1.0.9631
b73ae000-b73b2000 rwxp b73ae000 00:00 0 
b73b2000-b73b6000 r-xp 00000000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b73b6000-b73b7000 rw-p 00003000 03:01 5506560    /usr/lib/libXdmcp.so.6.0.0
b73b7000-b73d9000 r-xp 00000000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b73d9000-b73da000 rw-p 00021000 03:01 5507158    /usr/lib/libpng12.so.0.15.0
b73da000-b74f1000 r-xp 00000000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b74f1000-b74f7000 rw-p 00116000 03:01 5507298    /usr/lib/libxml2.so.2.6.27
b74f7000-b7527000 r-xp 00000000 03:01 5506669    /usr/lib/libcroco-0.6.so.3.0.1
b7527000-b752a000 rw-p 0002f000 03:01 5506669    /usr/lib/libcroco-0.6.so.3.0.1
b752a000-b752b000 rw-p b752a000 00:00 0 
b752b000-b7557000 r-xp 00000000 03:01 5506920    /usr/lib/libgsf-1.so.114.0.3
b7557000-b755a000 rw-p 0002b000 03:01 5506920    /usr/lib/libgsf-1.so.114.0.3
b755a000-b755b000 rw-p b755a000 00:00 0 
b755b000-b7585000 r-xp 00000000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7585000-b7586000 rw-p 0002a000 03:01 5507137    /usr/lib/libpangoft2-1.0.so.0.1600.2
b7586000-b7588000 r-xp 00000000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b7588000-b7589000 rw-p 00001000 03:01 5506549    /usr/lib/libXau.so.6.0.0
b7589000-b75a7000 r-xp 00000000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b75a7000-b75a9000 rw-p 0001d000 03:01 5506745    /usr/lib/libexpat.so.1.0.0
b75a9000-b75bc000 r-xp 00000000 03:01 5507304    /usr/lib/libz.so.1.2.3
b75bc000-b75bd000 rw-p 00012000 03:01 5507304    /usr/lib/libz.so.1.2.3
b75bd000-b75be000 rw-p b75bd000 00:00 0 
b75be000-b7626000 r-xp 00000000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b7626000-b7629000 rw-p 00068000 03:01 5506761    /usr/lib/libfreetype.so.6.3.10
b7629000-b7764000 r-xp 00000000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7764000-b7765000 r--p 0013b000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7765000-b7767000 rw-p 0013c000 03:01 1952996    /lib/tls/i686/cmov/libc-2.5.so
b7767000-b776a000 rw-p b7767000 00:00 0 
b776a000-b778f000 r-xp 00000000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b778f000-b7791000 rw-p 00024000 03:01 1953004    /lib/tls/i686/cmov/libm-2.5.so
b7791000-b77b5000 r-xp 00000000 03:01 5506654    /usr/lib/libglitz.so.1.0.0
b77b5000-b77b6000 rw-p 00024000 03:01 5506654    /usr/lib/libglitz.so.1.0.0
b77b6000-b77c9000 r-xp 00000000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b77c9000-b77cb000 rw-p 00013000 03:01 1953022    /lib/tls/i686/cmov/libpthread-2.5.so
b77cb000-b77ce000 rw-p b77cb000 00:00 0 
b77ce000-b783f000 r-xp 00000000 03:01 5505752    /usr/lib/libGL.so.1.0.9631
b783f000-b7859000 rwxp 00070000 03:01 5505752    /usr/lib/libGL.so.1.0.9631
b7859000-b785a000 rwxp b7859000 00:00 0 
b785a000-b7947000 r-xp 00000000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b7947000-b794b000 rw-p 000ed000 03:01 5506543    /usr/lib/libX11.so.6.2.0
b794b000-b7950000 r-xp 00000000 03:01 5506690    /usr/lib/libglitz-glx.so.1.0.0
b7950000-b7951000 rw-p 00004000 03:01 5506690    /usr/lib/libglitz-glx.so.1.0.0
b7951000-b79bf000 r-xp 00000000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b79bf000-b79c1000 rw-p 0006d000 03:01 5506653    /usr/lib/libcairo.so.2.11.1
b79c1000-b7a55000 r-xp 00000000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b7a55000-b7a56000 rw-p 00093000 03:01 5506846    /usr/lib/libglib-2.0.so.0.1200.11
b7a56000-b7a58000 r-xp 00000000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b7a58000-b7a5a000 rw-p 00001000 03:01 1953002    /lib/tls/i686/cmov/libdl-2.5.so
b7a5a000-b7a5b000 rw-p b7a5a000 00:00 0 
b7a5b000-b7a5d000 r-xp 00000000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b7a5d000-b7a5e000 rw-p 00002000 03:01 5506856    /usr/lib/libgmodule-2.0.so.0.1200.11
b7a5e000-b7a97000 r-xp 00000000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b7a97000-b7a98000 rw-p 00039000 03:01 5506900    /usr/lib/libgobject-2.0.so.0.1200.11
b7a98000-b7aae000 r-xp 00000000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aae000-b7aaf000 rw-p 00015000 03:01 5506810    /usr/lib/libgdk_pixbuf-2.0.so.0.1000.11
b7aaf000-b7ade000 r-xp 00000000 03:01 5507190    /usr/lib/librsvg-2.so.2.16.0
b7ade000-b7adf000 rw-p 0002f000 03:01 5507190    /usr/lib/librsvg-2.so.2.16.0
b7adf000-b7b1b000 r-xp 00000000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7b1b000-b7b1d000 rw-p 0003b000 03:01 5507133    /usr/lib/libpango-1.0.so.0.1600.2
b7b1d000-b7b24000 r-xp 00000000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7b24000-b7b25000 rw-p 00007000 03:01 5507135    /usr/lib/libpangocairo-1.0.so.0.1600.2
b7b25000-b7b26000 rw-p b7b25000 00:00 0 
b7b26000-b7b2a000 r-xp 00000000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7b2a000-b7b2b000 rw-p 00003000 03:01 5506566    /usr/lib/libXfixes.so.3.1.0
b7b2b000-b7b33000 r-xp 00000000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7b33000-b7b34000 rw-p 00007000 03:01 5506556    /usr/lib/libXcursor.so.1.0.2
b7b34000-b7b39000 r-xp 00000000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7b39000-b7b3a000 rw-p 00005000 03:01 5506584    /usr/lib/libXrandr.so.2.1.0
b7b3a000-b7b41000 r-xp 00000000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7b41000-b7b42000 rw-p 00006000 03:01 5506572    /usr/lib/libXi.so.6.0.0
b7b42000-b7b44000 r-xp 00000000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7b44000-b7b45000 rw-p 00001000 03:01 5506574    /usr/lib/libXinerama.so.1.0.0
b7b45000-b7b4c000 r-xp 00000000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7b4c000-b7b4d000 rw-p 00006000 03:01 5506586    /usr/lib/libXrender.so.1.3.0
b7b4d000-b7b4e000 rw-p b7b4d000 00:00 0 
b7b4e000-b7b5b000 r-xp 00000000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7b5b000-b7b5c000 rw-p 0000d000 03:01 5506564    /usr/lib/libXext.so.6.4.0
b7b5c000-b7b7f000 r-xp 00000000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7b7f000-b7b87000 rw-p 00023000 03:01 5506751    /usr/lib/libfontconfig.so.1.2.0
b7b87000-b7ba0000 r-xp 00000000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7ba0000-b7ba2000 rw-p 00018000 03:01 5506620    /usr/lib/libatk-1.0.so.0.1809.1
b7ba2000-b7c25000 r-xp 00000000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7c25000-b7c28000 rw-p 00083000 03:01 5506808    /usr/lib/libgdk-x11-2.0.so.0.1000.11
b7c28000-b7f79000 r-xp 00000000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f79000-b7f7f000 rw-p 00351000 03:01 5506957    /usr/lib/libgtk-x11-2.0.so.0.1000.11
b7f7f000-b7f80000 rw-p b7f7f000 00:00 0 
b7f80000-b7f83000 r-xp 00000000 03:01 5511293    /usr/lib/libakamaru.so.0.0.0
b7f83000-b7f84000 rw-p 00002000 03:01 5511293    /usr/lib/libakamaru.so.0.0.0
b7f84000-b7f85000 rw-p b7f84000 00:00 0 
b7f85000-b7f86000 r--p 00000000 03:01 5571590    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f86000-b7f87000 r--p 00000000 03:01 5571587    /usr/lib/locale/en_US.utf8/LC_PAPER
b7f87000-b7f88000 r--p 00000000 03:01 5571585    /usr/lib/locale/en_US.utf8/LC_NAME
b7f88000-b7f89000 r--p 00000000 03:01 5571579    /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f89000-b7f8a000 r--p 00000000 03:01 5571588    /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f8a000-b7f8b000 r--p 00000000 03:01 5571583    /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f8b000-b7f92000 r--s 00000000 03:01 5508729    /usr/lib/gconv/gconv-modules.cache
b7f92000-b7f93000 r--p 00000000 03:01 5571582    /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f93000-b7f95000 rwxp 00000000 00:0d 2701       /dev/zero
b7f95000-b7f96000 rw-p b7f95000 00:00 0 
b7f96000-b7faf000 r-xp 00000000 03:01 1949717    /lib/ld-2.5.so
b7faf000-b7fb1000 rw-p 00019000 03:01 1949717    /lib/ld-2.5.so
bf886000-bf899000 rwxp bf886000 00:00 0          [stack]
bf899000-bf89c000 rw-p bf899000 00:00 0 
ffffe000-fffff000 r-xp 00000000 00:00 0          [vdso]
Aborted (core dumped)

```

Any help would be greatly appreciated.

---

