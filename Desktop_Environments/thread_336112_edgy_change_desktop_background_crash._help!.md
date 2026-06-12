---
title: "edgy: change desktop background crash. help!"
date: 2007-01-11
forum: Desktop Environments
---

### Post by benma on 2007-01-11
Can anyone please help me?
I have edgy for about a month, and just desided to change the desktop background.
When i right click on the desktop and choose: change desktop background, i get the
bug reporting tool and the background change prog crashes. i saved the bug report:



Memory status: size: 54464512 vsize: 0 resident: 54464512 share: 0 rss: 14069760 rss_rlim: 0
CPU usage: start_time: 1168518476 rtime: 0 utime: 148 stime: 0 cutime:134 cstime: 0 timeout: 14 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/control-center'

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
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225550160 (LWP 15134)]
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
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb77e3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eb31b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb78a2722 in g_type_check_instance_cast ()
   from /usr/lib/libgobject-2.0.so.0
#5  0x0804e809 in ?? ()
#6  0x00000001 in ?? ()
#7  0x080a9298 in ?? ()
#8  0xb77d4120 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
#9  0x083170c0 in ?? ()
#10 0xb77f0464 in ?? () from /usr/lib/libglib-2.0.so.0
#11 0xb78e7538 in ?? ()
#12 0xb7f29ff4 in ?? () from /lib/ld-linux.so.2
#13 0xb78e7000 in ?? ()
#14 0xb78b9974 in ?? () from /usr/lib/libgconf-2.so.4
#15 0xbfbfdaf0 in ?? ()
#16 0xb7f1c942 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
#17 0xb78d6307 in gconf_client_get_type () from /usr/lib/libgconf-2.so.4
#18 0xb78c900b in gconf_listeners_notify () from /usr/lib/libgconf-2.so.4
#19 0xb78d6664 in gconf_client_value_changed () from /usr/lib/libgconf-2.so.4
#20 0xb78d6741 in gconf_client_value_changed () from /usr/lib/libgconf-2.so.4
#21 0xb7813aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#22 0xb7815802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#23 0xb78187df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#24 0xb7818b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#25 0xb7c2a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#26 0x0804d1fa in ?? ()
#27 0x08316000 in ?? ()
#28 0x08051cea in _IO_stdin_used ()
#29 0x0804d240 in ?? ()
#30 0x0809c1d8 in ?? ()
#31 0x00000000 in ?? ()

Thread 1 (Thread -1225550160 (LWP 15134)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb77e3323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eb31b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb78a2722 in g_type_check_instance_cast ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#5  0x0804e809 in ?? ()
No symbol table info available.
#6  0x00000001 in ?? ()
No symbol table info available.
#7  0x080a9298 in ?? ()
No symbol table info available.
#8  0xb77d4120 in __after_morecore_hook () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#9  0x083170c0 in ?? ()
No symbol table info available.
#10 0xb77f0464 in ?? () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb78e7538 in ?? ()
No symbol table info available.
#12 0xb7f29ff4 in ?? () from /lib/ld-linux.so.2
No symbol table info available.
#13 0xb78e7000 in ?? ()
No symbol table info available.
#14 0xb78b9974 in ?? () from /usr/lib/libgconf-2.so.4
No symbol table info available.
#15 0xbfbfdaf0 in ?? ()
No symbol table info available.
#16 0xb7f1c942 in _dl_rtld_di_serinfo () from /lib/ld-linux.so.2
No symbol table info available.
#17 0xb78d6307 in gconf_client_get_type () from /usr/lib/libgconf-2.so.4
No symbol table info available.
#18 0xb78c900b in gconf_listeners_notify () from /usr/lib/libgconf-2.so.4
No symbol table info available.
#19 0xb78d6664 in gconf_client_value_changed () from /usr/lib/libgconf-2.so.4
No symbol table info available.
#20 0xb78d6741 in gconf_client_value_changed () from /usr/lib/libgconf-2.so.4
No symbol table info available.
#21 0xb7813aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#22 0xb7815802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#23 0xb78187df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#24 0xb7818b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#25 0xb7c2a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#26 0x0804d1fa in ?? ()
No symbol table info available.
#27 0x08316000 in ?? ()
No symbol table info available.
#28 0x08051cea in _IO_stdin_used ()
No symbol table info available.
#29 0x0804d240 in ?? ()
No symbol table info available.
#30 0x0809c1d8 in ?? ()
No symbol table info available.
#31 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

