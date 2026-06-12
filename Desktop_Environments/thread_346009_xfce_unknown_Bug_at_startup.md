---
title: "xfce unknown Bug at startup?"
date: 2007-01-25
forum: Desktop Environments
---

### Post by desper on 2007-01-25
I am using Xfce, edgy.
there's always a crash report, trivial, but rather annoying.
anyone has any information? thanx!

The Bug Buddy says:

[COLOR="Navy"]The application that crashed is not known to bug-buddy, therefore the bug report can not be sent to the GNOME Bugzilla.  Please save the bug to a text file and report it to the appropriate bug tracker for this application.[/COLOR]

Detail

[COLOR="Navy"]Memory status: size: 60735488 vsize: 0 resident: 60735488 share: 0 rss: 10088448 rss_rlim: 0
CPU usage: start_time: 1169712644 rtime: 0 utime: 16 stime: 0 cutime:12 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

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
[New Thread -1233103184 (LWP 4682)]
[New Thread -1234912352 (LWP 4688)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb72906cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7db31b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb722b770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb722cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb73fd122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb73fd159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805d500 in main ()

Thread 2 (Thread -1234912352 (LWP 4688)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72c5803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb73f7813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb73f7b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb79917e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb741238f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7039504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb72cf51e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1233103184 (LWP 4682)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72906cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7db31b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb722b770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb722cef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb73fd122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb73fd159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805d500 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
[/COLOR]

---

### Post by petedragon on 2007-01-25
I had the same problem. To fix it I removed "evolution-alarm-notify" from the list of startup services in the session settings.

---

### Post by sanguinemoon on 2007-01-25
I got that problem too. "Solved" by removing Evolution,since I didn't plan on using that anyway

---

### Post by eric magray on 2007-01-27
i have that problem with 2 of my apps, how do i get rid of "evolution"?

---

### Post by conradcliff on 2007-02-03
applications/settings/autostart applications
un-check evolution

---

### Post by P235 on 2007-02-22
By unchecking evolution, can I still use evolution?  I use it a great deal for time management.

---

