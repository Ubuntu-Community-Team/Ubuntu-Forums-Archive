---
title: "gnome-panel crashes right after boot"
date: 2006-11-10
forum: Desktop Environments
---

### Post by rubenturner on 2006-11-10
I was surfing the web when gnome-panel suddenly crashed. Since then, everytime I reboot, the panel crashes right after boot up. I can see the taskbar and the menus, but not the applets, clock, etc. right after the crash, bug-buddy starts.
bug-buddy shows me the following output:

```
Memory status: size: 36818944 vsize: 0 resident: 36818944 share: 0 rss: 16711680 rss_rlim: 0
CPU usage: start_time: 1163145498 rtime: 0 utime: 76 stime: 0 cutime:69 cstime: 0 timeout: 7 it_real_value: 0 frequency: 0

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
[New Thread -1225165136 (LWP 5496)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb764d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f451b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7535770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7536ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7751122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7751159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77511d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7ba0d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7ba0dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b9c591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7746aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7748802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb774b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb774bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b4a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225165136 (LWP 5496)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb764d323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f451b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7535770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7536ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7751122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7751159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77511d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7ba0d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7ba0dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b9c591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7746aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7748802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb774b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb774bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b4a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

If i close bug-buddy, panel tries to restart and the same error occurs again.

---

### Post by chrx on 2006-11-10
sadly my gnome broke too when i was trying extracting an iso-file.

now, no panels show up at all, only bug-buddy.

don't no what to do..do i have to reinstall everything?

```
Memory status: size: 38567936 vsize: 0 resident: 38567936 share: 0 rss: 16613376 rss_rlim: 0
CPU usage: start_time: 1163184659 rtime: 0 utime: 61 stime: 0 cutime:56 cstime: 0 timeout: 5 it_real_value: 0 frequency: 0

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
[New Thread -1225443664 (LWP 6875)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7609323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f011b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74f1770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74f2ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb770d122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb770d159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb770d1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b5cd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b5cdba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b58591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7702aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7704802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77077df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7707b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b06574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225443664 (LWP 6875)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7609323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f011b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74f1770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74f2ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb770d122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb770d159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb770d1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b5cd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b5cdba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b58591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7702aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7704802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77077df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7707b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b06574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

```
chriz@chriz-desktop:~$ gnome-panel

(gnome-panel:7632): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -1 and height 24

Gtk-ERROR **: file gtkrecentmanager.c: line 2248 (get_uri_shortname_for_display): assertion failed: (name != NULL)
aborting...

** (bug-buddy:7650): WARNING **: Kunde inte läsa in ikon för Öppna mapp

```

---

### Post by rubenturner on 2006-11-12
In gconf, I just added all my running applets to the key apps/panel/global/disabled_panels  - since then, everything is working fine - and believe it or not, even the applets work as they should...

---

### Post by chrx on 2006-11-13
a bug was reported about this.
[https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/63465](https://launchpad.net/distros/ubuntu/+source/gnome-panel/+bug/63465)

when i threw away the iso i tried to open gnome-panel was ok., but im not gonna try it again.

---

### Post by nfs510 on 2006-11-20
I have a similar problem. Could anyone inform me how to solve it?

My Bugreport:
Memory status: size: 86757376 vsize: 0 resident: 86757376 share: 0 rss: 25837568 rss_rlim: 0
CPU usage: start_time: 1164076906 rtime: 0 utime: 80 stime: 0 cutime:72 cstime: 0 timeout: 8 it_real_value: 0 frequency: 12

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
[New Thread -1225238864 (LWP 4759)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#2  0xb7f341b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb6e1fa70 in ?? ()
#5  0xb79be021 in gdk_x11_drawable_get_xdisplay ()
   from /usr/lib/libgdk-x11-2.0.so.0
#6  0xb79bf78c in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
#7  0xb79c13bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#8  0xb79c17bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#9  0xb7737802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#10 0xb773a7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#11 0xb773ab89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#12 0xb7b39574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x08061d8c in main ()

Thread 1 (Thread -1225238864 (LWP 4759)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb763b323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f341b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb6e1fa70 in ?? ()
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
#9  0xb7737802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb773a7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb773ab89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb7b39574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by rjz35 on 2006-11-21
Deleting ~/.recently-used.xbel did the trick for me, its in your home dir

---

### Post by Ares Drake on 2006-11-24
> **rjz35 said:**
> Deleting ~/.recently-used.xbel did the trick for me, its in your home dir

Thanks a lot, that dit it for me as well!!

Cheers!

---

### Post by logos34 on 2007-02-07
> **rjz35 said:**
> Deleting ~/.recently-used.xbel did the trick for me, its in your home dir

Works for me too! :-)  What a lifesaver! 

I was beginning to think I'd finally managed to royally bork my edgy install...

---

