---
title: "Gnomebaker crash"
date: 2009-04-25
forum: General Help
---

### Post by waffen on 2009-04-25
When I put files (ADD FILE function) in gnomebaker its shutdown wiht no notice, I receipt this error:

```

mario@mario-laptop:~$ gnomebaker
*** glibc detected *** gnomebaker: double free or corruption (out): 0x00000000028cf540 ***
======= Backtrace: =========
/lib/libc.so.6[0x7f458cf82cb8]
/lib/libc.so.6(cfree+0x76)[0x7f458cf85276]
/usr/lib/libgdk-x11-2.0.so.0[0x7f459019d8e0]
/usr/lib/libgdk-x11-2.0.so.0[0x7f459019a2bb]
/usr/lib/libgdk-x11-2.0.so.0[0x7f459019aae7]
/usr/lib/libgdk-x11-2.0.so.0[0x7f459019af0e]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x24a)[0x7f458e16120a]
/usr/lib/libglib-2.0.so.0[0x7f458e1648e0]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1cd)[0x7f458e164dad]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa7)[0x7f4590521bc7]
gnomebaker(main+0x1d8)[0x4124e8]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7f458cf295a6]
gnomebaker[0x4121b9]
======= Memory map: ========
00400000-0044b000 r-xp 00000000 08:01 862011                             /usr/bin/gnomebaker
0064b000-0064c000 r--p 0004b000 08:01 862011                             /usr/bin/gnomebaker
0064c000-0064e000 rw-p 0004c000 08:01 862011                             /usr/bin/gnomebaker
020b4000-02f98000 rw-p 020b4000 00:00 0                                  [heap]
7f457add7000-7f457addb000 r-xp 00000000 08:01 613230                     /lib/libattr.so.1.1.0
7f457addb000-7f457afda000 ---p 00004000 08:01 613230                     /lib/libattr.so.1.1.0
7f457afda000-7f457afdb000 r--p 00003000 08:01 613230                     /lib/libattr.so.1.1.0
7f457afdb000-7f457afdc000 rw-p 00004000 08:01 613230                     /lib/libattr.so.1.1.0
7f457afdc000-7f457afe4000 r-xp 00000000 08:01 714235                     /usr/lib/libfam.so.0.0.0
7f457afe4000-7f457b1e3000 ---p 00008000 08:01 714235                     /usr/lib/libfam.so.0.0.0
7f457b1e3000-7f457b1e4000 r--p 00007000 08:01 714235                     /usr/lib/libfam.so.0.0.0
7f457b1e4000-7f457b1e5000 rw-p 00008000 08:01 714235                     /usr/lib/libfam.so.0.0.0
7f457b1e5000-7f457b1ec000 r-xp 00000000 08:01 613224                     /lib/libacl.so.1.1.0
7f457b1ec000-7f457b3eb000 ---p 00007000 08:01 613224                     /lib/libacl.so.1.1.0
7f457b3eb000-7f457b3ed000 rw-p 00006000 08:01 613224                     /lib/libacl.so.1.1.0
7f457b3ed000-7f457b3fb000 r-xp 00000000 08:01 744571                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
7f457b3fb000-7f457b5fa000 ---p 0000e000 08:01 744571                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
7f457b5fa000-7f457b5fb000 r--p 0000d000 08:01 744571                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
7f457b5fb000-7f457b5fc000 rw-p 0000e000 08:01 744571                     /usr/lib/gnome-vfs-2.0/modules/libfile.so
7f457b5fc000-7f457b5fe000 r-xp 00000000 08:01 269813                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f457b5fe000-7f457b7fd000 ---p 00002000 08:01 269813                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f457b7fd000-7f457b7fe000 r--p 00001000 08:01 269813                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f457b7fe000-7f457b7ff000 rw-p 00002000 08:01 269813                     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
7f457b7ff000-7f457b800000 ---p 7f457b7ff000 00:00 0 
7f457b800000-7f457c000000 rw-p 7f457b800000 00:00 0 
7f457c000000-7f457c06d000 rw-p 7f457c000000 00:00 0 
7f457c06d000-7f4580000000 ---p 7f457c06d000 00:00 0 
7f458002c000-7f458008c000 rw-s 00000000 00:09 10879004                   /SYSV00000000 (deleted)
7f458008c000-7f458008d000 ---p 7f458008c000 00:00 0 
7f458008d000-7f458088d000 rw-p 7f458008d000 00:00 0 
7f458088d000-7f45808a4000 r-xp 00000000 08:01 714069                     /usr/lib/libbeagle.so.1.0.2
7f45808a4000-7f4580aa3000 ---p 00017000 08:01 714069                     /usr/lib/libbeagle.so.1.0.2
7f4580aa3000-7f4580aa4000 r--p 00016000 08:01 714069                     /usr/lib/libbeagle.so.1.0.2
7f4580aa4000-7f4580aa5000 rw-p 00017000 08:01 714069                     /usr/lib/libbeagle.so.1.0.2
7f4580aa5000-7f4580ab1000 r-xp 00000000 08:01 713124                     /usr/lib/libtrackerclient.so.0.0.0
7f4580ab1000-7f4580cb0000 ---p 0000c000 08:01 713124                     /usr/lib/libtrackerclient.so.0.0.0
7f4580cb0000-7f4580cb1000 r--p 0000b000 08:01 713124                     /usr/lib/libtrackerclient.so.0.0.0
7f4580cb1000-7f4580cb2000 rw-p 0000c000 08:01 713124                     /usr/lib/libtrackerclient.so.0.0.0
7f4580cb2000-7f4580cd0000 r-xp 00000000 08:01 744093                     /usr/lib/gio/modules/libgvfsdbus.so
7f4580cd0000-7f4580ecf000 ---p 0001e000 08:01 744093                     /usr/lib/gio/modules/libgvfsdbus.so
7f4580ecf000-7f4580ed0000 r--p 0001d000 08:01 744093                     /usr/lib/gio/modules/libgvfsdbus.so
7f4580ed0000-7f4580ed1000 rw-p 0001e000 08:01 744093                     /usr/lib/gio/modules/libgvfsdbus.so
7f4580ed1000-7f4580ee6000 r-xp 00000000 08:01 711912                     /usr/lib/libgvfscommon.so.0.0.0
7f4580ee6000-7f45810e6000 ---p 00015000 08:01 711912                     /usr/lib/libgvfscommon.so.0.0.0
7f45810e6000-7f45810e7000 r--p 00015000 08:01 711912                     /usr/lib/libgvfscommon.so.0.0.0
7f45810e7000-7f45810e8000 rw-p 00016000 08:01 711912                     /usr/lib/libgvfscommon.so.0.0.0
7f4581103000-7f4581114000 r-xp 00000000 08:01 744092                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f4581114000-7f4581313000 ---p 00011000 08:01 744092                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f4581313000-7f4581314000 r--p 00010000 08:01 744092                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f4581314000-7f4581315000 rw-p 00011000 08:01 744092                     /usr/lib/gio/modules/libgioremote-volume-monitor.so
7f4581324000-7f458133c000 r--s 00000000 08:01 801302                     /usr/share/mime/mime.cache
7f458133c000-7f458Cancelado
mario@mario-laptop:~$ 

```

---

### Post by zvacet on 2009-04-25
I can not help you with this one but why don´t you try Brasero or K3b.

---

### Post by waffen on 2009-04-25
Brasero showme error and error and error when I try to copy a DVD Data file... so I'll try K3B, thanks!

---

