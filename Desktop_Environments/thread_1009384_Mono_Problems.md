---
title: "Mono Problems"
date: 2008-12-12
forum: Desktop Environments
---

### Post by Asheboy on 2008-12-12
Mono seems to have gone random on my system. When I run banshee it doesn't start and when I run it in a terminal it spits out:

```

** (/usr/lib/banshee-1/Banshee.exe:10736): CRITICAL **: _wapi_shm_file_open: shared file [/home/asheboy/.wapi/shared_data-Asheboy-Linux-i686-312-11-0] write error: No space left on device

** (/usr/lib/banshee-1/Banshee.exe:10736): CRITICAL **: _wapi_shm_attach: shared file [/home/asheboy/.wapi/shared_data-Asheboy-Linux-i686-312-11-0] open error
**
** ERROR:(shared.c:346):shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/banshee-1/Banshee.exe:10736): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/banshee-1/Banshee.exe:10736): WARNING **: Thread (nil) may have been prematurely finalized

** (/usr/lib/banshee-1/Banshee.exe:10736): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	banshee-1 [0x816b1fa]
	[0xb7f07440]
	/lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7ccaa01]
	/usr/lib/libglib-2.0.so.0(g_assertion_message+0x121) [0xb7e8a651]
	/usr/lib/libglib-2.0.so.0 [0xb7e8abad]
	banshee-1 [0x811703e]
	banshee-1 [0x8109342]
	banshee-1(mono_once+0x96) [0x8112726]
	banshee-1 [0x810907c]
	banshee-1 [0x8115f6e]
	banshee-1 [0x8116364]
	banshee-1 [0x80d1877]
	banshee-1(mono_runtime_init+0x26) [0x80d8836]
	banshee-1 [0x8134535]
	banshee-1(mono_main+0x3aa) [0x805a9da]
	banshee-1 [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cb4450]
	banshee-1 [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c756d0 (LWP 10736)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f07410 in __kernel_vsyscall ()
  1 Thread 0xb7c756d0 (LWP 10736)  0xb7f07410 in __kernel_vsyscall ()

Thread 1 (Thread 0xb7c756d0 (LWP 10736)):
#0  0xb7f07410 in __kernel_vsyscall ()
#1  0xb7e1e973 in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e9b25d in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7e9b6af in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7e9c0ad in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7e9c56c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0816b295 in ?? ()
#7  <signal handler called>
#8  0xb7f07410 in __kernel_vsyscall ()
#9  0xb7cc9085 in raise () from /lib/tls/i686/cmov/libc.so.6
#10 0xb7ccaa01 in abort () from /lib/tls/i686/cmov/libc.so.6
#11 0xb7e8a651 in g_assertion_message () from /usr/lib/libglib-2.0.so.0
#12 0xb7e8abad in g_assertion_message_expr () from /usr/lib/libglib-2.0.so.0
#13 0x0811703e in ?? ()
#14 0x08109342 in ?? ()
#15 0x08112726 in mono_once ()
#16 0x0810907c in ?? ()
#17 0x08115f6e in ?? ()
#18 0x08116364 in ?? ()
#19 0x080d1877 in ?? ()
#20 0x080d8836 in mono_runtime_init ()
#21 0x08134535 in ?? ()
#22 0x0805a9da in mono_main ()
#23 0x0805a122 in ?? ()
#24 0xb7cb4450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#25 0x0805a091 in ?? ()
#0  0xb7f07410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

I've tried reinstall Mono and that doesn't work, any ideas?

---

### Post by directhex on 2008-12-12
rm -r ~/.wapi

---

### Post by xile_ on 2010-12-29
> **directhex said:**
> rm -r ~/.wapi

Why would this help?
Either way, this folder isnt present in my installation.

My best guess it that this error has something to do with mono - but not sure what or how to fix it.

---

### Post by directhex on 2010-12-29
> **xile_ said:**
> Why would this help?
Either way, this folder isnt present in my installation.

My best guess it that this error has something to do with mono - but not sure what or how to fix it.

ls -hl /dev/shm

---

### Post by xile_ on 2010-12-30
> **directhex said:**
> ls -hl /dev/shm

~$ ls -hl /dev/shm/
totalt 696K
-rw-r----- 1 user user 4,0K 2010-12-30 08:08 mono.2181
-rw-r----- 1 user user  79K 2010-12-30 08:08 mono-shared-1002-shared_data-kth-Linux-i686-312-12-0
-rw-r----- 1 user user 3,6M 2010-12-30 08:08 mono-shared-1002-shared_fileshare-kth-Linux-i686-36-12-0
-r-------- 1 gdm gdm  65M 2010-12-30 08:05 pulse-shm-1644970933
-r-------- 1 user user  65M 2010-12-30 08:09 pulse-shm-1838087076
-r-------- 1 user user  65M 2010-12-30 08:07 pulse-shm-3951475214
-r-------- 1 user user  65M 2010-12-30 08:06 pulse-shm-4215343826
-r-------- 1 user user  65M 2010-12-30 08:09 pulse-shm-508357370


Then what? :-)

---

### Post by directhex on 2010-12-30
> **xile_ said:**
> Then what? :-)

Have you tinkered with the size of /dev/shm, e.g. limited it to 512M?

---

### Post by xile_ on 2010-12-30
> **directhex said:**
> Have you tinkered with the size of /dev/shm, e.g. limited it to 512M?

I have not made any changes to it in any way.
Banshee was working - I closed it down for approx 5min, reopened it and initiated playback, it plays roughly one second of the file, and then crashes.

I have to admit I no idea what /dev/shm is used for.

---

### Post by directhex on 2010-12-30
> **xile_ said:**
> I have not made any changes to it in any way.
Banshee was working - I closed it down for approx 5min, reopened it and initiated playback, it plays roughly one second of the file, and then crashes.

I have to admit I no idea what /dev/shm is used for.

You've rebooted the system?

---

### Post by xile_ on 2010-12-30
> **directhex said:**
> You've rebooted the system?

Yes, the system has beek rebooted several times - with no change in behavior.

---

