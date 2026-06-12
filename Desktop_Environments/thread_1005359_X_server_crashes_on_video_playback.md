---
title: "X server crashes on video playback"
date: 2008-12-08
forum: Desktop Environments
---

### Post by bartman on 2008-12-08
Hi!

I have an older laptop with an X700 ATi graphics card. Over the weekend I hooked up an extrnal monitor via the analog D-SUB port and with the ATi Catalyst Control Center I set up mirroring. I noticed a problem right there and then - during video playback the video showed up fine on the external monitor while the laptop display showed a black hole.

The problem I'm experiencing now is that when I try to play any video at all, the X server crashes immediately nad shows the login prompt again. It's the same as inserting an Ctrl+Alt+Backspace event.

This happens on all my media players - totem-gstreamer, totem-xine, vlc, mplayer. The video only works if I start up mplayer from nautilus or the Applications menu but even then it hogs my CPU. It's unlike not having DRI because the video plyback is smooth but my CPU does get very hot under prolonged full load.

```
$ lspci -v
...
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
	Subsystem: Hewlett-Packard Company Device 0940
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at c0000000 (32-bit, prefetchable) [size=128M]
	I/O ports at 2000 [size=256]
	Memory at c8800000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at c8820000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx
...
``````
$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
...
``````
$ cat /var/log/Xorg.0.log.old
...
AUDIT: Mon Dec  8 11:58:05 2008: 29928 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=29962 )
AUDIT: Mon Dec  8 11:58:05 2008: 29928 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=29963 )
AUDIT: Mon Dec  8 11:58:05 2008: 29928 X: client 4 rejected from local host ( uid=1000 gid=1000 pid=29964 )

Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x79) [0x80c3009]
1: [0xb8030400]
2: /usr/lib/xorg/modules//amdxmm.so [0xb3666214]
3: /usr/X11R6/bin/X [0x80d7148]
4: /usr/lib/xorg/modules/extensions//libextmod.so(XvdiPutImage+0x190) [0xb7b0c830]
5: /usr/lib/xorg/modules/extensions//libextmod.so [0xb7b0ff0a]
6: /usr/lib/xorg/modules/extensions//libextmod.so(ProcXvDispatch+0x3a) [0xb7b10f3a]
7: /usr/X11R6/bin/X(Dispatch+0x34f) [0x808c89f]
8: /usr/X11R6/bin/X(main+0x47d) [0x8071d1d]
9: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7c2f685]
10: /usr/X11R6/bin/X [0x8071101]
Saw signal 11.  Server aborting.
(II) Logitech USB-PS/2 Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) PS/2 Generic Mouse: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) AIGLX: Suspending AIGLX clients for VT switch
```

Any ideas what's happening here?

Thanks!

---

### Post by bartman on 2008-12-14
Well I  guess my suspicions were correct - something got botched in my configuration.

Purging and the installing xorg-driver-fglrx helped solve the situation where my 3D apps weren't working.

But the video playback issue is still there.

---

### Post by bartman on 2008-12-15
After spending some quality time with [[COLOR="Blue"]xorg.conf[/COLOR]](http://ubuntuforums.org/showthread.php?t=849422) and aticonfig I've managed to resolved the show stopping behaviour.

But now I get strange corruption with all windows (see attachment). It happens as soon as the content is scrolled or the window is dragged (or moved with Alt+F7). The corrupted window is redrawn as soon as I focus on another application.

* Oh, the joys of fglrx are here again!* ](*,)

---

### Post by bartman on 2009-01-29
Good news, everyone!

Well I got fed up with the radeon driver not supporting OpenGL so I reinstalled. What a smooth experience since my /home is on a separate partition.

And I see that the radeon OSS driver even supports OpenGL so i don't even need fglrx! Great! The performance is ~25% lower than fglrx but I really don't care.

Thanks for reading! :P

---

