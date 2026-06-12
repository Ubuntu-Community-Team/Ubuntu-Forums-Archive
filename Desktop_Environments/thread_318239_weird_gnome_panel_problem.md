---
title: "weird gnome panel problem"
date: 2006-12-13
forum: Desktop Environments
---

### Post by Jacks0n on 2006-12-13
Hi, I was using a VM, and pressed ctrl+alt+delete to close a frozen windows app. anyway after a few times... the screen flickered and changed the layout of the menu's on the top panel. I'm sure it's really easy to fix, but how do you change it back? I'm guessing something in gconf-editor needs to be changed, but I have no idea what...

here's a screenshot I took
[http://i147.photobucket.com/albums/r319/jacks0_n/Screenshot.png](http://i147.photobucket.com/albums/r319/jacks0_n/Screenshot.png)


-thanks!
Jackson

---

### Post by eldepeche on 2006-12-13
If you right click on things in the panel and uncheck "Lock to panel," then right click again and choose "Move," you can manually stick everything back where it was, then re-lock it. 

Why it all shifted, I don't have a clue...

---

### Post by elysium444 on 2007-01-02
I had this bug while extracting with file roller (archive manager). this is the bug:


Memory status: size: 140648448 vsize: 140648448 resident: 21012480 share: 11104256 rss: 21012480 rss_rlim: -1
CPU usage: start_time: 1167724400 rtime: 70 utime: 63 stime: 7 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100

Backtrace was generated from '/usr/bin/gnome-panel'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread 47167592696992 (LWP 6528)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0x00002ae60c44eeb5 in waitpid () from /lib/libpthread.so.0
#0  0x00002ae60c44eeb5 in waitpid () from /lib/libpthread.so.0
#1  0x00002ae60a2dca07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
#2  <signal handler called>
#3  0x00002ae60c58847b in raise () from /lib/libc.so.6
#4  0x00002ae60c589da0 in abort () from /lib/libc.so.6
#5  0x00002ae60c0f9d70 in g_logv () from /usr/lib64/libglib-2.0.so.0
#6  0x00002ae60c0f9df3 in g_log () from /usr/lib64/libglib-2.0.so.0
#7  0x00002ae60c0f9e76 in g_assert_warning () from /usr/lib64/libglib-2.0.so.0
#8  0x00002ae60af86948 in gtk_recent_info_get_short_name ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#9  0x00002ae60af8698b in gtk_recent_info_get_display_name ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#10 0x00002ae60af82c4b in gtk_recent_chooser_menu_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#11 0x00002ae60c0f1c84 in g_main_context_dispatch ()
   from /usr/lib64/libglib-2.0.so.0
#12 0x00002ae60c0f4acd in g_main_context_check ()
   from /usr/lib64/libglib-2.0.so.0
#13 0x00002ae60c0f4dda in g_main_loop_run () from /usr/lib64/libglib-2.0.so.0
#14 0x00002ae60af375f3 in gtk_main () from /usr/lib64/libgtk-x11-2.0.so.0
#15 0x0000000000420807 in main ()

Thread 1 (Thread 47167592696992 (LWP 6528)):
#0  0x00002ae60c44eeb5 in waitpid () from /lib/libpthread.so.0
No symbol table info available.
#1  0x00002ae60a2dca07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0x00002ae60c58847b in raise () from /lib/libc.so.6
No symbol table info available.
#4  0x00002ae60c589da0 in abort () from /lib/libc.so.6
No symbol table info available.
#5  0x00002ae60c0f9d70 in g_logv () from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#6  0x00002ae60c0f9df3 in g_log () from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#7  0x00002ae60c0f9e76 in g_assert_warning () from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#8  0x00002ae60af86948 in gtk_recent_info_get_short_name ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0x00002ae60af8698b in gtk_recent_info_get_display_name ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0x00002ae60af82c4b in gtk_recent_chooser_menu_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0x00002ae60c0f1c84 in g_main_context_dispatch ()
   from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#12 0x00002ae60c0f4acd in g_main_context_check ()
   from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#13 0x00002ae60c0f4dda in g_main_loop_run () from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#14 0x00002ae60af375f3 in gtk_main () from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#15 0x0000000000420807 in main ()
No symbol table info available.
#0  0x00002ae60c44eeb5 in waitpid () from /lib/libpthread.so.0

---

