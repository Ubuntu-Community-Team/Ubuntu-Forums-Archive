---
title: "Pidgin Segfaulting"
date: 2008-08-09
forum: Desktop Environments
---

### Post by ions on 2008-08-09
Pidgin has started crashing on me at startup.  This is what happens:

```
$ pidgin 
*** glibc detected *** pidgin: free(): invalid pointer: 0x0000000000ce7ca0 ***
======= Backtrace: =========
/lib/libc.so.6[0x7ff0b854f08a]
/lib/libc.so.6(cfree+0x8c)[0x7ff0b8552c1c]
/usr/lib/libpurple.so.0[0x7ff0b9458f9c]
/usr/lib/libpurple.so.0(purple_proxy_get_setup+0x8a)[0x7ff0b945c8cc]
/usr/lib/libpurple.so.0(purple_proxy_connect+0x114)[0x7ff0b945cbf5]
/usr/lib/purple-2/libmsn.so(msn_servconn_connect+0x169)[0x7ff0aa645630]
/usr/lib/purple-2/libmsn.so(msn_notification_connect+0x67)[0x7ff0aa64142a]
/usr/lib/purple-2/libmsn.so[0x7ff0aa6433ee]
/usr/lib/purple-2/libmsn.so(msn_cmdproc_process_cmd+0x1ee)[0x7ff0aa635fa8]
/usr/lib/purple-2/libmsn.so(msn_cmdproc_process_cmd_text+0x61)[0x7ff0aa63604e]
/usr/lib/purple-2/libmsn.so[0x7ff0aa645cb1]
pidgin[0x46be51]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e4)[0x7ff0b8d113d4]
/usr/lib/libglib-2.0.so.0[0x7ff0b8d146e5]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d5)[0x7ff0b8d14a05]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x7ff0ba457f03]
pidgin(main+0xac2)[0x486c0a]
/lib/libc.so.6(__libc_start_main+0xf4)[0x7ff0b84f91c4]
pidgin[0x42f159]
======= Memory map: ========
00400000-004e8000 r-xp 00000000 08:01 7839992                            /usr/bin/pidgin
006e7000-006ed000 rw-p 000e7000 08:01 7839992                            /usr/bin/pidgin
006ed000-00d4c000 rw-p 006ed000 00:00 0                                  [heap]
41d6d000-41d6e000 ---p 41d6d000 00:00 0 
41d6e000-4256e000 rw-p 41d6e000 00:00 0 
7ff09c000000-7ff09c021000 rw-p 7ff09c000000 00:00 0 
7ff09c021000-7ff0a0000000 ---p 7ff09c021000 00:00 0 
7ff0a2ee4000-7ff0a2f44000 rw-s 00000000 00:09 5505079                    /SYSV00000000 (deleted)
7ff0a2f44000-7ff0a2fa4000 rw-s 00000000 00:09 5472309                    /SYSV00000000 (deleted)
7ff0a2fa4000-7ff0a2fc6000 r-xp 00000000 08:01 7841600                    /usr/lib/libjpeg.so.62.0.0
7ff0a2fc6000-7ff0a31c6000 ---p 00022000 08:01 7841600                    /usr/lib/libjpeg.so.62.0.0
7ff0a31c6000-7ff0a31c7000 rw-p 00022000 08:01 7841600                    /usr/lib/libjpeg.so.62.0.0
7ff0a31c7000-7ff0a31cb000 r-xp 00000000 08:01 7872771                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7ff0a31cb000-7ff0a33cb000 ---p 00004000 08:01 7872771                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7ff0a33cb000-7ff0a33cc000 rw-p 00004000 08:01 7872771                    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-jpeg.so
7ff0a33cc000-7ff0a34d0000 rw-p 7ff0a33cc000 00:00 0 
7ff0a34d0000-7ff0a3557000 r--p 00000000 08:01 7972432                    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
7ff0a3557000-7ff0a37df000 r--s 00000000 08:01 4800817                    /var/lib/aspell/en-common.rws
7ff0a37df000-7ff0a37e1000 r-xp 00000000 08:01 7905335                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7ff0a37e1000-7ff0a39e0000 ---p 00002000 08:01 7905335                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7ff0a39e0000-7ff0a39e1000 rw-p 00001000 08:01 7905335                    /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7ff0a39e1000-7ff0a39f0000 r-xp 00000000 08:01 18759717                   /lib/libbz2.so.1.0.4
7ff0a39f0000-7ff0a3bef000 ---p 0000f000 08:01 18759717                   /lib/libbz2.so.1.0.4
7ff0a3bef000-7ff0a3bf1000 rw-p 0000e000 08:01 18759717                   /lib/libbz2.so.1.0.4
7ff0a3bf1000-7ff0a3c5f000 r-xp 00000000 08:01 7840524                    /usr/lib/libgio-2.0.so.0.0.0
7ff0a3c5f000-7ff0a3e5f000 ---p 0006e000 08:01 7840524                    /usr/lib/libgio-2.0.so.0.0.0
7ff0a3e5f000-7ff0a3e62000 rw-p 0006e000 08:01 7840524                    /usr/lib/libgio-2.0.so.0.0.0
7ff0a3e62000-7ff0a3e9a000 r-xp 00000000 08:01 7841217                    /usr/lib/libcroco-0.6.so.3.0.1
7ff0a3e9a000-7ff0a4099000 ---p 00038000 08:01 7841217                    /usr/lib/libcroco-0.6.so.3.0.1
7ff0a4099000-7ff0a409d000 rw-p 00037000 08:01 7841217                    /usr/lib/libcroco-0.6.so.3.0.1
7ff0a409d000-7ff0a40d4000 r-xp 00000000 08:01 7841471           Aborted

```

I had installed tor and privoxy yesterday.  It ticked me off so I removed it, it's the only thing I can think of that could be causing this.  Oh yeah, ran a memtest, no errors multiple passes.

8.04 64bit.

---

### Post by ions on 2008-08-09
Fixed this by System > Preferences > Network Proxy > Direct Internet Connection

It had been changed for tor which is now gone.

---

