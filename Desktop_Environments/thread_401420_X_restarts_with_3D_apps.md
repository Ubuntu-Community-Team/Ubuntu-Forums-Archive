---
title: "X restarts with 3D apps"
date: 2007-04-04
forum: Desktop Environments
---

### Post by el mariachi on 2007-04-04
After inputing glxinfo or starting a 3D app (like Planeshift) X restarts and takes me back to the login screen. No error message is shown.

I'm running an almost fresh Ubuntu install. No beryl whatsoever. It was working this morning, and I didn't make any change, at least that I know about.

EDIT: wine also makes it crash

this time I got an error report
```
Memory status: size: 32239616 vsize: 0 resident: 32239616 share: 0 rss: 7159808 rss_rlim: 0
CPU usage: start_time: 1175715626 rtime: 0 utime: 2 stime: 0 cutime:2 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-power-manager'

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
[New Thread -1225595216 (LWP 6094)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7991323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f0b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb761e6cc in dbus_g_method_return_error ()
   from /usr/lib/libdbus-glib-1.so.2
#5  0xb71da53e in g_slist_find_custom () from /usr/lib/libglib-2.0.so.0
#6  0xb761e602 in dbus_g_method_return_error ()
   from /usr/lib/libdbus-glib-1.so.2
#7  0xb71b5856 in g_hash_table_foreach () from /usr/lib/libglib-2.0.so.0
#8  0xb761e692 in dbus_g_method_return_error ()
   from /usr/lib/libdbus-glib-1.so.2
#9  0xb762144a in dbus_g_proxy_new_for_name ()
   from /usr/lib/libdbus-glib-1.so.2
#10 0xb7621bee in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
#11 0xb726fbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#12 0xb72707e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#13 0xb72708f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#14 0xb7620268 in dbus_g_proxy_get_bus_name ()
   from /usr/lib/libdbus-glib-1.so.2
#15 0x08061aa8 in ?? ()
#16 0x08061f67 in ?? ()
#17 0xb726a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#18 0xb727ab93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#19 0xb727c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#20 0xb727c279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#21 0x08050220 in ?? ()
#22 0xb761aad4 in dbus_g_connection_open () from /usr/lib/libdbus-glib-1.so.2
#23 0xb7621ad6 in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
#24 0xb726a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#25 0xb727ab93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#26 0xb727c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#27 0xb727c279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#28 0xb762297b in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
#29 0xb72358ce in dbus_connection_dispatch () from /usr/lib/libdbus-1.so.3
#30 0xb761a51d in dbus_server_setup_with_g_main ()
   from /usr/lib/libdbus-glib-1.so.2
#31 0xb71c2802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#32 0xb71c57df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#33 0xb71c5b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#34 0x08051e21 in ?? ()
#35 0xb706e8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#36 0x0804dbe1 in ?? ()

Thread 1 (Thread -1225595216 (LWP 6094)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7991323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f0b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb761e6cc in dbus_g_method_return_error ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#5  0xb71da53e in g_slist_find_custom () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb761e602 in dbus_g_method_return_error ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#7  0xb71b5856 in g_hash_table_foreach () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb761e692 in dbus_g_method_return_error ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#9  0xb762144a in dbus_g_proxy_new_for_name ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#10 0xb7621bee in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#11 0xb726fbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#12 0xb72707e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb72708f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb7620268 in dbus_g_proxy_get_bus_name ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#15 0x08061aa8 in ?? ()
No symbol table info available.
#16 0x08061f67 in ?? ()
No symbol table info available.
#17 0xb726a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb727ab93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb727c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#20 0xb727c279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#21 0x08050220 in ?? ()
No symbol table info available.
#22 0xb761aad4 in dbus_g_connection_open () from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#23 0xb7621ad6 in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#24 0xb726a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb727ab93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb727c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb727c279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb762297b in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#29 0xb72358ce in dbus_connection_dispatch () from /usr/lib/libdbus-1.so.3
No symbol table info available.
#30 0xb761a51d in dbus_server_setup_with_g_main ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#31 0xb71c2802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#32 0xb71c57df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#33 0xb71c5b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#34 0x08051e21 in ?? ()
No symbol table info available.
#35 0xb706e8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#36 0x0804dbe1 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```Gnome power management?


Could the mods lock/erase this thread? I found another one already regarding this issue, sorry.

---

### Post by Sqwishy on 2007-04-04
If you had a recent xorg update that's probobly the problem, you need to reinstall your drivers, its easiest with envy [[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)] then it should be fine.
this happened to me today and this is what i did.
:D

---

### Post by hackworth on 2007-04-05
Sweet, I had the same problem and reinstalling fixed it. Thanks!

---

