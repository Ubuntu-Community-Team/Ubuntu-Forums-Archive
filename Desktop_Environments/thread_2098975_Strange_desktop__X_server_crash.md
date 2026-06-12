---
title: "Strange desktop / X server crash"
date: 2012-12-28
forum: Desktop Environments
---

### Post by Gannin on 2012-12-28
I'm using Lubuntu 12.04 with an AMD card and AMD's fglrx drivers.

Recently, I've started experiencing a strange crash.  Sometimes when I open a new window, the new window will display for a second then the desktop will crash back to the login screen.  This didn't used to happen, but lately it's been happening about once or twice per day.

The only information I could glean from the logs is this:

Backtrace:
[ 46711.402] 0: /usr/bin/X (xorg_backtrace+0x26) [0x7fe2f3940876]
[ 46711.403] 1: /usr/bin/X (0x7fe2f37b8000+0x18c71a) [0x7fe2f394471a]
[ 46711.403] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7fe2f2ac8000+0xfcb0) [0x7fe2f2ad7cb0]
[ 46711.403] 3: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7fe2f2840000+0x72e68) [0x7fe2f28b2e68]
[ 46711.403] 4: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x7fe2f2840000+0x731eb) [0x7fe2f28b31eb]
[ 46711.403] 5: /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (pixman_blt+0x52) [0x7fe2f2849602]
[ 46711.403] 6: /usr/lib/xorg/modules/libfb.so (fbCopyNtoN+0x2e9) [0x7fe2ee832e29]
[ 46711.403] 7: /usr/lib/xorg/modules/glesx.so (0x7fe2ec8e0000+0x7702d) [0x7fe2ec95702d]
[ 46711.403] 8: /usr/lib/xorg/modules/glesx.so (0x7fe2ec8e0000+0x79136) [0x7fe2ec959136]
[ 46711.403] 9: /usr/bin/X (0x7fe2f37b8000+0x116454) [0x7fe2f38ce454]
[ 46711.403] 10: /usr/bin/X (0x7fe2f37b8000+0xd9c5d) [0x7fe2f3891c5d]
[ 46711.403] 11: /usr/bin/X (0x7fe2f37b8000+0xdb112) [0x7fe2f3893112]
[ 46711.403] 12: /usr/bin/X (0x7fe2f37b8000+0xd7eb2) [0x7fe2f388feb2]
[ 46711.403] 13: /usr/bin/X (ConfigureWindow+0x244) [0x7fe2f3831194]
[ 46711.403] 14: /usr/bin/X (0x7fe2f37b8000+0x4930b) [0x7fe2f380130b]
[ 46711.403] 15: /usr/bin/X (0x7fe2f37b8000+0x4e8a1) [0x7fe2f38068a1]
[ 46711.403] 16: /usr/bin/X (0x7fe2f37b8000+0x3d7ba) [0x7fe2f37f57ba]
[ 46711.403] 17: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xed) [0x7fe2f194976d]
[ 46711.404] 18: /usr/bin/X (0x7fe2f37b8000+0x3daad) [0x7fe2f37f5aad]
[ 46711.404] Segmentation fault at address 0x7fe2e263b000
[ 46711.404] 
Caught signal 11 (Segmentation fault). Server aborting
[ 46711.404] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[ 46711.404] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 46711.404] 
[ 46711.472] (II) evdev: Power Button: Close
[ 46711.472] (II) UnloadModule: "evdev"
[ 46711.472] (II) Unloading evdev
[ 46711.480] (II) evdev: Power Button: Close
[ 46711.480] (II) UnloadModule: "evdev"
[ 46711.480] (II) Unloading evdev
[ 46711.485] (II) evdev: Logitech USB Optical Mouse: Close
[ 46711.485] (II) UnloadModule: "evdev"
[ 46711.485] (II) Unloading evdev
[ 46711.488] (II) evdev: AT Translated Set 2 keyboard: Close
[ 46711.488] (II) UnloadModule: "evdev"
[ 46711.488] (II) Unloading evdev
[ 46711.489] (II) AIGLX: Suspending AIGLX clients for VT switch
[ 46711.492] (II) fglrx(0): Backup framebuffer data.
[ 46711.541] (II) fglrx(0): Backup complete.
[ 46711.998]  ddxSigGiveUp: Closing log
[ 46711.998] Server terminated with error (1). Closing log file.

Any ideas?

---

### Post by christopherbalz on 2013-06-06
I have the same issue: It only happens with Gnu Emacs, VirtualBox, and a few other programs such as Skype: [http://ubuntuforums.org/showthread.php?t=2151848&p=12679547#post12679547](http://ubuntuforums.org/showthread.php?t=2151848&p=12679547#post12679547)

---

