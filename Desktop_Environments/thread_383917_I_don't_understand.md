---
title: "I don't understand"
date: 2007-03-13
forum: Desktop Environments
---

### Post by sdmike on 2007-03-13
I don't understand why gnome-panel is giving me errors. I get this from the debugger.

Memory status: size: 43085824 vsize: 0 resident: 43085824 share: 0 rss: 20840448 rss_rlim: 0
CPU usage: start_time: 1173834735 rtime: 0 utime: 86 stime: 0 cutime:78 cstime: 0 timeout: 8 it_real_value: 0 frequency: 0

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
[New Thread -1225861456 (LWP 5229)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb75a4323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e9c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb793a7bc in gdk_x11_window_set_user_time ()
   from /usr/lib/libgdk-x11-2.0.so.0
#5  0xb792a934 in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#6  0xb79299a3 in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
#7  0xb792a3bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#8  0xb792a7bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#9  0xb769f802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#10 0xb76a27df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#11 0xb76a2b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#12 0xb7aa1574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x08061d8c in main ()

Thread 1 (Thread -1225861456 (LWP 5229)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb75a4323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e9c1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb793a7bc in gdk_x11_window_set_user_time ()
   from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#5  0xb792a934 in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#6  0xb79299a3 in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#7  0xb792a3bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#8  0xb792a7bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#9  0xb769f802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb76a27df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb76a2b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb7aa1574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by tee2 on 2007-03-13
I'm having this problem as well. ([http://ubuntuforums.org/showthread.php?t=383911](http://ubuntuforums.org/showthread.php?t=383911))

:confused:

edit: What were you doing before this happened?

---

### Post by sdmike on 2007-03-14
Actually I did an update and everything is back to normal.

---

### Post by tee2 on 2007-03-14
What did you update?

---

### Post by tee2 on 2007-03-15
bump

---

### Post by sdmike on 2007-03-17
I just ran the updates and it worked.

---

