---
title: "XFCE4.4 starts up, gives error report and nothin happens..."
date: 2007-01-31
forum: Desktop Environments
---

### Post by aggie333 on 2007-01-31
hi guys,
  i recently installed XFCE4.4 on ubuntu edgy...the thing is when is log into XFCE, i get this bug buddy error report

Memory status: size: 60227584 vsize: 0 resident: 60227584 share: 0 rss: 9687040 rss_rlim: 0
CPU usage: start_time: 1170003362 rtime: 0 utime: 24 stime: 0 cutime:21 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/evolution-alarm-notify'

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
[Thread debugging using libthread_db enabled]
[New Thread -1232947536 (LWP 6335)]
[New Thread -1234211936 (LWP 6351)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb72b56cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7dd91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7250770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7251ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7422122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb7422159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805d500 in main ()

Thread 2 (Thread -1234211936 (LWP 6351)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72ea803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb741c813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb741cb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb79b67e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb743738f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb705e504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb72f451e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1232947536 (LWP 6335)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b56cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7dd91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7250770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7251ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7422122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7422159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805d500 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

and after that nothing happens...i just have a blue screen...i can logout using alt+f4 though...
i did see some other thread about the same problem but it was not solved.....somebody pleaaaaaaaaaaaaaaase help me.....im sort of feelin weird after havin gotten used to XFCE...

---

### Post by kaman on 2007-02-24
I got the same problem.

---

