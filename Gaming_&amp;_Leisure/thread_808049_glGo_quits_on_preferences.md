---
title: "glGo quits on preferences"
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by Tyke91 on 2008-05-26
I've installed the program glGo (to play go online :D ) and every time I try to adjust the preferences, the program just stops.

here is the error output. 

```

mykola@mykola-laptop:~$ glGo
Init python: /usr/share/games/glGo/pythonlib.zip
*** glibc detected *** glGo: double free or corruption (!prev): 0x08f73620 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb730ca85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb73104f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb75c98b1]
glGo[0x821a7ba]
glGo[0x827789b]
glGo[0x827837b]
glGo[0x82851ac]
glGo[0x82986ae]
glGo[0x8331813]
glGo[0x83319c5]
glGo[0x8331b8d]
glGo[0x821a71f]
glGo[0x8279b23]
glGo[0x8184983]
glGo[0x8166281]
glGo[0x8166abf]
glGo[0x8166cd0]
glGo[0x817ea1c]
glGo[0x8166281]
glGo[0x8166abf]
glGo[0x8184ebe]
glGo[0x8166281]
glGo[0x8166abf]
glGo[0x8166cd0]
glGo[0x81846f9]
glGo[0x8166281]
glGo[0x8166abf]
glGo[0x8166cd0]
glGo[0x8174a35]
glGo[0x8166281]
glGo[0x8166abf]
glGo[0x81671a2]
glGo[0x812a824]
glGo[0x812db8a]
glGo[0x8331813]
glGo[0x83319c5]
glGo[0x8331b8d]
glGo[0x82847f8]
glGo[0x8331b38]
glGo[0x82847f8]
glGo[0x8331b38]
glGo[0x82847f8]
glGo[0x8331b38]
glGo[0x82847f8]
glGo[0x8331b38]
glGo[0x822ecc4]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xb765ba4f]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb764e759]
/usr/lib/libgobject-2.0.so.0[0xb76630a3]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c6)[0xb7664916]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7664c59]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_clicked+0x8a)[0xb792c01a]
/usr/lib/libgtk-x11-2.0.so.0[0xb792db7e]
/usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x4f)[0xb765ba4f]
/usr/lib/libgobject-2.0.so.0[0xb764d079]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x129)[0xb764e759]
/usr/lib/libgobject-2.0.so.0[0xb7662975]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x8c6)[0xb7664916]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7664c59]
/usr/lib/libgtk-x11-2.0.so.0(gtk_button_released+0x8a)[0xb792c0aa]
/usr/lib/libgtk-x11-2.0.so.0[0xb792c0d1]
/usr/lib/libgtk-x11-2.0.so.0[0xb7a058d4]
/usr/lib/libgobject-2.0.so.0[0xb764d079]
======= Memory map: ========
08048000-08473000 r-xp 00000000 08:06 1867791    /usr/games/glGo
08473000-084b4000 rw-p 0042b000 08:06 1867791    /usr/games/glGo
084b4000-08ff5000 rw-p 084b4000 00:00 0          [heap]
b5900000-b5921000 rw-p b5900000 00:00 0 
b5921000-b5a00000 ---p b5921000 00:00 0 
b5a5e000-b5a61000 rw-s 00000000 00:09 3833899    /SYSV00000000 (deleted)
b5a61000-b5ac1000 rw-s 00000000 00:09 3801126    /SYSV00000000 (deleted)
b5ac1000-b5b21000 rw-s 00000000 00:09 3768357    /SYSV00000000 (deleted)
b5b21000-b5c25000 rw-p b5b21000 00:00 0 
b5c25000-b5cb6000 r--p 00000000 08:06 2418195    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b5cb6000-b5cc5000 r-xp 00000000 08:06 1720358    /lib/libbz2.so.1.0.4
b5cc5000-b5cc6000 rw-p 0000f000 08:06 1720358    /lib/libbz2.so.1.0.4
b5cc6000-b5d25000 r-xp 00000000 08:06 2285733    /usr/lib/libgio-2.0.so.0.0.0
b5d25000-b5d27000 rw-p 0005e000 08:06 2285733    /usr/lib/libgio-2.0.so.0.0.0
b5d27000-b5e40000 r-xp 00000000 08:06 2287743    /usr/lib/libxml2.so.2.6.31
b5e40000-b5e45000 rw-p 00119000 08:06 2287743    /usr/lib/libxml2.so.2.6.31
b5e45000-b5e46000 rw-p b5e45000 00:00 0 
b5e46000-b5e78000 r-xp 00000000 08:06 2287043    /usr/lib/libcroco-0.6.so.3.0.1
b5e78000-b5e7b000 rw-p 00031000 08:06 2287043    /usr/lib/libcroco-0.6.so.3.0.1
b5e7b000-b5eab000 r-xp 00000000 08:06 2287297    /usr/lib/libgsf-1.so.114.0.7
b5eab000-b5eae000 rw-p 0002f000 08:06 2287297    /usr/lib/libgsf-1.so.114.0.7
b5eae000-b5eaf000 rw-p b5eae000 00:00 0 
b5eaf000-b5edf000 r-xp 00000000 08:06 2287620    /usr/lib/librsvg-2.so.2.22.2
b5edf000-b5ee0000 rw-p 00030000 08:06 2287620    /usr/lib/librsvg-2.so.2.22.2
b5ee5000-b5eeb000 r-xp 00000000 08:06 2310907    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5eeb000-b5eec000 rw-p 00005000 08:06 2310907    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b5eec000-b5eee000 r-xp 00000000 08:06 2359984    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5eee000-b5eef000 rw-p 00001000 08:06 2359984    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b5eef000-b5ef0000 r-xp 00000000 08:06 2311398    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5ef0000-b5ef1000 rw-p 00000000 08:06 2311398    /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
b5ef1000-b5f9c000 r--p 00000000 08:06 2500790    /usr/share/icons/Tangerine/icon-theme.cache
b5f9c000-b5f9e000 rw-p b5f9c000 00:00 0 
b5f9e000-b5fa4000 r--s 00000000 08:06 704576     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b5fa4000-b5fa7000 r--s 00000000 08:06 704586     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b5fa7000-b5fa8000 r--s 00000000 08:06 704578     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b5fa8000-b5fa9000 r--s 00000000 08:06 704571     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b5fa9000-b5fac000 r--s 00000000 08:06 704577     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b5fac000-b5faf000 r--s 00000000 08:06 704573     /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b5faf000-b5fb2000 r--s 00000000 08:06 704583     /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b5fb2000-b5fba000 r--s 00000000 08:06 704587     /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b5fba000-b5fc2000 r--s 00000000 08:06 704566     /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b5fc2000-b5fc3000 r--s 00000000 08:06 704569     /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b5fc3000-b5fe5000 r--s 00000000 08:06 710190     /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b5fe5000-b5fe8000 r--s 00000000 08:06 704584     /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b5fe8000-b6010000 r-xp 00000000 08:06 2311347    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6010000-b6011000 rw-p 00028000 08:06 2311347    /usr/lib/gtk-2.0/2.10.0/engines/libclearlooks.so
b6011000-b601a000 r-xp 00000000 08:06 1738088    /lib/tls/i686/cmov/libnss_files-2.7.so
b601a000-b601c000 rw-p 00008000 08:06 1738088    /lib/tls/i686/cmov/libnss_files-2.7.so
b601c000-b6024000 r-xp 00000000 08:06 1738092    /lib/tls/i686/cmov/libnss_nis-2.7.so
b6024000-b6026000 rw-p 00007000 08:06 1738092    /lib/tls/i686/cmov/libnss_nis-2.7.so
b6026000-b603a000 r-xp 00000000 08:06 1738082    /lib/tls/i686/cmov/libnsl-2.7.so
b603a000-b603c000 rw-p 00013000 08:06 1738082    /lib/tls/i686/cmov/libnsl-2.7.so
b603c000-b603e000 rw-p b603c000 00:00 0 
b603e000-b6045000 r-xp 00000000 08:06 1738084    /lib/tls/i686/cmov/libnss_compat-2.7.so
b6045000-b6047000 rw-p 00006000 08:06 1738084    /lib/tls/i686/cmov/libnss_compat-2.7.so
b6047000-b604e000 r--s 00000000 08:06 704581     /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b604e000-b6054000 r--s 00000000 08:06 704565     /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b6054000-b6056000 r--s 00000000 08:06 704807     /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b6056000-b6095000 r--p 00000000 08:06 2318783    /usr/lib/locale/en_US.utf8/LC_CTYPE
b6095000-b6096000 r--p 00000000 08:06 2318788    /usr/lib/locale/en_US.utf8/LC_NUMERIC
b6096000-b6097000 r--p 00000000 08:06 2318791    /usr/lib/locale/en_US.utf8/LC_TIME
b6097000-b6178000 r--p 00000000 08:06 2318782    /usr/lib/locale/en_US.utf8/LC_COLLATE
b6178000-b6179000 r--p 00000000 08:06 2318786    /usr/lib/locale/en_US.utf8/LC_MONETARY
b6179000-b617a000 r--p 00000000 08:06 2318792    /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b617a000-b61e2000 rw-p b617a000 00:00 0 
b61e2000-b61e6000 r-xp 00000000 08:06 2286907    /usr/lib/libXdmcp.so.6.0.0
b61e6000-b61e7000 rw-p 00003000 08:06 2286907    /usr/lib/libXdmcp.so.6.0.0
b61e7000-b620f000 r-xp 00000000 08:06 2287565    /usr/lib/libpixman-1.so.0.10.0
b620f000-b6210000 rw-p 00027000 08:06 2287565    /usr/lib/libpixman-1.so.0.10.0
b6210000-b6236000 r-xp 00000000 08:06 2287541    /usr/lib/libpangoft2-1.0.so.0.2000.1
b6236000-b6237000 rw-p 00026000 08:06 2287541    /usr/lib/libpangoft2-1.0.so.0.2000.1
b6237000-b6238000 rw-p b6237000 00:00 0 
b6238000-b623d000 r-xp 00000000 08:06 2287289    /usr/lib/libgpm.so.1.19.6
b623d000-b623e000 rw-p 00004000 08:06 2287289    /usr/lib/libgpm.so.1.19.6
b623e000-b62d6000 r-xp 00000000 08:06 1720448    /lib/libslang.so.2.1.3
b62d6000-b62e6000 rw-p 00098000 08:06 1720448    /lib/libslang.so.2.1.3
b62e6000-b631c000 rw-p b62e6000 00:00 0 
b631c000-b6349000 r-xp 00000000 08:06 1720400    /lib/libncurses.so.5.6
b6349000-b634c000 rw-p 0002c000 08:06 1720400    /lib/libncurses.so.5.6
b634c000-b6361000 r-xp 00000000 08:06 2286860    /usr/lib/libICE.so.6.3.0
b6361000-b6362000 rw-p 00014000 08:06 2286860    /usr/lib/libICE.so.6.3.0
b6362000-b6364000 rw-p b6362000 00:00 0 
b6364000-b636b000 r-xp 00000000 08:06 2286884    /usr/lib/libSM.so.6.0.0
b636b000-b636c000 rw-p 00006000 08:06 2286884    /usr/lib/libSM.so.6.0.0
b636c000-b636d000 rw-p b636c000 00:00 0 
b636d000-b6370000 r-xp 00000000 08:06 1720362    /lib/libcap.so.1.10
b6370000-b6371000 rw-p 00002000 08:06 1720362    /lib/libcap.so.1.10
b6Aborted

```

---

### Post by etienne2b on 2009-06-18
i am no help for this being a command line disabled user, and i would like to strongly express my wish to see GlGo in the normal ubuntu package software, not in the geek only tricks.
i will start a thread ;-)

---

