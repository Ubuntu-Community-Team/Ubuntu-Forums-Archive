---
title: "gnome-panel refuses to run"
date: 2007-03-24
forum: Desktop Environments
---

### Post by vkkim on 2007-03-24
I am running Edgy, using Gnome and Beryl and Emerald for my wm.  Suddenly out of the blue (I think I was extracting files from an archive at the time) gnome-panel crashes.  I close the bug-buddy window, gnome-panel restarts and crashes immediately.  Only the "Applications, Places, System" buttons are visible, but not functional. (Edit: Now they too are gone.)  The bug report is as follows:

```
Memory status: size: 69603328 vsize: 0 resident: 69603328 share: 0 rss: 12959744 rss_rlim: 0
CPU usage: start_time: 1174779573 rtime: 0 utime: 99 stime: 0 cutime:94 cstime: 0 timeout: 5 it_real_value: 0 frequency: 0

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
[New Thread -1225013584 (LWP 17945)]
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
#1  0xb7673323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f6b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb755b770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb755cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7777122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7777159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77771d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7bc6d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7bc6dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7bc2591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb776caa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb776e802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77717df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7771b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b70574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225013584 (LWP 17945)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7673323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f6b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb755b770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb755cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7777122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7777159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77771d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7bc6d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7bc6dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7bc2591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb776caa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb776e802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77717df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7771b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b70574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

Restarting GDM, metacity, or beryl has no effect.  I can live without it, but it would be nice to have.

---

### Post by vkkim on 2007-03-26
Help!  Although I said I can live with it, it's really starting to hamper my productivity.  [Bump.]

---

### Post by ComplexNumber on 2007-03-26
what happens when you go back to using metacity?

---

### Post by vkkim on 2007-03-26
Surprisingly, it works in metacity!  (I'm pretty sure I had tried it previously, but it's entirely possible that I had just forgotten.)  And when I restart beryl, gnome-panel continues to work.  That's really strange... but I'm happy as long as it works.  Thanks!

---

### Post by General_Ts0 on 2007-04-01
Ack, I'm getting the same thing.  I was trying to extract files from an .iso when this frustrating cycle hit me.  I haven't  installed anything, I tried burning a CD (from the iso) and when I extracted the ISO, wham !

any fix ? I can get in as root via recovery mode > startx

---

