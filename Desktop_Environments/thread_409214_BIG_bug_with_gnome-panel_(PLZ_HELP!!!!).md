---
title: "BIG bug with gnome-panel (PLZ HELP!!!!)"
date: 2007-04-14
forum: Desktop Environments
---

### Post by eldersoares on 2007-04-14
hi!
my story: i downloaded a movie that came in a .bin format that i didnt know what was. i renamed it to .iso and right-clicked in 'extract here'. since then, the gnome-panel crashes non-stop. it crashes and opens again, then crashes and open again.... since yesterday. i already restarted the system, reconfigured the packaged (dpkg-reconfigure). i uninstalled with dpkg --force-depends and installed again but i didnt work. i believe the problem is with some of those little programs near the clock because, until the panel crashes, the menus appears. i cant use most programs because i'm without the panel!!!

the bugzilla's crash message is:

Memory status: size: 42536960 vsize: 0 resident: 42536960 share: 0 rss: 20033536 rss_rlim: 0
CPU usage: start_time: 1176559556 rtime: 0 utime: 89 stime: 0 cutime:83 cstime: 0 timeout: 6 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225644368 (LWP 5650)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb75d9323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ed11b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74c1770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74c2ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76dd122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76dd159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76dd1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b2cd5d in IA__gtk_recent_info_get_short_name (info=0x850a5a8)
    at gtkrecentmanager.c:2208
#11 0xb7b2cdba in IA__gtk_recent_info_get_display_name (info=0x850a5a8)
    at gtkrecentmanager.c:1588
#12 0xb7b28591 in idle_populate_func (data=0x83adf50)
    at gtkrecentchoosermenu.c:902
#13 0xb76d2aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb76d4802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb76d77df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb76d7b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7ad6574 in IA__gtk_main () at gtkmain.c:1024
#18 0x08061d8c in main ()

Thread 1 (Thread -1225644368 (LWP 5650)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75d9323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ed11b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74c1770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74c2ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76dd122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76dd159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76dd1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b2cd5d in IA__gtk_recent_info_get_short_name (info=0x850a5a8)
    at gtkrecentmanager.c:2208
	validated = -1211968325
	short_name = (gchar *) 0x0
	__PRETTY_FUNCTION__ = "IA__gtk_recent_info_get_short_name"
#11 0xb7b2cdba in IA__gtk_recent_info_get_display_name (info=0x850a5a8)
    at gtkrecentmanager.c:1588
	__PRETTY_FUNCTION__ = "IA__gtk_recent_info_get_display_name"
#12 0xb7b28591 in idle_populate_func (data=0x83adf50)
    at gtkrecentchoosermenu.c:902
	name = <value optimized out>
	escaped = <value optimized out>
	priv = (GtkRecentChooserMenuPrivate *) 0x83af128
	info = (GtkRecentInfo *) 0x850a5a8
	retval = <value optimized out>
	item = <value optimized out>
#13 0xb76d2aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb76d4802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb76d77df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb76d7b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7ad6574 in IA__gtk_main () at gtkmain.c:1024
	tmp_list = (GList *) 0x5
	functions = (GList *) 0x0
	init = (GtkInitFunction *) 0xbfc077f4
	loop = (GMainLoop *) 0x823f478
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


i use ubuntu edgy in dell inspiron 6400
THANXXXX

---

### Post by ComplexNumber on 2007-04-14
are you running beryl? if so, change it to metacity and see if that clears up the problem.

---

### Post by eldersoares on 2007-04-14
i'm using metacity :(
actually, i think the problem is before the gnome-panel starts, 'cause that boring song when entering gnome doesnt sound. i have had some problems w/ dbus some time ago... i dont even know very well what dbus is but i might be related... im uninstalling and installing lots of things, all the libs that appeared in bugzilla...
the most strange was that the problem started w/ this file .bin that i downloaded and renamed to iso.... when i tried to extract, the file disappeared and gnome-panel CRASHED!!!!

some (bad) news:
i thought it could be some conf problem. so i renamed the $HOME/.gconf dir. well, the start sound came back but the panel no!!!!!

thanks anyway

---

### Post by eldersoares on 2007-04-14
well, i tried all day but i couldn't. now i installed kde and ill try to reinstall all the gnome again....

---

