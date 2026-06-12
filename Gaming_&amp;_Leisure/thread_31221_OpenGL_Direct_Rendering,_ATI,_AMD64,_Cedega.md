---
title: "OpenGL Direct Rendering, ATI, AMD64, Cedega"
date: 2005-05-02
forum: Gaming &amp; Leisure
---

### Post by macmorning on 2005-05-02
Hi all

First, thanks for all the answers I have already found by browsing these forums  \\:D/ 
I am now blocked on opengl, don't know if it's a driver, architecture or Cedega issue.
My opengl seems to work properly on X, I get a descent score in fglrx-gears (~3200 in 24 bit, 1280x1024, standard window size). Quake3 runs like a charm (haven't got the framerate here though).

But Cedega's Point2Play tells me that my "opengl direct rendering" is "not available", with low performances  :? 


```
macmorning@Bart:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

macmorning@Bart:~$ uname -a
Linux Bart 2.6.10-5-amd64-generic #1 Tue Apr 5 12:21:57 UTC 2005 x86_64 GNU/Linux

macmorning@Bart:~$ glxinfo | grep rendering
**direct rendering: Yes**

macmorning@Bart:~$ glxgears
14389 frames in 5.0 seconds = 2877.800 FPS
16093 frames in 5.0 seconds = 3218.600 FPS
16098 frames in 5.0 seconds = 3219.600 FPS
16067 frames in 5.0 seconds = 3213.400 FPS

macmorning@Bart:~$ locate libGL
/usr/lib/libGL.so.1
/usr/lib/libGL.so.1.2
/usr/lib/libGLU.so.1
/usr/lib/libGLU.so.1.3
/usr/X11R6/lib/libGL.so.1.2
/usr/X11R6/lib/libGL.so.1
/usr/X11R6/lib/libGLU.so.1.3
/usr/X11R6/lib/libGLU.so.1
/usr/X11R6/lib/modules/extensions/libGLcore.a
/usr/X11R6/lib32/libGL.so.1.2
/usr/X11R6/lib32/libGLU.so.1.3
/usr/X11R6/lib32/libGL.so.1
/usr/X11R6/lib32/libGLU.so.1
/usr/lib32/libGL.so.1
/usr/lib32/libGL.so.1.2
/usr/lib32/libGLU.so.1
/usr/lib32/libGLU.so.1.3 
```

I have read in the Cedega howto that the Mesa driver which is supposed to be found in /usr/X11R6/lib/ can cause some problems in some cases and that I shouldn't try to to remove them unless I have some problems with some games.
But I also read somewhere that ATI drivers (fglrx ?) are using part of the Mesa driver.
Can I try to remove them ? How do I do that, just put a sym link from /usr/X11R6/lib/libGL.so.1.2 to /usr/lib/libGL.so.1.2 etc ?
I will try that tonight when I get home.

Any help would be very appreciated  :smile:

---

### Post by macmorning on 2005-05-04
For some reasons Cedega was using the wrong libs.

```
export LIBGL_DRIVERS_DIR=/usr/X11R6/lib32/modules/dri
export LD_LIBRARY_PATH=/usr/lib32:$LD_LIBRARY_PATH:.
cedega -winver win98 WoW.exe -opengl
```

And voilà

---

