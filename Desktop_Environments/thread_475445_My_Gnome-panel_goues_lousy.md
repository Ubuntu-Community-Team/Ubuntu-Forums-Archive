---
title: "My Gnome-panel goues lousy"
date: 2007-06-16
forum: Desktop Environments
---

### Post by Ji31 on 2007-06-16
Today morning I have start my computer and I have my Gnome-panel lousy. I can see just Aplications, Places and System, but these are not function and I can't to see any others (minimalized programs, clocks atd.)

I have tried to  reinstall packs gnome-panel and gnome-panel-data but nothing helped.

The error which I get is:
```

Memory status: size: 42500096 vsize: 0 resident: 42500096 share: 0 rss: 18046976 rss_rlim: 0
CPU usage: start_time: 1181983684 rtime: 0 utime: 57 stime: 0 cutime:51 cstime: 0 timeout: 6 it_real_value: 0 frequency: 0

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
[Thread debugging using libthread_db enabled]
[New Thread -1225873744 (LWP 4688)]
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
#1  0xb75a1323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e991b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7489770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb748aef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb76a5122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb76a5159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb76a51d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7af4d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7af4dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7af0591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb769aaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb769c802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb769f7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb769fb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7a9e574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225873744 (LWP 4688)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75a1323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e991b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7489770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb748aef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb76a5122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76a5159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb76a51d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7af4d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7af4dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7af0591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb769aaa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb769c802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb769f7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb769fb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7a9e574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```
What can cause that? Thanks

---

### Post by Ji31 on 2007-06-17
Hi,

nobody knows please? I have tried to delete/rename */home/my_user/.gconf/apps/panel* but after the reboot it stay without that directory and nothing was created by default.

Also *sudo dpkg-reconfigure gnome-panel* didn't help.

And I have created a new user "lama" and there is everything ok...

So does anybody please know what to do?

Thank you a lot..

---

### Post by Ji31 on 2007-06-17
Please, please, please, nobody knows?

---

### Post by neon777 on 2007-06-18
Removing .recently_used* in my home directory helped...

---

