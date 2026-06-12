---
title: "ati + amd64 + cvscedega + steam"
date: 2005-06-29
forum: Gaming &amp; Leisure
---

### Post by OneSeventeen on 2005-06-29
So I've downloaded the new ati drivers for my x200 graphics card, and I get about 300FPS on the "gears test", and I've heard I should get at least 1000FPS before thinking of gaming.

I tried to apt-get install xorg-driver-fglrx hoping that might help, but since the other driver is there, I get the "trying to overwrite `/usr/X11R6/bin/fgl_glxgears', which is also in package fglrx64-6-8-0" error.

I am running Hoary for the amd_64 platform, which gives me errors anytime I try to make software, such as cedega.
"#error Unknown CPU architecture!"


I really want to play counter-strike: source on my amd64 laptop with ubuntu 64. Is this possible?  anyone else have these issues?

I don't mind working at getting this up and running, I just want to know where to start.

---

### Post by DarkManX4lf on 2005-06-30
well for me, i got as far as installing steam using cedega but when trying to run cs1.6 i get 4fps in game....when i used to have mandrake i used to get 70fps in cs1.6 (i have a ati radeon 9800 oc'ed to xt).....


i followed this guide 

[http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ATI](http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ATI)

to get my ati drivers installed, if you follow that guide and want to know what version of linux kernel  you are using just type this in the terminal

uname -r

or 

sudo uname -r

either one should work then run glxgears you should be getting good fps now

---

