---
title: "xserver and console ttys simultaneously"
date: 2007-12-02
forum: Desktop Environments
---

### Post by mvastola on 2007-12-02
I'm trying to configure a gusty box as a playback device for video for a school tv station.  The plan is to use custom database scripts to operate mplayer (in slave mode) and use xserver to output video through an nVidia graphics card with TV Out.  Additionally, there's an on-board graphics card that's just hooked up to the console monitor.

It's a pretty intricate setup, but everything seems to work great, with the slight problem that when I start Xserver (with *X :1 -layout "TV-Out"*) to start outputting video, it implicitly renders me unable to use the local computer at all..

Running that command switches over the virtual console to xwindows, which means 
a)the console monitor (hooked into the on-board VGA) goes black
b)the s-video output on the nVidia will start outputting video, and 
c)Keyboard and mouse get redirected to the xserver.

If I do Ctrl-Alt-F1, I get my console back, but s-video blacks out (not acceptable on a server that's running a tv station)... Ctrl-Alt-F7 gives s-video but no console.

Is there any way to either have video still go out when that virtual console isn't live, or run xserver without a virtual terminal at all? (FWIW, the xserver setup won't ever need keyboard/mouse input.) 

Thanks!

---

