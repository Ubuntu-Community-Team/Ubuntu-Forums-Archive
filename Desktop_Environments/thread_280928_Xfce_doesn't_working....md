---
title: "Xfce doesn't working..."
date: 2006-10-20
forum: Desktop Environments
---

### Post by goldup on 2006-10-20
I've got ubuntu 6.10 and I installed xfce by 'apt-get install xubuntu-desktop' All was ok, but one time xfce crashed, so I removed it and installed again, and ./config folder too. Its still crashing. :confused:

---

### Post by taurus on 2006-10-20
It crashes right after you log in; it crashes while you surf the web; it crashes while you do nothing!!!  Can you be a little more specific instead of it just crashes?

But if you want to use XFce4, then try installing the Xubuntu version...

---

### Post by goldup on 2006-10-20
Just after log in. I can see only blue desktop and nothing else.

---

### Post by goldup on 2006-10-21
Here is a bug report:

```

Memory status: size: 51826688 vsize: 0 resident: 51826688 share: 0 rss: 9695232 rss_rlim: 0
CPU usage: start_time: 1161375872 rtime: 0 utime: 20 stime: 0 cutime:16 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

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
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
[New Thread -1233250640 (LWP 9818)]
[New Thread -1234531424 (LWP 9841)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb72686cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d8b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7203770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7204ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb73d5122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb73d5159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805d500 in main ()

Thread 2 (Thread -1234531424 (LWP 9841)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb729d803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb73cf813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb73cfb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb79697e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb73ea38f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7012504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb72a751e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1233250640 (LWP 9818)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72686cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7d8b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7203770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7204ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb73d5122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb73d5159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805d500 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


```

---

