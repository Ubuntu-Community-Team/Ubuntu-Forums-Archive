---
title: "pthread_mutex_lock problem"
date: 2008-07-01
forum: Desktop Environments
---

### Post by SoAnIs on 2008-07-01
I recently tried installing kubuntu-kde4-desktop, this didn't work (dbus issue.) Now, all my qt4 apps fail, with the following error:
lyx: pthread_mutex_lock.c:87: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.
Aborted

Backtrace of lyx:
GNU gdb 6.8-debian
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu"...
(gdb) handle SIG33 pass s[Knostop noprint
Signal        Stop	Print	Pass to program	Description
SIG33         No	No	Yes		Real-time event 33
(gdb) set pagination 0
(gdb) run lix[K[Kyx[K[K[K[K
Starting program: /usr/bin/lyx 
[Thread debugging using libthread_db enabled]
warning: Lowest section in /usr/lib/libicudata.so.38 is .hash at 0000000000000120
[New Thread 0x7fcb9b728780 (LWP 1594)]
lyx: pthread_mutex_lock.c:87: __pthread_mutex_lock: Assertion `mutex->__data.__owner == 0' failed.

Program received signal SIGABRT, Aborted.
[Switching to Thread 0x7fcb9b728780 (LWP 1594)]
0x00007fcb98966095 in raise () from /lib/libc.so.6
(gdb) backtrace uf[K[Kfull
#0  0x00007fcb98966095 in raise () from /lib/libc.so.6
No symbol table info available.
#1  0x00007fcb98967af0 in abort () from /lib/libc.so.6
No symbol table info available.
#2  0x00007fcb9895f2df in __assert_fail () from /lib/libc.so.6
No symbol table info available.
#3  0x00007fcb9a501ac7 in pthread_mutex_lock () from /lib/libpthread.so.0
No symbol table info available.
#4  0x00007fcb977db298 in g_source_attach () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0x00007fcb9ad68eee in ?? () from /usr/lib/libQtGui.so.4
No symbol table info available.
#6  0x00007fcb9ad3c39e in QApplicationPrivate::createEventDispatcher () from /usr/lib/libQtGui.so.4
No symbol table info available.
#7  0x00007fcb9a86630f in QCoreApplication::init () from /usr/lib/libQtCore.so.4
No symbol table info available.
#8  0x00007fcb9a86654f in QCoreApplication::QCoreApplication () from /usr/lib/libQtCore.so.4
No symbol table info available.
#9  0x00007fcb9acf9534 in QApplication::QApplication () from /usr/lib/libQtGui.so.4
No symbol table info available.
#10 0x00000000007bcb54 in GuiApplication (this=0x63a, argc=@0x63a, argv=0x6) at ../../../../src/frontends/qt4/GuiApplication.cpp:105
No locals.
#11 0x00000000007bd8f4 in lyx::createApplication (argc=@0x7fffa375bb9c, argv=0x7fffa375bcb8) at ../../../../src/frontends/qt4/GuiApplication.cpp:89
No locals.
#12 0x0000000000540880 in lyx::LyX::exec (this=0x7fffa375bba0, argc=@0x7fffa375bb9c, argv=0x7fffa375bcb8) at ../../src/LyX.cpp:451
	exit_status = <value optimized out>
#13 0x000000000042f4b3 in main (argc=1, argv=0x7fffa375bcb8) at ../../src/main.cpp:48
	the_lyx_instance = {<boost::noncopyable_::noncopyable> = {<No data fields>}, first_start = false, batch_command = {static npos = 18446744073709551615, _M_dataplus = {<std::allocator<char>> = {<__gnu_cxx::new_allocator<char>> = {<No data fields>}, <No data fields>}, _M_p = 0xcfc198 ""}}, pimpl_ = {ptr = 0xd83240}}
(gdb) info registers
rax            0x0	0
rbx            0x7fffa375b600	140735935788544
rcx            0xffffffffffffffff	-1
rdx            0x6	6
rsi            0x63a	1594
rdi            0x63a	1594
rbp            0x7fcb9b728780	0x7fcb9b728780
rsp            0x7fffa375b558	0x7fffa375b558
r8             0x0	0
r9             0x203d3d2072656e77	2323080192360541815
r10            0x8	8
r11            0x206	518
r12            0x7fffa375c7b6	140735935793078
r13            0x7fcb9a509535	140512444060981
r14            0x57	87
r15            0x7fcb9a509cb6	140512444062902
rip            0x7fcb98966095	0x7fcb98966095 <raise+53>
eflags         0x206	[ PF IF ]
cs             0x33	51
ss             0x2b	43
ds             0x0	0
es             0x0	0
fs             0x0	0
gs             0x0	0
fctrl          0x37f	895
fstat          0x0	0
ftag           0xffff	65535
fiseg          0x0	0
fioff          0x0	0
foseg          0x0	0
fooff          0x0	0
fop            0x0	0
mxcsr          0x1f80	[ IM DM ZM OM UM PM ]
(gdb) thread apply all backtrace

Thread 1 (Thread 0x7fcb9b728780 (LWP 1594)):
#0  0x00007fcb98966095 in raise () from /lib/libc.so.6
#1  0x00007fcb98967af0 in abort () from /lib/libc.so.6
#2  0x00007fcb9895f2df in __assert_fail () from /lib/libc.so.6
#3  0x00007fcb9a501ac7 in pthread_mutex_lock () from /lib/libpthread.so.0
#4  0x00007fcb977db298 in g_source_attach () from /usr/lib/libglib-2.0.so.0
#5  0x00007fcb9ad68eee in ?? () from /usr/lib/libQtGui.so.4
#6  0x00007fcb9ad3c39e in QApplicationPrivate::createEventDispatcher () from /usr/lib/libQtGui.so.4
#7  0x00007fcb9a86630f in QCoreApplication::init () from /usr/lib/libQtCore.so.4
#8  0x00007fcb9a86654f in QCoreApplication::QCoreApplication () from /usr/lib/libQtCore.so.4
#9  0x00007fcb9acf9534 in QApplication::QApplication () from /usr/lib/libQtGui.so.4
#10 0x00000000007bcb54 in GuiApplication (this=0x63a, argc=@0x63a, argv=0x6) at ../../../../src/frontends/qt4/GuiApplication.cpp:105
#11 0x00000000007bd8f4 in lyx::createApplication (argc=@0x7fffa375bb9c, argv=0x7fffa375bcb8) at ../../../../src/frontends/qt4/GuiApplication.cpp:89
#12 0x0000000000540880 in lyx::LyX::exec (this=0x7fffa375bba0, argc=@0x7fffa375bb9c, argv=0x7fffa375bcb8) at ../../src/LyX.cpp:451
#13 0x000000000042f4b3 in main (argc=1, argv=0x7fffa375bcb8) at ../../src/main.cpp:48
(gdb) quit
The program is running.  Exit anyway? (y or n)

---

