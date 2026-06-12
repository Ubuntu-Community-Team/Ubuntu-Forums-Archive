---
title: "X crashing at least once a day for the past couple of days"
date: 2010-03-24
forum: Desktop Environments
---

### Post by agent8131 on 2010-03-24
On my next reboot I'll do a memtest to try and isolate if it's a hardware issue.  However, the problem seemed to start after some package updates a couple of weeks ago.  This has become a real problem as I've been losing work whenever this happens.  I figured I'd see if anyone could help with the backtrace.

```
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f00c6]
1: /usr/bin/X(xf86SigHandler+0x41) [0x4852c1]
2: /lib/libc.so.6 [0x7f02d4784530]
3: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv001646X+0x26) [0x7f02d19cb85$
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv001415X+0x64) [0x7f02d19dfe0$
5: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f02d1c6d904]
6: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f02d1c8374d]
7: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f02d1c8691e]
8: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f02d1c86e9c]
9: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f02d1c8743f]
10: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f02d1c4a358]
11: /usr/bin/X [0x535205]
12: /usr/bin/X [0x4ffb96]
13: /usr/bin/X(BlockHandler+0x50) [0x452200]
14: /usr/bin/X(WaitForSomething+0x141) [0x4edbf1]
15: /usr/bin/X(Dispatch+0xb2) [0x44de92]
16: /usr/bin/X(main+0x3b5) [0x434085]
17: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f02d476fabd]
18: /usr/bin/X [0x433509]
Saw signal 11.  Server aborting.
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) BTC USB Multimedia Keyboard: Close
(II) UnloadModule: "evdev"
(II) BTC USB Multimedia Keyboard: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech USB-PS/2 Optical Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log

```

---

