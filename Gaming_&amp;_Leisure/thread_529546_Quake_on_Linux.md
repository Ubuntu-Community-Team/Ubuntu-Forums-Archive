---
title: "Quake on Linux"
date: 2007-08-19
forum: Gaming &amp; Leisure
---

### Post by darkhacker902 on 2007-08-19
I have the Original Quake for windows, when i try and open it with Wine in ubuntu, I get the loading screen, but at the bottom in my taskbar it says joequake error. and it never loads :(

How do I install it properly?

---

### Post by jrusso2 on 2007-08-19
Instead of running the Original Quake in WINE, its better to  run it natively in Linux.

I have never run the original quake I can't find the CD but Quake 2 runs quite well in Linux.

Here is a How To on running it natively.

[http://www.yolinux.com/HOWTO/Quake-HOWTO.html](http://www.yolinux.com/HOWTO/Quake-HOWTO.html)

---

### Post by darkhacker902 on 2007-08-19
Alright well since i heard about running it natively, I just did sudo aptitude install quake2

and its installed


but when I run it....I get this:


```
***** WARNING *****

   The networking part of Quake II (especially the server part) contains
   several unfixed security issues. Therefore, Quake II should not be
   used over untrusted networks (like the internet). The version
   included in Debian is intended only for local play.   

   See for an possibly non-exhaustive list of issues:
   http://archives.neohapsis.com/archives/bugtraq/2004-10/0299.html
   http://www.r1ch.net/stuff/r1q2/
   http://bugs.debian.org/280573

*******************

Do you understand the security implications of continuing?
y
QuakeIIForge 0.3
using /home/ryan/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
/dev/dsp: No such file or directory
SNDDMA_Init: Could not open /dev/dsp.
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
recursive shutdown
Error: Couldn't load pics/colormap.pcx
```

---

### Post by jrusso2 on 2007-08-19
Do you have the quake 2 CD cause there is a folder you need to copy.

---

### Post by darkhacker902 on 2007-08-19
I have quake 1 in a folder on my desktop.

---

### Post by cjl2301 on 2007-08-19
Check out post #7 on this thread:

[http://ubuntuforums.org/showthread.php?t=311391&highlight=quake](http://ubuntuforums.org/showthread.php?t=311391&highlight=quake)

It will tell you how to get quake running using the Darkplaces engine.  It's very easy to setup (I just did myself) and I think you will be quite pleased with the results - I know I was.

---

