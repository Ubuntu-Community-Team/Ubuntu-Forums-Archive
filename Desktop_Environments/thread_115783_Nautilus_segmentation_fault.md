---
title: "Nautilus segmentation fault"
date: 2006-01-11
forum: Desktop Environments
---

### Post by garak on 2006-01-11
Each time I try to open a file with double-click, Nautilus exit with an error and restart (same if I right-click and select "open with...")

```
Backtrace was generated from '/usr/bin/nautilus'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
`system-supplied DSO at 0xffffe000' has disappeared; keeping its symbols.
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1226348864 (LWP 18253)]
[New Thread -1237189712 (LWP 18271)]
[New Thread -1236923472 (LWP 18270)]
[New Thread -1236657232 (LWP 18269)]
[New Thread -1236390992 (LWP 18268)]
[New Thread -1236124752 (LWP 18267)]
[New Thread -1235858512 (LWP 18266)]
[New Thread -1234457680 (LWP 18259)]
[New Thread -1228825680 (LWP 18255)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb76574ab in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7d20508 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7415b78 in strcmp () from /lib/tls/i686/cmov/libc.so.6
#5  0xb78ca6f4 in gnome_vfs_uris_match () from /usr/lib/libgnomevfs-2.so.0
#6  0xb7ec1ec0 in egg_recent_model_add_full ()
   from /usr/lib/libnautilus-private.so.2
#7  0xb7ec2104 in egg_recent_model_add ()
   from /usr/lib/libnautilus-private.so.2
#8  0x080a2867 in fm_directory_view_stop_batching_selection_changes ()
#9  0xb7e73c77 in nautilus_directory_schedule_dequeue_pending ()
   from /usr/lib/libnautilus-private.so.2
#10 0xb7e75252 in nautilus_directory_async_state_changed ()
   from /usr/lib/libnautilus-private.so.2
#11 0xb7e77bba in nautilus_directory_call_when_ready_internal ()
   from /usr/lib/libnautilus-private.so.2
#12 0xb7ebb319 in nautilus_vfs_file_get_type ()
   from /usr/lib/libnautilus-private.so.2
#13 0xb7e9047a in nautilus_file_call_when_ready ()
   from /usr/lib/libnautilus-private.so.2
#14 0x080a0331 in fm_directory_view_move_copy_items ()
#15 0x080a0406 in fm_directory_view_activate_files ()
#16 0x080abbd2 in fm_icon_view_get_type ()
#17 0xb76733ae in g_cclosure_marshal_VOID__POINTER ()
   from /usr/lib/libgobject-2.0.so.0
#18 0xb76673a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#19 0xb7675b13 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#20 0xb7677150 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#21 0xb76774c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#22 0xb7e9d4ca in nautilus_icon_container_get_selection ()
   from /usr/lib/libnautilus-private.so.2
#23 0xb7ea4162 in nautilus_icon_container_move_icon ()
   from /usr/lib/libnautilus-private.so.2
#24 0xb7dfeb68 in eel_marshal_BOOLEAN__BOXED () from /usr/lib/libeel-2.so.2
#25 0xb76673a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#26 0xb7675b13 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#27 0xb7676ec3 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#28 0xb76774c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#29 0xb7dde509 in eel_canvas_window_to_world () from /usr/lib/libeel-2.so.2
#30 0xb7ea4695 in nautilus_icon_container_unselect_all ()
   from /usr/lib/libnautilus-private.so.2
#31 0xb7aed02c in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#32 0xb7666d75 in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#33 0xb76673a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#34 0xb7675c9f in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#35 0xb7676ec3 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#36 0xb76774c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#37 0xb7bcf16f in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb7aeb767 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb7aebbc8 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#40 0xb798fb2d in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#41 0xb75ef4ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#42 0xb75f24f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#43 0xb75f27e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#44 0xb7aeae65 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#45 0x08079ac6 in main ()

Thread 9 (Thread -1228825680 (LWP 18255)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb746b0f4 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb75f2348 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb75f27e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb76cc37e in link_thread_io_context () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 8 (Thread -1234457680 (LWP 18259)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7653c96 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78c592b in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#3  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 7 (Thread -1235858512 (LWP 18266)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7653c96 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78c592b in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#3  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 6 (Thread -1236124752 (LWP 18267)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7653c96 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78c592b in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#3  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 5 (Thread -1236390992 (LWP 18268)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7653c96 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78c592b in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#3  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 4 (Thread -1236657232 (LWP 18269)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7653c96 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78c592b in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#3  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 3 (Thread -1236923472 (LWP 18270)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7653c96 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78c592b in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#3  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 2 (Thread -1237189712 (LWP 18271)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7653c96 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb78c592b in _gnome_vfs_thread_pool_init ()
   from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#3  0xb760b8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7651361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb7474bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1226348864 (LWP 18253)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb76574ab in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7d20508 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7415b78 in strcmp () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb78ca6f4 in gnome_vfs_uris_match () from /usr/lib/libgnomevfs-2.so.0
No symbol table info available.
#6  0xb7ec1ec0 in egg_recent_model_add_full ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#7  0xb7ec2104 in egg_recent_model_add ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#8  0x080a2867 in fm_directory_view_stop_batching_selection_changes ()
No symbol table info available.
#9  0xb7e73c77 in nautilus_directory_schedule_dequeue_pending ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#10 0xb7e75252 in nautilus_directory_async_state_changed ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#11 0xb7e77bba in nautilus_directory_call_when_ready_internal ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#12 0xb7ebb319 in nautilus_vfs_file_get_type ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#13 0xb7e9047a in nautilus_file_call_when_ready ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#14 0x080a0331 in fm_directory_view_move_copy_items ()
No symbol table info available.
#15 0x080a0406 in fm_directory_view_activate_files ()
No symbol table info available.
#16 0x080abbd2 in fm_icon_view_get_type ()
No symbol table info available.
#17 0xb76733ae in g_cclosure_marshal_VOID__POINTER ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb76673a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb7675b13 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#20 0xb7677150 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#21 0xb76774c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb7e9d4ca in nautilus_icon_container_get_selection ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#23 0xb7ea4162 in nautilus_icon_container_move_icon ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#24 0xb7dfeb68 in eel_marshal_BOOLEAN__BOXED () from /usr/lib/libeel-2.so.2
No symbol table info available.
#25 0xb76673a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb7675b13 in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb7676ec3 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb76774c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0xb7dde509 in eel_canvas_window_to_world () from /usr/lib/libeel-2.so.2
No symbol table info available.
#30 0xb7ea4695 in nautilus_icon_container_unselect_all ()
   from /usr/lib/libnautilus-private.so.2
No symbol table info available.
#31 0xb7aed02c in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#32 0xb7666d75 in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#33 0xb76673a8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0xb7675c9f in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0xb7676ec3 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#36 0xb76774c3 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#37 0xb7bcf16f in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#38 0xb7aeb767 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#39 0xb7aebbc8 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#40 0xb798fb2d in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#41 0xb75ef4ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#42 0xb75f24f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#43 0xb75f27e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#44 0xb7aeae65 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#45 0x08079ac6 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

---

