---
title: "Desktop crashes frequently"
date: 2010-05-26
forum: Desktop Environments
---

### Post by dr_gap on 2010-05-26
Kubuntu 10.04, Thinkpad T41, Radeon Mobility 7500 graphics

"frequently" = once a day.

Without warning, my desktop disappears, leaving behind for a tiny fraction of a second some text characters on a black screen.  It took me a while to figure out what the text is: it's the last thing the OS normally prints before the login prompt when booting into a terminal session.  Nothing unusual, no errors.

I'm bounced back to the graphical login screen, and I can log back in and everything seems normal, but all unsaved work is lost.  It doesn't crash all the way back to a reboot.

AFAICT Apport does not record the crash.  I've appended the end of Xorg.0.log.old and it looks like there might be an error recorded there.

I have the dreaded Radeon Mobility 7500 graphics adapter, and I always suspect it when I have UI problems. (I have a custom xorg.conf to fix some other problems.)

any clues?  Anything I can do to further debug?  Should I ask over at KDE?  File a bug report?

Thanks, 
gary



-----------------------------------------------------

(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(II) Macintosh mouse button emulation: initialized for relative axes.
(II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse0)
(II) No input driver/identifier specified (ignoring)
(II) XKB: reuse xkmfile /var/lib/xkb/server-8DD95E60B8F2D3E5FE848929A26D769396ED53C1.xkm
(II) XKB: reuse xkmfile /var/lib/xkb/server-244408F757B051FD612C870C3E49152B1B4C355C.xkm

Backtrace:
0: /usr/bin/X (xorg_backtrace+0x3b) [0x80e937b]
1: /usr/bin/X (0x8048000+0x61c7d) [0x80a9c7d]
2: (vdso) (__kernel_rt_sigreturn+0x0) [0x388410]
3: /usr/lib/xorg/modules/drivers/radeon_drv.so (0x601000+0xb2039) [0x6b3039]
4: /usr/lib/xorg/modules/libexa.so (0x373000+0x9490) [0x37c490]
5: /usr/lib/xorg/modules/libexa.so (0x373000+0x9558) [0x37c558]
6: /usr/bin/X (miCopyRegion+0x21b) [0x819cadb]
7: /usr/bin/X (miDoCopy+0x44d) [0x819cffd]
8: /usr/lib/xorg/modules/libexa.so (0x373000+0x7a4a) [0x37aa4a]
9: /usr/bin/X (0x8048000+0xda9c3) [0x81229c3]
10: /usr/bin/X (0x8048000+0x28df5) [0x8070df5]
11: /usr/bin/X (0x8048000+0x2a477) [0x8072477]
12: /usr/bin/X (0x8048000+0x1ed7a) [0x8066d7a]
13: /lib/tls/i686/cmov/libc.so.6 (__libc_start_main+0xe6) [0x1a2bd6]
14: /usr/bin/X (0x8048000+0x1e961) [0x8066961]
Segmentation fault at address (nil)

Caught signal 11 (Segmentation fault). Server aborting

Please consult the The X.Org Foundation support 
         at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) TPPS/2 IBM TrackPoint: Close
(II) UnloadModule: "evdev"
(II) ThinkPad Extra Buttons: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
 ddxSigGiveUp: Closing log

---

### Post by dr_gap on 2010-06-16
One of my python apps consistently generates this crash, so I'm now able to cause it at will.  I have an strace of a crash.

What should I do to debug this?  Would filing a bug report be the way to go?  Can someone suggest how to make sense out of the strace log? Post it here? Any pointers?  Etc?

thanks,
gary

---

