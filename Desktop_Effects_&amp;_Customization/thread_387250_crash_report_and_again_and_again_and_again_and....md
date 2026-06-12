---
title: "crash report and again and again and again and..."
date: 2007-03-18
forum: Desktop Effects &amp; Customization
---

### Post by WernerBrandt on 2007-03-18
Specs; 
Dell Latitude, Intel Centrino, ATI x300
Edgy release, Beryl

Beryl worked fine (well most of the time anyways :) ) no 

But yesterday I got this bug reporting tool / crash report and it keeps poppin'  up.

I cannot click any programs, ALT + F2 dont work.
Creating a launcher and thus opening a program works, If one knows the command, browser works.

Panel = nogo.

This is whats in the report:

```

Memory status: size: 53305344 vsize: 0 resident: 53305344 share: 0 rss: 12374016 rss_rlim: 0
CPU usage: start_time: 1174203276 rtime: 0 utime: 46 stime: 0 cutime:45 cstime: 0 timeout: 1 it_real_value: 0 frequency: 0

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
[New Thread -1225206096 (LWP 5241)]
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
#1  0xb7644323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f3c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb752c770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb752def3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7748122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7748159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77481d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b97d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b97dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b93591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb773daa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb773f802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77427df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7742b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b41574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225206096 (LWP 5241)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7644323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f3c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb752c770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb752def3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7748122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7748159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77481d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b97d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b97dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b93591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb773daa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb773f802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77427df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7742b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b41574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

Any suggestions?

**BTW:**
1). Checked memory using memtest allready

2). using different sessions @ logon don ' t work, same results, also crash reports.
So default gnome AND/OR safe mode is a nogo too :(

3). two more reports attached

---

