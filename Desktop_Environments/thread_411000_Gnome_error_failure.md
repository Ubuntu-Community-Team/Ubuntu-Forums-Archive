---
title: "Gnome error failure"
date: 2007-04-16
forum: Desktop Environments
---

### Post by cprophecy on 2007-04-16
When i login to gnome as my primary login part of the top and bottom taskbar comes up, and then an error message pops up.

```
Memory status: size: 33021952 vsize: 0 resident: 33021952 share: 0 rss: 13922304 rss_rlim: 0
CPU usage: start_time: 1176707912 rtime: 0 utime: 69 stime: 0 cutime:62 cstime: 0 timeout: 7 it_real_value: 0 frequency: 0

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
[New Thread -1225431376 (LWP 5688)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb760c323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f051b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb74f5770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb74f6ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7711122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7711159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0xb77111d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#10 0xb7b60d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b60dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7b5c591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#13 0xb7706aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#14 0xb7708802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb770b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb770bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb7b0a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x08061d8c in main ()

Thread 1 (Thread -1225431376 (LWP 5688)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb760c323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f051b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb74f5770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb74f6ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7711122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7711159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb77111d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb7b60d5d in gtk_recent_info_get_short_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b60dba in gtk_recent_info_get_display_name ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7b5c591 in gtk_recent_chooser_menu_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0xb7706aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7708802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb770b7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb770bb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb7b0a574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0x08061d8c in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

After i press save or close on the bug reporting tool, the same error message just keeps popping up, and does not allow me to access anything in gnome. I can quickly press ALT-F2 to run a command but then i cant type the command in, another error window just pops up. I'm not really sure how to resolve this. I had to create a testuser account to login and make gnome available. I tried renaming .gnome and .gnome2 to backup directories, did not fix anything. Could someone help resolve this error? thanks

---

### Post by Zyphrexi on 2007-04-16
have you made any major changes to your system lately?

---

### Post by cprophecy on 2007-04-16
no. i was only trying to access a .iso file when i first saw the error. then the system kinda froze up  so i rebooted. ubuntu had a few updates that needed to restart the computer to complete.

---

### Post by honeyjr on 2007-04-17
Hope I am answering this correctly, please bear with me it is my very first post on the forum. 
I had the same problem today and found this solution. It worked for me and I am back in gnome.  :D 

[http://64.233.167.104/search?q=cache:dDB9fzhjA_IJ:ubuntuforums.org/showthread.php%3Fp%3D2391618+gnome+panel+bug+buddy+error+delete+recently&hl=en&ct=clnk&cd=1](http://64.233.167.104/search?q=cache:dDB9fzhjA_IJ:ubuntuforums.org/showthread.php%3Fp%3D2391618+gnome+panel+bug+buddy+error+delete+recently&hl=en&ct=clnk&cd=1)

Quote:
Originally Posted by KJS View Post
solution
delete the
recently-used.xbel
file found in your home directory

---

