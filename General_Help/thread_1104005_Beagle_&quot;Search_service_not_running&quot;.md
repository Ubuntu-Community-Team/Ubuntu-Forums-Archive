---
title: "Beagle: &quot;Search service not running&quot;"
date: 2009-03-23
forum: General Help
---

### Post by Mka on 2009-03-23
I have beagled enabled via gnome-session-properties but when I press F12 and search something I get "Search service not nunning" message and a button I should click to "Start seach service". This happens everytime. 

I ran **beagled --fg** on Terminal and there after I ran beable-search. The beagled program quited with this message: 

Always: Starting Beagle Daemon (version 0.3.8)
Always: Running on Mono 1.9.1
Always: Command Line: /usr/lib/beagle/BeagleDaemon.exe --fg
Warn: Extended attributes are not supported on this filesystem. Performance will suffer as a result.
Warn: GMail account information not set. Search is disabled.
Warn: Caught exception in DoTaskReal
        Tag: Konqueror History Crawler
    Creator: 
Description: 
   Priority: Delayed (0)
System.IO.IOException: Attempt to watch /var/tmp/kdecache-mkanyicy/http/c failed: Permission denied
  at Beagle.Util.Inotify.CreateOrModifyWatch (Beagle.Util.WatchInfo watched) [0x00000] 
  at Beagle.Util.Inotify.Subscribe (System.String path, Beagle.Util.InotifyCallback callback, EventType mask, EventType initial_filter) [0x00000] 
  at Beagle.Util.Inotify.Subscribe (System.String path, Beagle.Util.InotifyCallback callback, EventType mask) [0x00000] 
  at Beagle.Daemon.KonqQueryable.KonqQueryable.HasNextIndexable () [0x00000] 
  at Beagle.Daemon.LuceneQueryable+AddGeneratorTask.DoTaskReal () [0x00000] 
  at Beagle.Util.Scheduler+Task.DoTask () [0x00000] 
Stacktrace:


Native stacktrace:

	beagled [0x817b4ae]
	beagled [0x807f78b]
	[0xb7f7d410]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7ca06d0 (LWP 9621)]
[New Thread 0xb49ceb90 (LWP 9695)]
[New Thread 0xb4e12b90 (LWP 9691)]
[New Thread 0xb4d0db90 (LWP 9649)]
[New Thread 0xb4f27b90 (LWP 9634)]
[New Thread 0xb5028b90 (LWP 9633)]
[New Thread 0xb5129b90 (LWP 9632)]
[New Thread 0xb6519b90 (LWP 9625)]
[New Thread 0xb6628b90 (LWP 9624)]
[New Thread 0xb7360b90 (LWP 9623)]
[New Thread 0xb78f9b90 (LWP 9622)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f7d430 in __kernel_vsyscall ()
  11 Thread 0xb78f9b90 (LWP 9622)  0xb7f7d430 in __kernel_vsyscall ()
  10 Thread 0xb7360b90 (LWP 9623)  0xb7f7d430 in __kernel_vsyscall ()
  9 Thread 0xb6628b90 (LWP 9624)  0xb7f7d430 in __kernel_vsyscall ()
  8 Thread 0xb6519b90 (LWP 9625)  0xb7f7d430 in __kernel_vsyscall ()
  7 Thread 0xb5129b90 (LWP 9632)  0xb7f7d430 in __kernel_vsyscall ()
  6 Thread 0xb5028b90 (LWP 9633)  0xb7f7d430 in __kernel_vsyscall ()
  5 Thread 0xb4f27b90 (LWP 9634)  0xb7f7d430 in __kernel_vsyscall ()
  4 Thread 0xb4d0db90 (LWP 9649)  0xb7f7d430 in __kernel_vsyscall ()
  3 Thread 0xb4e12b90 (LWP 9691)  0xb7f7d430 in __kernel_vsyscall ()
  2 Thread 0xb49ceb90 (LWP 9695)  0xb7f7d430 in __kernel_vsyscall ()
  1 Thread 0xb7ca06d0 (LWP 9621)  0xb7f7d430 in __kernel_vsyscall ()

Thread 11 (Thread 0xb78f9b90 (LWP 9622)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7e65906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xb7360b90 (LWP 9623)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7e62075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xb6628b90 (LWP 9624)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7daddf1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb6693917 in Mono_Unix_UnixSignal_WaitAny ()
   from /usr/lib/libMonoPosixHelper.so
#3  0xb6640b65 in ?? ()
#4  0xb6640a30 in ?? ()
#5  0xb66407ae in ?? ()
#6  0xb66ab6c9 in ?? ()
#7  0x08098c55 in mono_runtime_delegate_invoke ()
#8  0x080d5fdf in ?? ()
#9  0x081279de in ?? ()
#10 0x0813ff75 in ?? ()
#11 0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb6519b90 (LWP 9625)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7e65328 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08124909 in ?? ()
#3  0x080ddb1b in ?? ()
#4  0xb6646b4a in ?? ()
#5  0xb6646967 in ?? ()
#6  0xb66468a2 in ?? ()
#7  0xb664680d in ?? ()
#8  0xb66467bf in ?? ()
#9  0xb664620e in ?? ()
#10 0xb664610e in ?? ()
#11 0xb6644dca in ?? ()
#12 0xb66ab6c9 in ?? ()
#13 0x08098c55 in mono_runtime_delegate_invoke ()
#14 0x080d5fdf in ?? ()
#15 0x081279de in ?? ()
#16 0x0813ff75 in ?? ()
#17 0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb5129b90 (LWP 9632)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7daddf1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ee79ab in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7ee7d5c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0817b565 in ?? ()
#5  0x0807f78b in ?? ()
#6  <signal handler called>
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 6 (Thread 0xb5028b90 (LWP 9633)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7dab167 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb78edfdd in inotify_snarf_events () from /usr/lib/beagle/libbeagleglue.so
#3  0xb4e1302f in ?? ()
#4  0xb51a27b4 in ?? ()
#5  0xb6644dca in ?? ()
#6  0xb66ab6c9 in ?? ()
#7  0x08098c55 in mono_runtime_delegate_invoke ()
#8  0x080d5fdf in ?? ()
#9  0x081279de in ?? ()
#10 0x0813ff75 in ?? ()
#11 0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#12 0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb4f27b90 (LWP 9634)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7e623a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d1821 in ?? ()
#7  0xb51a2742 in ?? ()
#8  0xb51a3726 in ?? ()
#9  0xb51a3146 in ?? ()
#10 0xb6644dca in ?? ()
#11 0xb66ab6c9 in ?? ()
#12 0x08098c55 in mono_runtime_delegate_invoke ()
#13 0x080d5fdf in ?? ()
#14 0x081279de in ?? ()
#15 0x0813ff75 in ?? ()
#16 0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb4d0db90 (LWP 9649)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7db61d6 in epoll_wait () from /lib/tls/i686/cmov/libc.so.6
#2  0x080d8a02 in ?? ()
#3  0x080d5f74 in ?? ()
#4  0x081279de in ?? ()
#5  0x0813ff75 in ?? ()
#6  0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb4e12b90 (LWP 9691)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7e623a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d92fd in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb49ceb90 (LWP 9695)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7e623a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d92fd in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e5e50f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7db5a0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7ca06d0 (LWP 9621)):
#0  0xb7f7d430 in __kernel_vsyscall ()
#1  0xb7dab167 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eb1c52 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7eb22e2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb6641109 in ?? ()
#5  0xb66410ce in ?? ()
#6  0xb78fb132 in ?? ()
#7  0xb78fa485 in ?? ()
#8  0xb78fa1c3 in ?? ()
#9  0x0809cb76 in mono_runtime_exec_main ()
#10 0x0809d19b in mono_runtime_run_main ()
#11 0x0805af2e in mono_main ()
#12 0x0805a432 in ?? ()
#13 0xb7cea685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#14 0x0805a371 in ?? ()
#0  0xb7f7d430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

What should I do get my beagle back on track? I am using Intrepid.

---

### Post by directhex on 2009-03-23
File a bug - looks like Beagle doesn't cope with permission issues

---

