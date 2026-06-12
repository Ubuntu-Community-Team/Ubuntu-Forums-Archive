---
title: "System -&gt; Administration Tools Quit Unexpectedly"
date: 2006-07-29
forum: Desktop Environments
---

### Post by wong3000 on 2006-07-29
Greetings to all experienced and newbies alike. I am a newbie in Linux OS as I have just switched from Windows XP platform to Ubuntu 6.06.

What bugs me in this OS is the Administration tools. Whenever I try to click most, almost all utilities  end with the "-admin" will end up in error stating that the application "**xxx-admin has quit unexpectedly**". Restarting the program will pop up the same error message. the "Inform Developers" option brought me to the debug details as follows:

Backtrace was generated from '/usr/bin/network-admin'

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
[Thread debugging using libthread_db enabled]
[New Thread -1224395072 (LWP 5886)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7406463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ecd8e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb72f49a1 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb72f62b9 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb768c006 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb768c03a in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805c35e in ?? ()
#10 0x00000000 in ?? ()

Thread 1 (Thread -1224395072 (LWP 5886)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7406463 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ecd8e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb72f49a1 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb72f62b9 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb768c006 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb768c03a in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805c35e in ?? ()
No symbol table info available.
#10 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


Thus, I plead for anyone to help me in this problem. What can I do to solve this? HELP!!:confused: :(

---

### Post by wong3000 on 2006-07-29
Can anyone help? PLS........
I can't create a new user account and configure the networks because of the errors....
Can anyone suggest a formula to reinstall the missing parts that cause the error? What application should I look into in the Synaptic Package Manager to reinstall the Administration package?:confused: :sad:

---

