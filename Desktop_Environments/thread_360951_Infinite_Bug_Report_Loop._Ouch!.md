---
title: "Infinite Bug Report Loop. Ouch!"
date: 2007-02-13
forum: Desktop Environments
---

### Post by Redeyes_Gambit on 2007-02-13
}{i,
 
I seem to have encountered a rather vicious little hiccup in Ubuntu and would appreciate any help I can get. When I start up Ubuntu, apparently gnome-panel crashes which brings up bug buddy. I review the report and close bug buddy only to have the whole thing crash again. This goes on and on until I finally hit ctrl+alt+F1, log in to the text terminal and type "sudo reboot." I run Beryl and the last things I was doing before all this started was:

1. Installed cursor selector (not real name. Can't remember what it's called exactly. It's in synaptic and I have used it before without issue) and was getting ready to change the cursor.

2. Set gdesklets to start up auto-magically by adding "gdesklets start" to the session autostarting apps.

3. installed ntfs 3g

My bug report is as follows (it may not be formatted correctly since I'm opening it in windows notepad :P )
 
>  Memory status: size: 58179584 vsize: 0 resident: 58179584 share: 0 rss: 17453056 rss_rlim: 0
 CPU usage: start_time: 1171412995 rtime: 0 utime: 109 stime: 0 cutime:101 cstime: 0 timeout: 8 it_real_value: 0 frequency: 0
 
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
 [New Thread -1225689424 (LWP 5136)]
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
 (no debugging symbols found)
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
 #1  0xb75ce323 in __waitpid_nocancel ()
    from /lib/tls/i686/cmov/libpthread.so.0
 #2  0xb7ec61b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
 #3  <signal handler called>
 #4  0xffffe410 in __kernel_vsyscall ()
 #5  0xb74b6770 in raise () from /lib/tls/i686/cmov/libc.so.6
 #6  0xb74b7ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
 #7  0xb76d2122 in g_logv () from /usr/lib/libglib-2.0.so.0
 #8  0xb76d2159 in g_log () from /usr/lib/libglib-2.0.so.0
 #9  0xb76d21d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
 #10 0xb7b21d5d in gtk_recent_info_get_short_name ()
    from /usr/lib/libgtk-x11-2.0.so.0
 #11 0xb7b21dba in gtk_recent_info_get_display_name ()
    from /usr/lib/libgtk-x11-2.0.so.0
 #12 0xb7b1d591 in gtk_recent_chooser_menu_new ()
    from /usr/lib/libgtk-x11-2.0.so.0
 #13 0xb76c7aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
 #14 0xb76c9802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
 #15 0xb76cc7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
 #16 0xb76ccb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
 #17 0xb7acb574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
 #18 0x08061d8c in main ()
 
 Thread 1 (Thread -1225689424 (LWP 5136)):
 #0  0xffffe410 in __kernel_vsyscall ()
 No symbol table info available.
 #1  0xb75ce323 in __waitpid_nocancel ()
    from /lib/tls/i686/cmov/libpthread.so.0
 No symbol table info available.
 #2  0xb7ec61b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
 No symbol table info available.
 #3  <signal handler called>
 No symbol table info available.
 #4  0xffffe410 in __kernel_vsyscall ()
 No symbol table info available.
 #5  0xb74b6770 in raise () from /lib/tls/i686/cmov/libc.so.6
 No symbol table info available.
 #6  0xb74b7ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
 No symbol table info available.
 #7  0xb76d2122 in g_logv () from /usr/lib/libglib-2.0.so.0
 No symbol table info available.
 #8  0xb76d2159 in g_log () from /usr/lib/libglib-2.0.so.0
 No symbol table info available.
 #9  0xb76d21d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
 No symbol table info available.
 #10 0xb7b21d5d in gtk_recent_info_get_short_name ()
    from /usr/lib/libgtk-x11-2.0.so.0
 No symbol table info available.
 #11 0xb7b21dba in gtk_recent_info_get_display_name ()
    from /usr/lib/libgtk-x11-2.0.so.0
 No symbol table info available.
 #12 0xb7b1d591 in gtk_recent_chooser_menu_new ()
    from /usr/lib/libgtk-x11-2.0.so.0
 No symbol table info available.
 #13 0xb76c7aa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
 No symbol table info available.
 #14 0xb76c9802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
 No symbol table info available.
 #15 0xb76cc7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
 No symbol table info available.
 #16 0xb76ccb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
 No symbol table info available.
 #17 0xb7acb574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
 No symbol table info available.
 #18 0x08061d8c in main ()
 No symbol table info available.
 #0  0xffffe410 in __kernel_vsyscall ()
 
 
 Any ideas?

---

### Post by Sord_Fish on 2007-02-13
this just happened to me followed  [**this link **]("http://www.ubuntuforums.org/showthread.php?t=301633&highlight=loop") and im all better. :D

---

### Post by Redeyes_Gambit on 2007-02-14
ALRIGHT! I'm back in business. Writing from Ubuntu as we speak.. err, I mean, type... 

Many thanks to you Sord_Fish!

Any idea what causes this? The other people who were encountering this issue were talking about mounting .iso files. I wasn't. Very odd indeed.

---

