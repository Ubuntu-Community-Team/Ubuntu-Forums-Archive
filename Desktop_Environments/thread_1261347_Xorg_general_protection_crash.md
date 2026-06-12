---
title: "Xorg general protection crash"
date: 2009-09-08
forum: Desktop Environments
---

### Post by dargaud on 2009-09-08
For the last 3 (?) days, I've had several crash of X while I was using the PC. Needless to say, it's pretty annoying, even with the session app relaunch.
Looked in the logs:
```
2009-09-08 22:06:07	penguin	kernel	[84287.940957] Xorg[4285] general protection ip:7f836b7ad186 sp:7fff793eee10 error:0 in nvidia_drv.so[7f836b74a000+39a000]
2009-09-08 22:06:08	penguin	kdm[4243]	X server for display :0 terminated unexpectedly

uname -a
Linux penguin 2.6.28-15-generic #51-Ubuntu SMP Mon Aug 31 13:39:06 UTC 2009 x86_64 GNU/Linux

```

No recent updates. The only thing I've been doing different recently is using x11vnc to access that PC remotely, but it wasn't launched when the crashes occurred.

---

### Post by krunge on 2009-09-08
Maybe check /var/log/Xorg.0 (or more likely /var/log/Xorg.0.old) for more messages.

---

### Post by dargaud on 2009-09-09
I'm not sure what to look for, but here's what I found at the end of xorg.0.old
```
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/bin/X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7f836ef20040]
3: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f836ba6284b]
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f836ba6521f]
5: /usr/bin/X [0x53a291]
6: /usr/bin/X [0x535df5]
7: /usr/bin/X(Dispatch+0x364) [0x44e304]
8: /usr/bin/X(main+0x3bd) [0x433d8d]
9: /lib/libc.so.6(__libc_start_main+0xe6) [0x7f836ef0b5a6]
10: /usr/bin/X [0x433219]
Saw signal 11.  Server aborting.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) Logitech G9 Laser Mouse: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) Logitech G9 Laser Mouse: Close
(II) UnloadModule: "evdev"

```

---

### Post by krunge on 2009-09-09
> **dargaud said:**
> I'm not sure what to look for, but here's what I found at the end of xorg.0.old
```
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f1b66]
1: /usr/bin/X(xf86SigHandler+0x41) [0x485a61]
2: /lib/libc.so.6 [0x7f836ef20040]
3: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f836ba6284b]
4: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f836ba6521f]

```
Well, a backtrace like that is very good place to start troubleshooting. I'd start googling for some of the terms in it.

BTW, signal 11 indicates segmentation violation, which should not happen (i.e. it could be a bug in the Xorg server, nvidia_drv, etc.)

OTOH, you can get sig11's with bad RAM or other failing hardware.

---

### Post by dargaud on 2009-09-10
In /var/log/kdm.log I also found the following, but I'm not sure if it's related as there's no date stamp.
```
Backtrace:
*** glibc detected *** /usr/bin/X: corrupted double-linked list: 0x0000000002528
c90 ***
======= Backtrace: =========
/lib/libc.so.6[0x7fb35cb14a8e]
/lib/libc.so.6[0x7fb35cb168f1]
/lib/libc.so.6(__libc_malloc+0x98)[0x7fb35cb18828]
/lib/libc.so.6(__backtrace_symbols+0x10f)[0x7fb35cb9781f]
/usr/bin/X(xorg_backtrace+0x33)[0x4f1b73]
/usr/bin/X(xf86SigHandler+0x41)[0x485a61]
/lib/libc.so.6[0x7fb35cacf040]
/usr/lib/xorg/modules/drivers//nvidia_drv.so(_nv001522X+0x16)[0x7fb35935c186]
/usr/lib/xorg/modules/drivers//nvidia_drv.so[0x7fb3596160c1]
/usr/lib/xorg/modules/drivers//nvidia_drv.so[0x7fb359616137]
/usr/lib/xorg/modules/drivers//nvidia_drv.so[0x7fb35961ed90]
/usr/lib/xorg/modules/drivers//nvidia_drv.so[0x7fb3595cfcf3]
/usr/lib/xorg/modules/drivers//nvidia_drv.so[0x7fb3595d0002]
/usr/lib/xorg/modules/drivers//nvidia_drv.so[0x7fb3595b968a]
/usr/bin/X[0x506ad9]
/usr/bin/X[0x536d53]
/usr/bin/X(main+0x44c)[0x433e1c]
/lib/libc.so.6(__libc_start_main+0xe6)[0x7fb35caba5a6]
/usr/bin/X[0x433219]
======= Memory map: ========
...

```
As for the corrupted memory, it's a possibility. One of my (new) chips had some hiccups in MemTest86, but I then selected mem parameters that let it run smoothly for 24 hours.

---

### Post by krunge on 2009-09-10
> **dargaud said:**
> In /var/log/kdm.log I also found the following, but I'm not sure if it's related as there's no date stamp.

It appears to be a similar backtrace.  Did you try googling for terms that are in it?
> 
As for the corrupted memory, it's a possibility. One of my (new) chips had some hiccups in MemTest86, but I then selected mem parameters that let it run smoothly for 24 hours.
Try a burnin test, e.g. building the Linux kernel in a loop. There should be no failures even for 100's of kernel compiles.  [http://www.bitwizard.nl/sig11/](http://www.bitwizard.nl/sig11/)

---

### Post by krazyd on 2009-09-10
If memtest doesn't show errors in 24 hours, it's unlikely to be a RAM problem. from the logs it looks like buggy nvidia drivers.

try upgrading to newer drivers from nvidia website / nvnews.

---

### Post by ugmoe2000 on 2009-11-02
I get the same errors on a IBM T61 Thinkpad in both 64bit Jaunty & 64bit Karmic... I seem to get these errors more frequently running 64bit than 32 but I've also received them running 32bit Jaunty.  Here's the tail of my GDM log file from 64bit Karmic   


Backtrace: 0: /usr/bin/X(xorg_backtrace+0x26) [0x4f00c6]
  1: /usr/bin/X(xf86SigHandler+0x41) [0x4852c1]
  2: /lib/libc.so.6 [0x7f5315ddf530]
  3: /usr/lib/xorg/modules/drivers//nvidia_drv.so [0x7f5312fdd157]
  4: /usr/bin/X [0x5388db]
  5: /usr/lib/xorg/modules/extensions//libdbe.so [0x7f5313a8b495]
  6: /usr/bin/X(compPositionWindow+0x72) [0x501002]
  7: /usr/bin/X(miSlideAndSizeWindow+0x1b2) [0x4e8012]
  8: /usr/bin/X(compResizeWindow+0xb6) [0x500de6]
  9: /usr/bin/X(ConfigureWindow+0xa7f) [0x43a7df]
  10: /usr/bin/X(ProcConfigureWindow+0x87) [0x44d7d7]
  11: /usr/bin/X(Dispatch+0x394) [0x44e174]
  12: /usr/bin/X(main+0x3b5) [0x434085]
  13: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f5315dcaabd]
  14: /usr/bin/X [0x433509]
  Saw signal 11.  Server aborting. 

It seems to be almost identical across the different versions of ubuntu. I get this error with all versions of the nvidia drivers (180.xx, 185.xx and now even 190.42) I have a feeling it's just buggy drivers... but I don't have the know-how to test for it.

---

### Post by delbyblue on 2009-11-10
I have got the same problem, but error is on file ld-2.10.1.so.
How can i know what is it? Any solution?

---

### Post by delbyblue on 2009-11-13
I have changed my nVidia driver to an older version (from 185 to 173) and things seems go well now. Maybe just a buggy driver...

---

### Post by steevc on 2009-11-16
I'm also getting X server crashes. In my case it always seems to crash when multiple users are logged in. One of them will do something like click on something in Firefox and the display jumps back to the log-in screen and we will find that a different user's session has crashed. For some reason it seems to be mainly my sessions that crash, perhaps it has something to do with me being last to log in, but I'm not sure that's always the case.

This only started happening after I upgraded from 9.04 to 9.10.

I'm using nvidia 185.18.36. Should I try an older version? How do I downgrade?

Apart from that the system seems stable, so I don't think it could be a memory problem. Mind you, it sounds like one of my fans is on the way out. I need to check that some time.

Just found a possible Launchpad bug for this 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/473049](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/473049)

---

