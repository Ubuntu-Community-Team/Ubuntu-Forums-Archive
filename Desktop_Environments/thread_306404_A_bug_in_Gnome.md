---
title: "A bug in Gnome"
date: 2006-11-24
forum: Desktop Environments
---

### Post by Richard Roy on 2006-11-24
Hello,

I installed ubuntu (edgy), and then KDE (kubuntu-desktop).
When I wanted to return to Gnome, I'm getting each time the massage:

--------
There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The Settings Daemon restarted too many times.

GNOME will still try to restart the Settings Daemon next time you log in.
---------


The bug report is:
Memory status: size: 37740544 vsize: 0 resident: 37740544 share: 0 rss: 13295616 rss_rlim: 0
CPU usage: start_time: 1164423649 rtime: 0 utime: 120 stime: 0 cutime:114 cstime: 0 timeout: 6 it_real_value: 0 frequency: 5

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
[New Thread -1225242960 (LWP 11979)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb763b323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f331b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb6e41a70 in ?? ()
#5  0xb79be021 in gdk_x11_drawable_get_xdisplay ()
   from /usr/lib/libgdk-x11-2.0.so.0
#6  0xb79bf78c in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
#7  0xb79c13bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#8  0xb79c17bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#9  0xb7736802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#10 0xb77397df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#11 0xb7739b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#12 0xb7b38574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x08061d8c in main ()

Thread 1 (Thread -1225242960 (LWP 11979)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb763b323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f331b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb6e41a70 in ?? ()
No symbol table info available.
#5  0xb79be021 in gdk_x11_drawable_get_xdisplay ()
   from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#6  0xb79bf78c in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#7  0xb79c13bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#8  0xb79c17bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#9  0xb7736802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb77397df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb7739b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb7b38574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


How do I solve this bug ?

---

### Post by K.Mandla on 2006-11-25
Dig around on [Launchpad ]("http://www.launchpad.net/malone")and see if you can find anything similar. If not, you might want to post the bug there and see if it can be confirmed.

It's possible that the error occurs in Gnome itself, which could require the attention of the Gnome developers before it gets corrected in Ubuntu.

---

