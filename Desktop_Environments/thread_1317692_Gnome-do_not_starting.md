---
title: "Gnome-do not starting"
date: 2009-11-06
forum: Desktop Environments
---

### Post by humphreybc on 2009-11-06
Gnome-do doesn't want to start after a series of updates today. I tried purging it and reinstalling with aptitude but still no go.

Here's the error message that gets spat out when I try to run it from terminal:

```

benjamin@benjamin-laptop:~$ gnome-do

** (/usr/lib/gnome-do/Do.exe:4325): CRITICAL **: _wapi_shm_file_open: shared file [/home/benjamin/.wapi/shared_data-benjamin-laptop-Linux-x86_64-328-12-0] open error: Input/output error

** (/usr/lib/gnome-do/Do.exe:4325): CRITICAL **: _wapi_shm_attach: shared file [/home/benjamin/.wapi/shared_data-benjamin-laptop-Linux-x86_64-328-12-0] open error
**
ERROR:shared.c:349:shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/gnome-do/Do.exe:4325): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/gnome-do/Do.exe:4325): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	/usr/bin/cli [0x47a5ef]
	/lib/libpthread.so.0 [0x7f21d75df190]
	/lib/libc.so.6(gsignal+0x35) [0x7f21d70104b5]
	/lib/libc.so.6(abort+0x180) [0x7f21d7013f50]
	/lib/libglib-2.0.so.0(g_assertion_message+0x120) [0x7f21d7c59540]
	/lib/libglib-2.0.so.0 [0x7f21d7c59ab0]
	/usr/bin/cli [0x56a310]
	/usr/bin/cli [0x557be6]
	/usr/bin/cli(mono_once+0x64) [0x5653e4]
	/usr/bin/cli [0x557b53]
	/usr/bin/cli [0x5692c5]
	/usr/bin/cli [0x506dfe]
	/usr/bin/cli(mono_runtime_init+0x25) [0x50e9b5]
	/usr/bin/cli [0x419133]
	/usr/bin/cli(mono_main+0x417) [0x461f97]
	/lib/libc.so.6(__libc_start_main+0xfd) [0x7f21d6ffbabd]
	/usr/bin/cli [0x416e19]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
0x00007f21d75de090 in __read_nocancel () from /lib/libpthread.so.0
* 1 Thread 0x7f21d82be730 (LWP 4325)  0x00007f21d75de090 in __read_nocancel ()
   from /lib/libpthread.so.0

Thread 1 (Thread 0x7f21d82be730 (LWP 4325)):
#0  0x00007f21d75de090 in __read_nocancel () from /lib/libpthread.so.0
#1  0x000000000047a764 in ?? ()
#2  <signal handler called>
#3  0x00007f21d70104b5 in raise () from /lib/libc.so.6
#4  0x00007f21d7013f50 in abort () from /lib/libc.so.6
#5  0x00007f21d7c59540 in g_assertion_message () from /lib/libglib-2.0.so.0
#6  0x00007f21d7c59ab0 in g_assertion_message_expr ()
   from /lib/libglib-2.0.so.0
#7  0x000000000056a310 in ?? ()
#8  0x0000000000557be6 in ?? ()
#9  0x00000000005653e4 in mono_once ()
#10 0x0000000000557b53 in ?? ()
#11 0x00000000005692c5 in ?? ()
#12 0x0000000000506dfe in ?? ()
#13 0x000000000050e9b5 in mono_runtime_init ()
#14 0x0000000000419133 in ?? ()
#15 0x0000000000461f97 in mono_main ()
#16 0x00007f21d6ffbabd in __libc_start_main () from /lib/libc.so.6
#17 0x0000000000416e19 in ?? ()
#18 0x00007fff6c5b35e8 in ?? ()
#19 0x000000000000001c in ?? ()
#20 0x0000000000000002 in ?? ()
#21 0x00007fff6c5b467f in ?? ()
#22 0x00007fff6c5b468c in ?? ()
#23 0x0000000000000000 in ?? ()

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

Advice?

---

