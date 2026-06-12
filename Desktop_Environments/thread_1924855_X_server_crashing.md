---
title: "X server crashing"
date: 2012-02-13
forum: Desktop Environments
---

### Post by kamelie1706 on 2012-02-13
Hi,

My X server crashes and I am not able to reproduce with ab specifc application and I can not guess which action cause this.
I have tried both unity & unity2D but same instability.

This is the error message I could find in /var/log/Xorg.0.log (complete version attached)
[B]Backtrace:
[  2411.396] 0: /usr/bin/X (xorg_backtrace+0x37) [0x80a66f7]
[  2411.396] 1: /usr/bin/X (0x8048000+0x62b3a) [0x80aab3a]
[  2411.396] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb785c40c]
[  2411.396] 3: (vdso) (__kernel_vsyscall+0x10) [0xb785c424]
[  2411.396] 4: /lib/i386-linux-gnu/libc.so.6 (__select+0x2d) [0xb75cbe9d]
[  2411.396] 5: /usr/bin/X (WaitForSomething+0x18c) [0x80a3f8c]
[  2411.397] 6: /usr/bin/X (0x8048000+0x29ed2) [0x8071ed2]
[  2411.397] 7: /usr/bin/X (0x8048000+0x1c70c) [0x806470c]
[  2411.397] 8: /lib/i386-linux-gnu/libc.so.6 (__libc_start_main+0xf3) [0xb751a113]
[  2411.397] 9: /usr/bin/X (0x8048000+0x1ca21) [0x8064a21]
[  2411.397] 
Caught signal 3 (Quit). Server aborting

Would it help if use another desktop or should I try proprietary ATI drivers?

I do not care about fancy desktop effect but I just want a stable graphic environment!
[/B]

---

### Post by hildenbrandsteven on 2012-02-13
You can't reproduce the crash, but how often is this happening?

---

### Post by kamelie1706 on 2012-02-13
Typically at least once in 2h desktop activity.

I have just run memory test but everything is fine there.

---

