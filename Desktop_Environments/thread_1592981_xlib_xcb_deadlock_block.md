---
title: "xlib xcb deadlock block"
date: 2010-10-11
forum: Desktop Environments
---

### Post by pevgeniev on 2010-10-11
Hi,
Please advise me where can I post this question, if this is not the right place.
I’ve a program developed using xlib and cairo. Just for the reference I do mix calls between cairo and xlib, although I’m not sure If that might be the cause of the error.
I get a deadlock or  a block in some situations.
I’ve three threads that work with xlib. One is the main UI thread which makes calls to both xlib and cairo, another uses it just to send a XClientMessage and third makes some xlib calls like XCopyArea and at the end send an XClientMessage (those are for some animations).
I’ve called InitThreads in the beginning of the program. I’ve also guarded all xlib calls with XLockDisplay (cairo calls are also guarded with XLockDisplay). 
I’m using ubuntu 10.10. 
The stack traces are:
(gdb) thread 1
#0  0xb77e5430 in __kernel_vsyscall ()
#1  0xb71d8ba6 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb70dcd80 in ?? () from /usr/lib/libxcb.so.1
#3  0xb70dd2eb in ?? () from /usr/lib/libxcb.so.1
#4  0xb70dd687 in xcb_writev () from /usr/lib/libxcb.so.1
#5  0xb76ed2e9 in _XSend () from /usr/lib/libX11.so.6
#6  0xb76ed900 in _XEventsQueued () from /usr/lib/libX11.so.6
#7  0xb76d6588 in XPending () from /usr/lib/libX11.so.6

(gdb) thread 6
#0  0xb77e5430 in __kernel_vsyscall ()
#1  0xb75ac829 in __lll_lock_wait () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb75a7f3b in _L_lock_752 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb75a7d51 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb76d311a in ?? () from /usr/lib/libX11.so.6
#5  0xb76d268a in XLockDisplay () from /usr/lib/libX11.so.6

(gdb) thread 7
#0  0xb77e5430 in __kernel_vsyscall ()
#1  0xb75ac829 in __lll_lock_wait () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb75a7f3b in _L_lock_752 () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb75a7d51 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb76d311a in ?? () from /usr/lib/libX11.so.6
#5  0xb76d268a in XLockDisplay () from /usr/lib/libX11.so.6

Where thread 1 is the main ui thread, currently calling XPending (it has already called XLockDisplay) in an event loop, thead 7 is the thread that just sends XClientMessage and thread 6 is the thread that has made some calls to XCopyArea and is now about to make a call to XSendMessage (it is waiting along with thread 7 for thread 1 to finish). But thread 1 never seem to return from poll.

I’m not sure it is relevant (I’m by no means an expert on linux or libc), but I’ve another thread waiting in poll (it’s a thread for TCP/IP network communication)

(gdb) thread 2
#0  0xb77e5430 in __kernel_vsyscall ()
#1  0xb71d8ba6 in poll () from /lib/tls/i686/cmov/libc.so.6

Has anyone experience similar deadlock/block? Can this be a bug in xcb and is it worth trying to compile xlib without xcb?

Thanks

---

