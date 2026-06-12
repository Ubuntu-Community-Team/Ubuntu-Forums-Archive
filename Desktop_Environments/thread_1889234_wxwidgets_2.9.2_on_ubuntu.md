---
title: "wxwidgets 2.9.2 on ubuntu"
date: 2011-12-01
forum: Desktop Environments
---

### Post by aishsarathy on 2011-12-01
Hi,

I use wxwidgets 2.9.2 version to develop my application on Ubuntu 11.04 .
My application crahses with the following debug report .

Program received signal SIGABRT, Aborted.
[Switching to Thread 0xb6aefb70 (LWP 24267)]
0x0012e416 in __kernel_vsyscall ()
(gdb) bt
#0  0x0012e416 in __kernel_vsyscall ()
#1  0x016dfe71 in raise () from /lib/i386-linux-gnu/libc.so.6
#2  0x016e334e in abort () from /lib/i386-linux-gnu/libc.so.6
#3  0x016a8d1d in unwind_cleanup () from /lib/i386-linux-gnu/libpthread.so.0
#4  0x01695d9d in _Unwind_DeleteException () from /lib/i386-linux-gnu/libgcc_s.so.1
#5  0x0163fe8d in __cxa_end_catch () from /usr/lib/i386-linux-gnu/libstdc++.so.6
#6  0x007b1625 in wxAppConsoleBase::OnUnhandledException() () from /usr/local/lib/libwx_baseu-2.9.so.2
#7  0x009b68ed in wxThreadInternal::PthreadStart(wxThread*) () from /usr/local/lib/libwx_baseu-2.9.so.2
#8  0x016a1e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#9  0x0178573e in clone () from /lib/i386-linux-gnu/libc.so.6

Can someone help suggest a way out ?

---

### Post by deonis on 2011-12-01
It does appear like a bug but I am not sure that it's related to wxWidgets. Perhaps where is something wrong with wxGtk your are using ?  I might be wrong ...

---

### Post by aishsarathy on 2011-12-01
Bug with?

---

