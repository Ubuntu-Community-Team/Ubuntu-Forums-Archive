---
title: "Problem to load GNOME panel"
date: 2007-04-22
forum: Desktop Environments
---

### Post by Bodomity on 2007-04-22
Hello.

After restart I have mail from Bug Buddy with this:


Memory status: size: 39600128 vsize: 0 resident: 39600128 share: 0 rss: 14049280 rss_rlim: 0
CPU usage: start_time: 1177262662 rtime: 0 utime: 169 stime: 0 cutime:156 cstime: 0 timeout: 13 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb763a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f321b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7522770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7523ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb773e122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb773e159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb773e1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b8dd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b8ddba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b89591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7733aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7735802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77387df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb7738b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b37574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225247056 (LWP 6284)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb763a323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f321b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7522770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7523ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb773e122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb773e159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb773e1d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b8dd5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b8ddba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b89591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7733aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7735802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77387df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb7738b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b37574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


I really dont know what happens, I dont install any untrust programs.. I just create 64px panel, could it be problem? Anyway, How to make defaults in GNOME panel, couse I dont like KDE pretty well.

Thanks.

---

### Post by Flare183 on 2007-04-22
I had the same problem on edgy on gnome. It really made me :-x. But since i started over and went to KDE. I haven't had such a problem thank god!:)   Thank you god for watching over me!.

I also think that it has something to do with either Beryl or Compiz. But I'm not sure.

---

