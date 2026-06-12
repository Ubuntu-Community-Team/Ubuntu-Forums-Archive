---
title: "palm sync with evolution still fails"
date: 2005-10-19
forum: Desktop Environments
---

### Post by brj on 2005-10-19
hi,

i still cannot correctly sync my palm tunsten e with evolution (it works with jpilot). sync starts but after some time the evolution-data-server crashes:

Backtrace was generated from '/usr/libexec/evolution-data-server-1.4'

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1219275072 (LWP 13229)]
[New Thread -1224139856 (LWP 13235)]
[New Thread -1223869520 (LWP 13230)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in ?? ()
#0  0xffffe410 in ?? ()
#1  0x00000001 in ?? ()
#2  0x00000000 in ?? ()
#3  0xbf9f4880 in ?? ()
#4  0xb768956b in waitpid () from /lib/tls/i686/cmov/libc.so.6
#5  0xb76333d9 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7633751 in system () from /lib/tls/i686/cmov/libc.so.6
#7  0x0804b520 in server_logging_register_domain ()
#8  <signal handler called>
#9  0xb7d1b261 in pvl_head () from /usr/lib/libecal-1.2.so.3
#10 0xb7d08ca9 in icalcomponent_as_ical_string ()
   from /usr/lib/libecal-1.2.so.3
#11 0xb7d08cbf in icalcomponent_as_ical_string ()
   from /usr/lib/libecal-1.2.so.3
#12 0xb7132190 in e_cal_backend_file_todos_get_type ()
   from /usr/lib/evolution-data-server-1.2/extensions/libecalbackendfile.so
#13 0xb7790750 in g_child_watch_add () from /usr/lib/libglib-2.0.so.0
#14 0xb778e4ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#15 0xb77914f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#16 0xb77917e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#17 0xb790a590 in bonobo_main () from /usr/lib/libbonobo-2.so.0
#18 0x0804bb37 in main ()

Thread 3 (Thread -1223869520 (LWP 13230)):
#0  0xffffe410 in ?? ()
No symbol table info available.
#1  0xb70d3378 in ?? ()
No symbol table info available.
#2  0xffffffff in ?? ()
No symbol table info available.
#3  0x00000009 in ?? ()
No symbol table info available.
#4  0xb76bd0f4 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb7791348 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb77917e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb788b37e in link_thread_io_context () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#8  0xb77aa8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb75f1361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#10 0xb76c6bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 2 (Thread -1224139856 (LWP 13235)):
#0  0xffffe410 in ?? ()
No symbol table info available.
#1  0xb7090f58 in ?? ()
No symbol table info available.
#2  0x00000002 in ?? ()
No symbol table info available.
#3  0x00000000 in ?? ()
No symbol table info available.
#4  0xb75f62ce in __lll_mutex_lock_wait ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb75f2fdb in _L_mutex_lock_33 () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#6  0xb7090f58 in ?? ()
No symbol table info available.
#7  0xb778279b in g_hash_table_remove () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb76d3ade in pthread_mutex_lock () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#9  0xb7132343 in e_cal_backend_file_todos_get_type ()
   from /usr/lib/evolution-data-server-1.2/extensions/libecalbackendfile.so
No symbol table info available.
#10 0xb7135443 in e_cal_backend_file_get_type ()
   from /usr/lib/evolution-data-server-1.2/extensions/libecalbackendfile.so
No symbol table info available.
#11 0xb7d5f560 in e_cal_backend_sync_remove_object ()
   from /usr/lib/libedata-cal-1.2.so.1
No symbol table info available.
#12 0xb7d5f631 in e_cal_backend_sync_remove_object ()
   from /usr/lib/libedata-cal-1.2.so.1
No symbol table info available.
#13 0xb7d5a452 in e_cal_backend_remove_object ()
   from /usr/lib/libedata-cal-1.2.so.1
No symbol table info available.
#14 0xb7d609d3 in e_data_cal_get_type () from /usr/lib/libedata-cal-1.2.so.1
No symbol table info available.
#15 0xb7d54471 in _ORBIT_skel_small_GNOME_Evolution_Calendar_Cal_removeObject
    () from /usr/lib/libedata-cal-1.2.so.1
No symbol table info available.
#16 0xb7882260 in ORBit_POA_setup_root () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#17 0xb7886c4e in ORBit_OAObject_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#18 0xb7873ceb in ORBit_small_invoke_adaptor () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#19 0xb788257c in ORBit_POAObject_post_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#20 0xb7882c1b in ORBit_POAObject_post_invoke () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#21 0xb786e5f9 in giop_thread_queue_process () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#22 0xb786e69a in giop_thread_queue_process () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#23 0xb77ac5a2 in g_thread_pool_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#24 0xb77aa8c4 in g_static_private_free () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#25 0xb75f1361 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#26 0xb76c6bde in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1219275072 (LWP 13229)):
#0  0xffffe410 in ?? ()
No symbol table info available.
#1  0x00000001 in ?? ()
No symbol table info available.
#2  0x00000000 in ?? ()
No symbol table info available.
#3  0xbf9f4880 in ?? ()
No symbol table info available.
#4  0xb768956b in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#5  0xb76333d9 in strtold_l () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7633751 in system () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0x0804b520 in server_logging_register_domain ()
No symbol table info available.
#8  <signal handler called>
No symbol table info available.
#9  0xb7d1b261 in pvl_head () from /usr/lib/libecal-1.2.so.3
No symbol table info available.
#10 0xb7d08ca9 in icalcomponent_as_ical_string ()
   from /usr/lib/libecal-1.2.so.3
No symbol table info available.
#11 0xb7d08cbf in icalcomponent_as_ical_string ()
   from /usr/lib/libecal-1.2.so.3
No symbol table info available.
#12 0xb7132190 in e_cal_backend_file_todos_get_type ()
   from /usr/lib/evolution-data-server-1.2/extensions/libecalbackendfile.so
No symbol table info available.
#13 0xb7790750 in g_child_watch_add () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb778e4ee in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#15 0xb77914f6 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#16 0xb77917e3 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#17 0xb790a590 in bonobo_main () from /usr/lib/libbonobo-2.so.0
No symbol table info available.
#18 0x0804bb37 in main ()
No symbol table info available.
#0  0xffffe410 in ?? ()

jakob

---

### Post by manicka on 2005-10-19
How have you configured gpilot?

---

### Post by brj on 2005-10-20
[QUOTE=manicka]How have you configured gpilot?[/QUOTE]

hi,

afaik the config is ok. 
all contacts and some entries in the calendar are actually synchronized, but suddenly it breaks.

i remember a thread about problems with special appointments (over midnight ?). but i have no clue which entry causes the problem.


jakob

---

### Post by fdimmling on 2005-11-16
Exactly the same here with my Tungsten E. Sometimes it works without problems but mostly the evolution-data-server crashes.
I tried jpilot but nothinmg happened at all. I put the correct dev /dev/ttyUSB1 in the rc file. As long as the pilot applet was present it seemed to be responding and everything got stuck with respect to pilot and applet and jpilot. When I removed the applet and rebootet nothing seemed to happen at all.

Friedrich

---

