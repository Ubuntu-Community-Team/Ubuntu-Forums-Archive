---
title: "render errors"
date: 2004-11-30
forum: Gaming &amp; Leisure
---

### Post by humina on 2004-11-30
I posted this in the discussion for another ATI problem.  I decided to start my own thread to see if I could get my problem solved.  Here is what I posted before:

I ran the howto [here](http://www.ubuntuforums.org/showthread.php?t=3567&highlight=ati) and when I run tuxracer I notice that it runs faster than before, but there are a bunch of random polygons everywhere. I get the same problem with tuxkart. How do I fix that? :-( 

Output of various commands:

lsmod | grep fglrx
----------------------------------
fglrx 215044 7

dmesg | grep fglrx
----------------------------------
fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] module loaded - fglrx 3.12.0 [Jul 16 2004] on minor 0
[fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[fglrx] AGP detected, AgpState = 0x1f00421b (hardware caps of chipset)
[fglrx] AGP enabled, AgpCommand = 0x1f004312 (selected caps)
[fglrx] free AGP = 54800384
[fglrx] max AGP = 54800384
[fglrx] free LFB = 116391936
[fglrx] max LFB = 116391936
[fglrx] free Inv = 0
[fglrx] max Inv = 0
[fglrx] total Inv = 0
[fglrx] total TIM = 0
[fglrx] total FB = 0
[fglrx] total AGP = 16384

fglrxinfo
---------------
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4510 (X4.3.0-3.12.0)

My fgl_glxgears command works fine and I get over 500 FPS

glxgears produces the following output and works fine:
-------------------------------------------------------------------
15212 frames in 5.0 seconds = 3042.400 FPS
15326 frames in 5.0 seconds = 3065.200 FPS
15293 frames in 5.0 seconds = 3058.600 FPS
15184 frames in 5.0 seconds = 3036.800 FPS
15248 frames in 5.0 seconds = 3049.600 FPS

---

### Post by humina on 2004-12-02
the posts on this tread helped me solve this problem:

[http://www.ubuntuforums.org/showthread.php?t=5461&highlight=ati](http://www.ubuntuforums.org/showthread.php?t=5461&highlight=ati)

I used the debs posted.  You add the line to your /etc/apt/sources.list
Then update your sorces,
Then you follow the regular instructions.  In my case I just updated my fglrx-driver.  You can use apt with the following:
sudo apt-get install fglrx-driver
or you can use the package manager.

---

