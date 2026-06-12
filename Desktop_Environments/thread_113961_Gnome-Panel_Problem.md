---
title: "Gnome-Panel Problem"
date: 2006-01-07
forum: Desktop Environments
---

### Post by vbmaster on 2006-01-07
omfg, the thing is this: i was naturally surfing on my breezy when I get a message of crashing on gnome panel. I didn't done absolutely anything that can cause this. I said do restart the aplication but the error keeps still and I don't know what to do. :( 

At the moment i'm on my root user, that at the entrance gives an error too but doesn't crash....

I'm going to my session and i'll edit this post with the error that shows to me there, and on my root session.

Thanks.

P.S.: i already tried to reinstall gnome-panel by synaptic, although i don't have acess to the menus of gnome-panel.

---

### Post by vbmaster on 2006-01-07
The error appears to be this:

```

Backtrace was generated from '/usr/bin/gnome-panel'

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
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1223375168 (LWP 8182)]
[New Thread -1229628496 (LWP 8207)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb77944ab in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f72508 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb77b0dcd in g_error_free () from /usr/lib/libglib-2.0.so.0
#5  0x080a6965 in panel_addto_event_box_get_type ()
#6  0x080a7377 in egg_recent_model_get_list ()
#7  0x080a787c in egg_recent_model_changed ()
#8  0x0808d349 in panel_recent_append_documents_menu ()
#9  0x0808bc89 in panel_menu_items_create_action_item ()
#10 0x0808c28a in panel_place_menu_item_new ()
#11 0x08087c28 in panel_menu_bar_get_type ()
#12 0xb7843991 in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#13 0xb782a366 in g_object_thaw_notify () from /usr/lib/libgobject-2.0.so.0
#14 0xb782a9d7 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#15 0xb782b569 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#16 0xb782b712 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#17 0x08087f50 in panel_menu_bar_load_from_gconf ()
#18 0x08072006 in panel_applet_on_load_queue ()
#19 0xb77c1750 in g_child_watch_add () from /usr/lib/libglib-2.0.so.0
#20 0xb77bf4ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#21 0xb77c24f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#22 0xb77c27e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#23 0xb7b36e65 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#24 0x080655f7 in main ()

Thread 2 (Thread -1229628496 (LWP 8207)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb771a0f4 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb77c2348 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb77c27e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7d2837e in link_thread_io_context () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb77db8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb778e361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb7723bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1223375168 (LWP 8182)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb77944ab in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f72508 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb77b0dcd in g_error_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0x080a6965 in panel_addto_event_box_get_type ()
No symbol table info available.
#6  0x080a7377 in egg_recent_model_get_list ()
No symbol table info available.
#7  0x080a787c in egg_recent_model_changed ()
No symbol table info available.
#8  0x0808d349 in panel_recent_append_documents_menu ()
No symbol table info available.
#9  0x0808bc89 in panel_menu_items_create_action_item ()
No symbol table info available.
#10 0x0808c28a in panel_place_menu_item_new ()
No symbol table info available.
#11 0x08087c28 in panel_menu_bar_get_type ()
No symbol table info available.
#12 0xb7843991 in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb782a366 in g_object_thaw_notify () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb782a9d7 in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb782b569 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb782b712 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0x08087f50 in panel_menu_bar_load_from_gconf ()
No symbol table info available.
#18 0x08072006 in panel_applet_on_load_queue ()
No symbol table info available.
#19 0xb77c1750 in g_child_watch_add () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#20 0xb77bf4ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#21 0xb77c24f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#22 0xb77c27e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#23 0xb7b36e65 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#24 0x080655f7 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

I need urgent help :'(

---

### Post by vbmaster on 2006-01-07
Hey guys...i found this on my xsessionerrors:

** (gnome-panel:8324): WARNING **: panel-applet-frame.c:1240: failed to load applet OAFIID:GNOME_Panel_TrashApplet:

how do i do to disable the trash aplet?

---

### Post by art on 2006-01-07
When it asks to restart, do not restart it. What happens then?

---

### Post by tomash_cz on 2006-01-08
Hello, please there is urgent of help for a total newbie. My breezy runned well until today, when I launched gnome-terminal it showed following error:



(gnome-terminal:12896): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:12896): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Launching a SCIM daemon with Socket FrontEnd...
tomash@baobei:/usr/share/gnome-terminal$ cd
tomash@baobei:~$ gnome-terminal

(gnome-terminal:12899): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:12899): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Launching a SCIM daemon with Socket FrontEnd...


The problem is so critical, that i can not launch evolution, OOo etc.....

Don't you have an idea how to solve the problem. Please mind that i am absolute newbie. Thank you very much!

---

### Post by paciugo on 2006-01-08
I had the same problem a couple of days ago. I solved deleting almost all the hidden files in the session (apart amarok, firefox, etc.) ans it works. I read (don't remember where) that could be a problem of the xml parser reading a corrupted file.
Bye

---

### Post by tomash_cz on 2006-01-08
Thank you for advise, just could you give me more detail steps how to proceed it since i'm a real newbie. Tks!

---

