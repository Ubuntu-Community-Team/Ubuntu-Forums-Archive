---
title: "Synaptic and Gnome crash"
date: 2008-01-04
forum: Desktop Environments
---

### Post by venkatagiridhar on 2008-01-04
I've installed feisty on my system a week ago and the performance and response time is now considerably lower than it was first installed. Whenever i try to resize the tabs by clicking on the properties tab, the system simply hangs up.

The synaptic pakage manager crashes whenever i open it.
Here's the response i get after it crashed.


giridhar@giridhar-desktop:~$ sudo synaptic
*** glibc detected *** synaptic: munmap_chunk(): invalid pointer: 0x082c1040 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(cfree+0x1bb)[0xb733092b]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb768b961]
/usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so[0xb702ae96]
/usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so[0xb7026843]
/usr/lib/gtk-2.0/2.10.0/engines/libindustrial.so[0xb70281c3]
/usr/lib/libgtk-x11-2.0.so.0(gtk_paint_box+0xaa)[0xb7d06fea]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_button_paint+0x29a)[0xb7bb778a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bb788e]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c911de]
/usr/lib/libgobject-2.0.so.0[0xb7722f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20c)[0xb772485c]
/usr/lib/libgobject-2.0.so.0[0xb7735973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb773660f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7736a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7daf498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x139)[0xb7bf3099]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bf3131]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bb22b1]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb7bf3b2b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bf3bf4]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c911de]
/usr/lib/libgobject-2.0.so.0[0xb7722f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20c)[0xb772485c]
/usr/lib/libgobject-2.0.so.0[0xb7735973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb773660f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7736a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7daf498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x139)[0xb7bf3099]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bf3131]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bb22b1]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb7bf3b2b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bf3bf4]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c911de]
/usr/lib/libgobject-2.0.so.0[0xb7722f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x20c)[0xb772485c]
/usr/lib/libgobject-2.0.so.0[0xb7735973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb773660f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7736a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7daf498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x139)[0xb7bf3099]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bf3131]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bae3df]
/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x6b)[0xb7bf3b2b]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bf3bf4]
/usr/lib/libgtk-x11-2.0.so.0[0xb7dc6ad1]
/usr/lib/libgtk-x11-2.0.so.0(_gtk_marshal_BOOLEAN__BOXED+0x5e)[0xb7c911de]
/usr/lib/libgobject-2.0.so.0[0xb7722f89]
/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x122)[0xb7724772]
/usr/lib/libgobject-2.0.so.0[0xb7735973]
/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68f)[0xb773660f]
/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29)[0xb7736a09]
/usr/lib/libgtk-x11-2.0.so.0[0xb7daf498]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x507)[0xb7c8b787]
/usr/lib/libgdk-x11-2.0.so.0[0xb79c306f]
/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xba)[0xb79c373a]
/usr/lib/libgtk-x11-2.0.so.0[0xb7bf3d8f]
/usr/lib/libgdk-x11-2.0.so.0[0xb79a95e8]
/usr/lib/libglib-2.0.so.0[0xb7682551]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x17c)[0xb768411c]
/usr/lib/libglib-2.0.so.0[0xb768755f]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1a9)[0xb7687909]
/usr/lib/libgtk-x11-2.0.so.0(gtk_dialog_run+0x18b)[0xb7c0577b]
synaptic[0x8087b31]
======= Memory map: ========
08048000-080fd000 r-xp 00000000 08:07 344906     /usr/sbin/synaptic
080fd000-08101000 rw-p 000b4000 08:07 344906     /usr/sbin/synaptic
08101000-08a73000 rw-p 08101000 00:00 0          [heap]
b52da000-b5472000 rw-p b52da000 00:00 0 
b5472000-b6581000 r--s 00000000 08:07 674647     /var/cache/apt/pkgcache.bin
b6581000-b65e1000 rw-s 00000000 00:08 1474577    /SYSV00000000 (deleted)
b65e1000-b6657000 r--p 00000000 08:07 558133     /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans-Bold.ttf
b6657000-b665d000 r-xp 00000000 08:07 409227     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpAborted (core dumped)


what's wrong??. Please help.
System Specs:

P4 1500Hz, 32MB Nvidia TNT2 graphics card

---

