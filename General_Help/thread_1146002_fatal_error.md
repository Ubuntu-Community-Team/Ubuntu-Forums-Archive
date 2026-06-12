---
title: "fatal error"
date: 2009-05-02
forum: General Help
---

### Post by javanar on 2009-05-02
i am running ubuntu 8.10 using a 64 bit processor. My computer's screen suddenly becomes black. In the log messages I found this :


Fatal server error:
lockup
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) Logitech USB Receiver: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x65) [0x480f45]
1: /lib/libc.so.6 [0x7f227b7f50a0]
2: /usr/lib/xorg/modules/extensions//libdri.so(DRILock+0xab) [0x7f227a68799b]
3: /usr/lib/xorg/modules/drivers//intel_drv.so [0x7f227a213747]
4: /usr/X11R6/bin/X(AbortDDX+0x8d) [0x4681ed]
5: /usr/X11R6/bin/X(AbortServer+0x18) [0x4f82d8]
6: /usr/X11R6/bin/X(FatalError+0xd5) [0x4f89a5]
7: /usr/lib/xorg/modules/drivers//intel_drv.so(I830WaitLpRing+0x1f1) [0x7f227a208771]
8: /usr/lib/xorg/modules/drivers//intel_drv.so(I830Sync+0x1d3) [0x7f227a208b73]
9: /usr/lib/xorg/modules//libexa.so(exaWaitSync+0x5c) [0x7f2279749f6c]
10: /usr/lib/xorg/modules//libexa.so(ExaDoPrepareAccess+0x91) [0x7f227974b121]
11: /usr/lib/xorg/modules//libexa.so(ExaCheckPutImage+0x165) [0x7f2279752aa5]
12: /usr/lib/xorg/modules//libexa.so [0x7f227974c452]
13: /usr/X11R6/bin/X [0x533a6f]
14: /usr/X11R6/bin/X(ProcPutImage+0x157) [0x44a6b7]
15: /usr/X11R6/bin/X(Dispatch+0x364) [0x44d6e4]
16: /usr/X11R6/bin/X(main+0x45d) [0x4336fd]
17: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f227b7e0466]
18: /usr/X11R6/bin/X [0x432ad9]
Saw signal 11. Server aborting.
(II) AIGLX: Suspending AIGLX clients for VT switch




Can anybody help me pls to understand and overcome the problem? Thx.

---

### Post by sahabcse on 2009-05-02
I think it looks like some sort of error with your xserver configuration.


You should try reconfiguring it.

---

