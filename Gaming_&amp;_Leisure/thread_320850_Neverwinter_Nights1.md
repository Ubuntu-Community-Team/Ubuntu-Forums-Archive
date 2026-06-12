---
title: "Neverwinter Nights1"
date: 2006-12-18
forum: Gaming &amp; Leisure
---

### Post by Elvish Legion on 2006-12-18
Is there a work around for the choppy game play with ATI cards?  If so how?

---

### Post by pay on 2006-12-18
Do you have the ati-drivers installed? ```
fglrxinfo
glxinfo | grep rendering
```

---

### Post by Elvish Legion on 2006-12-18
Yup

jduvall@jduvall-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

jduvall@jduvall-laptop:~$ glxinfo | grep rendering
direct rendering: Yes
jduvall@jduvall-laptop:~$

---

### Post by Kubunteando on 2006-12-25
Check this:

[http://nwn.bioware.com/forums/viewtopic.html?topic=405580&forum=72](http://nwn.bioware.com/forums/viewtopic.html?topic=405580&forum=72)

Do you mean by choppy that after around 1 hour playing the Hard Disk starts to work heavily and the game goes really slow or unusable?

You can check the RAM memory that is using, if it is huge (in my case it reached 2.8GB, I have 1GB RAM and 2GB SWAP) Then it is the ATI drivers mamory bug. I had also problems when playing Cube 2 Sauerbraten. I have the same drivers 8.28. It does not matter if they are from the Ubuntu repositories or from ATI itself.

You can update to the last ATI drivers if your card is supported on those (mine it is not).

In my case I installed the Open Source drivers with DRI. It needs some work, even some compiling, but I got a much better performance (specially lower CPU usage, so the game runs really smoothly). For this you can check:

[www.mesa3d.org](www.mesa3d.org)
dri.freedesktop.org

If you are using Ubuntu edgy, you need MESA 6.5.1. Thr DRI drivers will give you the direct rendering or HW acceleration. The output of my "fglrxinfo" is:

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 4x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.1

Also I used the section of "Tweak the performance" of:
[http://www.gentoo.org/doc/en/dri-howto.xml](http://www.gentoo.org/doc/en/dri-howto.xml)

In my case if I enable the Fast Writes (as mentioned in the link) this crashes the system.
You maybe are more lucky.

Actually I am surprised that this issue does not appear more often. It took me a couple of months noticing that the issue did not came from Linux, but from the ATI drivers.

---

