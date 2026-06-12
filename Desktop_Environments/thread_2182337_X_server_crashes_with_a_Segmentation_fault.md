---
title: "X server crashes with a Segmentation fault"
date: 2013-10-20
forum: Desktop Environments
---

### Post by fRLHCJy on 2013-10-20
On my Ubuntu 13.04 system, most X clients are causing xorg to die with a segmentation fault.  Here are the relevant lines from /var/log/Xorg.0.log :



 [ 12417.131] (EE) 
 [ 12417.131] (EE) Backtrace:
 [ 12417.131] (EE) 0: X (xorg_backtrace+0x49) [0xb7714f49]
 [ 12417.131] (EE) 1: X (0xb7567000+0x1b1e86) [0xb7718e86]
 [ 12417.132] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb754440c]
 [ 12417.132] (EE) 3: /lib/i386-linux-gnu/libc.so.6 (0xb7147000+0x7fed6) [0xb71c6ed6]
 [ 12417.132] (EE) 4: ?? [0xb91d8f50]
 [ 12417.132] (EE) 
 [ 12417.132] (EE) Segmentation fault at address 0x0
 [ 12417.132] 
 Fatal server error:
 [ 12417.132] Caught signal 11 (Segmentation fault). Server aborting
 [ 12417.132] 
 [ 12417.132] (EE) 
 Please consult the The X.Org Foundation support 
          at [http://wiki.x.org](http://wiki.x.org)
  for help. 
 [ 12417.133] (EE) Please also check the log file at "/var/log/Xorg.0.log" for  additional information.
 [ 12417.133] (EE)



Interestingly, xterm does not cause xorg to crash, so xinit works, but a window
manager -- even a simple one like twm -- will cause xorg to crash.  Even xclock
causes xorg to crash.  So far xterm and xmessage are the only x clients I have
found that don't crash the server, but I only tested a few.

Thank you in advance for any and all replies.

---

### Post by fRLHCJy on 2013-10-20
On my Ubuntu 13.04 system, most X clients are causing xorg to die with a segmentation fault.  Here are the relevant lines from /var/log/Xorg.0.log :



 [ 12417.131] (EE) 
 [ 12417.131] (EE) Backtrace:
 [ 12417.131] (EE) 0: X (xorg_backtrace+0x49) [0xb7714f49]
 [ 12417.131] (EE) 1: X (0xb7567000+0x1b1e86) [0xb7718e86]
 [ 12417.132] (EE) 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xb754440c]
 [ 12417.132] (EE) 3: /lib/i386-linux-gnu/libc.so.6 (0xb7147000+0x7fed6) [0xb71c6ed6]
 [ 12417.132] (EE) 4: ?? [0xb91d8f50]
 [ 12417.132] (EE) 
 [ 12417.132] (EE) Segmentation fault at address 0x0
 [ 12417.132] 
 Fatal server error:
 [ 12417.132] Caught signal 11 (Segmentation fault). Server aborting
 [ 12417.132] 
 [ 12417.132] (EE) 
 Please consult the The X.Org Foundation support 
          at [http://wiki.x.org](http://wiki.x.org)
  for help. 
 [ 12417.133] (EE) Please also check the log file at "/var/log/Xorg.0.log" for  additional information.
 [ 12417.133] (EE)



Interestingly, xterm does not cause xorg to crash, so xinit works, but a window
manager -- even a simple one like twm -- will cause xorg to crash.  Even xclock
causes xorg to crash.  So far xterm and xmessage are the only x clients I have
found that don't crash the server, but I only tested a few.

Thank you in advance for any and all replies.

---

### Post by tgalati4 on 2013-10-21
Are you running 32-bit or 64-bit Ubuntu?  This statement looks like a mismatch:   /lib**/i386-linux-gnu/**libc.so.6

What is the graphics card?  Is this in a virtual machine or a standard, bare-metal installation?

---

### Post by Toz on 2013-10-21
*Merged duplicate threads.*

---

