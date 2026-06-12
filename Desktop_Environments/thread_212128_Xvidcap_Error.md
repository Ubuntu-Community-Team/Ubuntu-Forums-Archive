---
title: "Xvidcap Error"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Irony on 2006-07-09
I've installed *xvidcap_1.1.4pre3_i386.deb* and it seems to work fine. The only irritation is that on stopping a screen video recording session I get an error box popping up with 'xvidcap has quit unexpectedly' with options to restart, close or inform developers.

Here is the bug report. Does anyone know what it means?

[PHP]Backtrace was generated from '/usr/bin/xvidcap'

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225283904 (LWP 14375)]
[New Thread -1247253584 (LWP 14437)]
[New Thread -1237943376 (LWP 14423)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb74b321d in pthread_join () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08061d04 in xvc_capture_stop ()
#3  0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#4  0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#5  0xb75622ea in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#6  0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#7  0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#8  0xb7af9f56 in gtk_toggle_tool_button_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#10 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#11 0xb75622ea in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#12 0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#13 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#14 0xb7af9661 in gtk_toggle_button_toggled ()
   from /usr/lib/libgtk-x11-2.0.so.0
#15 0xb7af99e4 in gtk_toggle_button_set_inconsistent ()
   from /usr/lib/libgtk-x11-2.0.so.0
#16 0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#17 0xb755316f in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#18 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#19 0xb75625cc in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#20 0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#21 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#22 0xb799e49f in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
#23 0xb7af9a42 in gtk_toggle_button_set_inconsistent ()
   from /usr/lib/libgtk-x11-2.0.so.0
#24 0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#25 0xb755316f in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#26 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#27 0xb75625cc in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#28 0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#29 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#30 0xb799e41c in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb799f38c in _gtk_button_paint () from /usr/lib/libgtk-x11-2.0.so.0
#32 0xb7a5f8f0 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#33 0xb755316f in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
#34 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#35 0xb75629ce in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
#36 0xb7563886 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#37 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#38 0xb7b41dbf in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb7a5e06d in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#40 0xb7a5e47b in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#41 0xb77dddec in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#42 0xb74e28d6 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#43 0xb74e5996 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#44 0xb74e5cb8 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#45 0xb7a5d775 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#46 0x08061025 in xvc_ui_run ()
#47 0x0806c929 in main ()

Thread 3 (Thread -1237943376 (LWP 14423)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7353136 in nanosleep () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb738998a in usleep () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#3  0x08061750 in do_record_thread ()
No symbol table info available.
#4  0xb74b2341 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb73904ee in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 2 (Thread -1247253584 (LWP 14437)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74b848b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ecc8e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x080e8c72 in ff_jpeg_fdct_islow ()
No symbol table info available.
#5  0x080c620d in avcodec_encode_audio ()
No symbol table info available.
#6  0x080702a0 in capture_audio_thread ()
No symbol table info available.
#7  0xb74b2341 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#8  0xb73904ee in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1225283904 (LWP 14375)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74b321d in pthread_join () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0x08061d04 in xvc_capture_stop ()
No symbol table info available.
#3  0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#4  0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#5  0xb75622ea in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#6  0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb7af9f56 in gtk_toggle_tool_button_get_type ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#11 0xb75622ea in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#12 0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb7af9661 in gtk_toggle_button_toggled ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#15 0xb7af99e4 in gtk_toggle_button_set_inconsistent ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#16 0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb755316f in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb75625cc in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#20 0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#21 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb799e49f in gtk_button_clicked () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#23 0xb7af9a42 in gtk_toggle_button_set_inconsistent ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#24 0xb755f423 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb755316f in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb75625cc in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb7563b19 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb799e41c in gtk_button_released () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#31 0xb799f38c in _gtk_button_paint () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#32 0xb7a5f8f0 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#33 0xb755316f in g_cclosure_new_swap () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0xb755379f in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0xb75629ce in g_signal_stop_emission () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#36 0xb7563886 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#37 0xb7563e89 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#38 0xb7b41dbf in gtk_widget_activate () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#39 0xb7a5e06d in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#40 0xb7a5e47b in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#41 0xb77dddec in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#42 0xb74e28d6 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#43 0xb74e5996 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#44 0xb74e5cb8 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#45 0xb7a5d775 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#46 0x08061025 in xvc_ui_run ()
No symbol table info available.
#47 0x0806c929 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()[/PHP]

---

