---
title: "cedega, video problems"
date: 2006-08-05
forum: Desktop Environments
---

### Post by pr0-t31n on 2006-08-05
I have installed cedega and installed couter-strike but when i run it its really really choppy... Cedega tells me I fail the direct redering and 3d acceleration test.  Thanks for your time and help in advance.

Here are some of the tests i did

sev@ubuntu:~$ glxinfo | grep 'direct rendering'
direct rendering: No
sev@ubuntu:~$ glxgears -iacknowledgethatthistoolisnotabenchmark
1548 frames in 5.1 seconds = 302.683 FPS
1440 frames in 5.0 seconds = 286.708 FPS
1560 frames in 5.4 seconds = 291.539 FPS
1440 frames in 5.1 seconds = 280.568 FPS
1440 frames in 5.1 seconds = 280.176 FPS
1320 frames in 5.3 seconds = 250.728 FPS
1560 frames in 5.4 seconds = 290.311 FPS
1560 frames in 5.4 seconds = 291.216 FPS
1560 frames in 5.4 seconds = 291.318 FPS
1560 frames in 5.4 seconds = 290.746 FPS
1560 frames in 5.5 seconds = 286.010 FPS
1200 frames in 5.0 seconds = 238.585 FPS
1200 frames in 5.3 seconds = 225.028 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
sev@ubuntu:~$ locate libGL
/usr/lib/i686/mmx/cmov/libGL.so.1.2
/usr/lib/i686/mmx/cmov/libGL.so.1
/usr/lib/libGLU.so.1.3.060302
/usr/lib/libGL.so.1.2
/usr/lib/libGLU.so.1
/usr/lib/libGL.so.1
/usr/X11R6/lib/modules/extensions/libGLcore.a

---

### Post by aceracer24 on 2006-08-08
you probably don't have the proprietary drivers installed, just teh standard ones that ubunto installs for you. You need to run synaptic and search for nvidia and install the glx driver. If your running ATI, I can't help you.

---

