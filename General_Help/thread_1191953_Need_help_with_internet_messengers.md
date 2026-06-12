---
title: "Need help with internet messengers"
date: 2009-06-19
forum: General Help
---

### Post by bww15 on 2009-06-19
Hi I installed ubuntu but the internet messenger wont work . I started pidgin and it stucks on connecting and I tried other ims and have the same problems . Please help

---

### Post by synapsys on 2009-06-19
Are you using a proxy or a direct connection to the internet?

If proxy you will need to configure your im programs accordingly.

If direct, start pidgin from a terminal and post output.

---

### Post by bww15 on 2009-06-19
this is the output
*** glibc detected *** pidgin: corrupted double-linked list: 0x0998d108 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb753707f]
/lib/tls/i686/cmov/libc.so.6[0xb7538b8d]
/lib/tls/i686/cmov/libc.so.6(__libc_calloc+0xef)[0xb753a6ef]
/usr/lib/libglib-2.0.so.0(g_malloc0+0x3c)[0xb776320c]
/usr/lib/libglib-2.0.so.0[0xb774d992]
/usr/lib/libpurple.so.0(purple_dbus_unregister_pointer+0x43)[0xb76fc6b3]
/usr/lib/libpurple.so.0(purple_plugin_destroy+0xa0)[0xb769f760]
/usr/lib/libpurple.so.0(purple_plugins_destroy_all+0x2a)[0xb769f8ea]
/usr/lib/libpurple.so.0(purple_core_quit+0xfa)[0xb768e45a]
pidgin(main+0xcd2)[0x80c3622]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb74dd775]
pidgin[0x806db61]
======= Memory map: ========
08048000-0810e000 r-xp 00000000 08:05 1213276    /usr/bin/pidgin
0810e000-0810f000 r--p 000c5000 08:05 1213276    /usr/bin/pidgin
0810f000-08112000 rw-p 000c6000 08:05 1213276    /usr/bin/pidgin
097d4000-09aa2000 rw-p 097d4000 00:00 0          [heap]
b5900000-b5921000 rw-p b5900000 00:00 0 
b5921000-b5a00000 ---p b5921000 00:00 0 
b5a51000-b5a6b000 r-xp 00000000 08:05 1246199    /usr/lib/gio/modules/libgvfsdbus.so
b5a6b000-b5a6c000 r--p 00019000 08:05 1246199    /usr/lib/gio/modules/libgvfsdbus.so
b5a6c000-b5a6d000 rw-p 0001a000 08:05 1246199    /usr/lib/gio/modules/libgvfsdbus.so
b5a6d000-b5a7f000 r-xp 00000000 08:05 1213759    /usr/lib/libgvfscommon.so.0.0.0
b5a7f000-b5a80000 r--p 00012000 08:05 1213759    /usr/lib/libgvfscommon.so.0.0.0
b5a80000-b5a81000 rw-p 00013000 08:05 1213759    /usr/lib/libgvfscommon.so.0.0.0
b5a8e000-b5a9d000 r-xp 00000000 08:05 1246198    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5a9d000-b5a9e000 r--p 0000e000 08:05 1246198    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5a9e000-b5a9f000 rw-p 0000f000 08:05 1246198    /usr/lib/gio/modules/libgioremote-volume-monitor.so
b5a9f000-b5aa9000 r-xp 00000000 08:05 1214466    /usr/lib/libgstinterfaces-0.10.so.0.16.0
b5aa9000-b5aaa000 r--p 00009000 08:05 1214466    /usr/lib/libgstinterfaces-0.10.so.0.16.0
b5aaa000-b5aab000 rw-p 0000a000 08:05 1214466    /usr/lib/libgstinterfaces-0.10.so.0.16.0
b5aab000-b5adf000 r-xp 00000000 08:05 1214454    /usr/lib/libgstbase-0.10.so.0.19.0
b5adf000-b5ae0000 r--p 00033000 08:05 1214454    /usr/lib/libgstbase-0.10.so.0.19.0
b5ae0000-b5ae1000 rw-p 00034000 08:05 1214454    /usr/lib/libgstbase-0.10.so.0.19.0
b5ae1000-b5af1000 r-xp 00000000 08:05 1214478    /usr/lib/libgstrtp-0.10.so.0.16.0
b5af1000-b5af2000 r--p 0000f000 08:05 1214478    /usr/lib/libgstrtp-0.10.so.0.16.0
b5af2000-b5af3000 rw-p 00010000 08:05 1214478    /usr/lib/libgstrtp-0.10.so.0.16.0
b5af3000-b5b12000 r-xp 00000000 08:05 1214452    /usr/lib/libgstaudio-0.10.so.0.16.0
b5b12000-b5b13000 ---p 0001f000 08:05 1214452    /usr/lib/libgstaudio-0.10.so.0.16.0
b5b13000-b5b14000 r--p 0001f000 08:05 1214452    /usr/lib/libgstaudio-0.10.so.0.16.0
b5b14000-b5b15000 rw-p 00020000 08:05 1214452    /usr/lib/libgstaudio-0.10.so.0.16.0
b5b15000-b5b2a000 r-xp 00000000 08:05 1214626    /usr/lib/libbluetooth.so.3.2.1
b5b2a000-b5b2b000 r--p 00014000 08:05 1214626    /usr/lib/libbluetooth.so.3.2.1
b5b2b000-b5b2c000 rw-p 00015000 08:05 1214626    /usr/lib/libbluetooth.so.3.2.1
b5b2d000-b5b37000 r-xp 00000000 08:05 868392     /usr/lib/gstreamer-0.10/libgstgio.so
b5b37000-b5b38000 r--p 00009000 08:05 868392     /usr/lib/gstreamer-0.10/libgstgio.so
b5b38000-b5b39000 rw-p 0000a000 08:05 868392     /usr/lib/gstreamer-0.10/libgstgio.so
b5b39000-b5b58000 r-xp 00000000 08:05 868450     /usr/lib/gstreamer-0.10/libgstbluetooth.so
b5b58000-b5b59000 ---p 0001f000 08:05 868450     /usr/lib/gstreamer-0.10/libgstbluetooth.so
b5b59000-b5b5a000 r--p 0001f000 08:05 868450     /usr/lib/gstreamer-0.10/libgstbluetooth.so
b5b5a000-b5b5b000 rw-p 00020000 08:05 868450     /usr/lib/gstreamer-0.10/libgstbluetooth.so
b5b5b000-b5ba1000 r-xp 00000000 08:05 1204227    /usr/lib/nss/libnssckbi.so
b5ba1000-b5ba9000 r--p 00045000 08:05 1204227    /usr/lib/nss/libnssckbi.so
b5ba9000-b5bad000 rw-p 0004d000 08:05 1204227    /usr/lib/nss/libnssckbi.so
b5bad000-b5bf1000 r-xp 00000000 08:05 1204226    /usr/lib/nss/libfreebl3.so
b5bf1000-b5bf2000 r--p 00043000 08:05 1204226    /usr/lib/nss/libfreebl3.so
b5bf2000-b5bf3000 rw-p 00044000 08:05 1204226    /usr/lib/nss/libfreebl3.so
b5bf3000-b5c27000 r-xp 00000000 08:05 1204230    /usr/lib/nss/libsoftokn3.so
b5c27000-b5c28000 r--p 00034000 08:05 1204230    /usr/lib/nss/libsoftokn3.so
b5c28000-b5c29000 rw-p 00035000 08:05 1204230    /usr/lib/nss/libsoftokn3.so
b5c29000-b5c5f000 r-xp 00000000 08:05 1221893    /usr/lib/purple-2/libqq.so
b5c5f000-b5c60000 ---p 00036000 08:05 1221893    /usr/lib/purple-2/libqq.so
b5c60000-b5c61000 r--p 00036000 08:05 1221893    /usr/lib/purple-2/libqq.so
b5c61000-b5c63000 rw-p 00037000 08:05 1221893    /usr/lib/purple-2/libqq.so
b5c63000-b5c92000 r-xp 00000000 08:05 1163344    /lib/libncurses.so.5.7
b5c92000-b5c94000 r--p 0002e000 08:05 1163344    /lib/libncurses.so.5.7
b5c94000-b5c95000 rw-p 00030000 08:05 1163344    /lib/libncurses.so.5.7
b5c95000-b5cc1000 r-xp 00000000 08:05 1163388    /lib/libreadline.so.5.2
b5cc1000-b5cc2000 ---p 0002c000 08:05 1163388    /lib/libreadline.so.5.2
b5cc2000-b5cc3000 r--p 0002c000 08:05 1163388    /lib/libreadline.so.5.2
b5cc3000-b5cc6000 rw-p 0002d000 08:05 1163388    /lib/libreadline.so.5.2
b5cc6000-b5cc7000 rw-p b5cc6000 00:00 0 
b5cc7000-b5cca000 r-xp 00000000 08:05 1214542    /usr/lib/libhesiod.so.0
b5cca000-b5ccb000 r--p 00002000 08:05 1214542    /usr/lib/libhesiod.so.0
b5ccb000-b5ccc000 rw-p 00003000 08:05 1214542    /usr/lib/libhesiod.so.0
b5ccc000-b5cd5000 r-xp 00000000 08:05 1214978    /usr/lib/libzephyr.so.3.0.0
b5cd5000-b5cd6000 ---p 00009000 08:05 1214978    /usr/lib/libzephyr.so.3.0.0
b5cd6000-b5cd7000 r--p 00009000 08:05 1214978    /usr/lib/libzephyr.so.3.0.0
b5cd7000-b5cd8000 rw-p 0000a000 08:05 1214978    /usr/lib/libzephyr.so.3.0.0
b5cd8000-b5cdb000 rw-p b5cd8000 00:00 0 
b5cdb000-b5ce7000 r-xp 00000000 08:05 1221898    /usr/lib/purple-2/libzephyr.so
b5ce7000-b5ce8000 r--p 0000b000 08:05 1221898    /usr/lib/purple-2/libzephyr.so
b5ce8000-b5ce9000 rw-p 0000c000 08:05 1221898    /usr/lib/purple-2/libzephyr.so
b5ce9000-b5d13000 r-xp 00000000 08:05 1214632    /usr/lib/libmeanwhile.so.1.0.2
b5d13000-b5d14000 rw-p 00029000 08:05 1214632    /usr/lib/libmeanwhile.so.1.0.2
b5d1b000-b5d1f000 r-xp 00000000 08:05 1245540    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5d1f000-b5d20000 r--p 00003000 08:05 1245540    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5d20000-b5d21000 rw-p 00004000 08:05 1245540    /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
b5d21000-b5d36000 r-xp 00000000 08:05 1221894    /usr/lib/purple-2/libsametime.so
b5d36000-b5d37000 r--p 00014000 08:05 1221894    /usr/lib/purple-2/libsametime.so
b5d37000-b5d38000 rw-p 00015000 08:05 1221894    /usr/lib/purple-2/libsametime.so
b5d38000-b5d39000 rw-p b5d38000 00:00 0 
b5d39000-b5d3d000 r-xp 00000000 08:05 1221870    /usr/lib/purple-2/ssl-nss.so
b5d3d000-b5d3e000 r--p 00003000 08:05 1221870    /usr/lib/purple-2/ssl-nss.so
b5d3e000-b5d3f000 rw-p 00004000 08:05 1221870    /usr/lib/purple-2/ssl-nss.so
b5d3f000-b5d48000 r-xp 00000000 08:05 1221876    /usr/lib/purple-2/log_reader.so
b5d48000-b5d49000 r--p 00008000 08:05 1221876    /usr/lib/purple-2/log_reader.so
b5d49000-b5d4a000 rw-p 00009000 08:05 1221876    /usr/lib/purple-2/log_reader.so
b5d4a000-b5d4c000 r-xp 00000000 08:05 1221879    /usr/lib/purple-2/psychic.so
b5d4c000-b5d4d000 r--p 00001000 08:05 1221879    /usr/lib/purple-2/psychic.so
b5d4d000-b5d4e000 rw-p 00002000 08:05 1221879    /usr/lib/purple-2/psychic.so
b5d4e000-b5d4f000 r-xp 00000000 08:05 1221891    /usr/lib/purple-2/libaim.so
b5d4f000-b5d50000 r--p 00000000 08:05 1221891    /usr/lib/purple-2/libaim.so
b5d50000-b5d51000 rw-p 00001000 08:05 1221891    /usr/lib/purple-2/libaim.so
b5d51000-b5d5b000 r-xp 00000000 08:05 1221896    /usr/lib/purple-2/libsimple.so
b5d5b000-b5d5c000 r--p 00009000 08:05 1221896    /usr/lib/purple-2/libsimple.so
b5d5c000-b5d5d000 rw-p 0000a000 08:05 1221896    /usr/lib/purple-2/libsimple.so
b5d5d000-b5d6d000 rw-p b5d5d000 00:00 0 
b5d6d000-b5dac000 r-xp 00000000 08:05 1221890    /usr/lib/purple-2/liboscar.so.0.0.0
b5dac000-b5dad000 r--p 0003f000 08:05 1221890    /usr/lib/purple-2/liboscar.so.0.0.0
b5dad000-b5dae000 rw-p 00040000 08:05 1221890    /usr/lib/purple-2/liboscar.so.0.0.0
b5dae000-b5daf000 rw-p b5dae000 00:00 0 
b5daf000-b5df0000 r-xp 00000000 08:05 1221887    /usr/lib/purple-2/libmsn.so
b5df0000-b5df1000 r--p 00040000 08:05 1221887    /usr/lib/purple-2/libmsn.so
b5df1000-b5df2000 rw-p 00041000 08:05 1221887    /usr/lib/purple-2/libmsn.so
b5df2000-b5df4000 rw-p b5df2000 00:00 0 
b5df4000-b5f20000 r-xp 00000000 08:05 1214186    /usr/lib/libdb-4.6.so
b5f20000-b5f22000 r--p 0012b000 08:05 1214186    /usr/libAborted


I dont kow what connection im using . when i install the driver it connects automaticly to the internet.

Only yahoo account is not working in ubuntu, the others work . but on windows yahoo works

---

### Post by Therion on 2009-06-19
> **bww15 said:**
> Only yahoo account is not working in ubuntu, the others work . but on windows yahoo works
Lots of threads about this.

Why it's happening and what to do about it:  [http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo)

---

### Post by bww15 on 2009-06-19
Thank You! It worked!

---

