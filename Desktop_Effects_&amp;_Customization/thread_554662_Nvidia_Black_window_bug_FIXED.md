---
title: "Nvidia Black window bug FIXED"
date: 2007-09-19
forum: Desktop Effects &amp; Customization
---

### Post by AriciU on 2007-09-19
For those of you that are having issues with black windows and stuff, install the new nvidia driver (100.14.19) released yesterday and all your problems will be fixed.

It works with xorg 7.3 also and there is a big improvement of compiz performance with it.

Get it from [www.nvidia.com](www.nvidia.com)


EDIT: I don't think ubuntu will package it up any time soon, don't think it will come with Gutsy either since it's probably too late to add it so you'll have to install it manually. If you don't know how to do it or experience problems with the driver not getting used on reboot then just get on irc and ask about "blacklisting nv driver on bootup" in the #ubuntu channel.

---

### Post by martynp on 2007-09-19
So I download it and typed 'sh NVIDIA-Linux-x86-100.14.19-pkg1.run' (without the quotes) in terminal and get a message saying it can't open.

Any thoughts please?

Thanks

---

### Post by AriciU on 2007-09-19
Never got an error like that... maybe you've tried it while running and X session.

You must install the drivers from terminal. Just kill the GDM process and you'll get to native terminal...

---

### Post by tlacuache on 2007-10-24
I'm running the new nvidia driver and I've still got the black windows bug.

This is from my glxinfo:

...
OpenGL version string: 2.1.1 NVIDIA 100.14.19
...

nvidia-settings also confirms I'm at 100.14.19. So I guess it doesn't totally fix the problem.

-SG

---

### Post by nawsher on 2007-12-14
hey .... i just downloaded the new nvidia driver last night, and installed it in my hp dv2000 notebook. and it works flawlessly ........ no more black window bugger :lolflag:! thanks to all you guys who contributed. i been going nuts for this fix .... 

btw, AriciU is right ..... you just have to kill the GDM, and install from terminal.

cheers.

---

### Post by Vinno on 2007-12-14
What black window bug? It isnt the top part of a title of a program that just bugs up sometimes is it?

---

### Post by FuturePilot on 2007-12-14
> **Vinno said:**
> What black window bug? It isnt the top part of a title of a program that just bugs up sometimes is it?

It's actually where entire windows will just be black. You can't see anything but a black window. The window doesn't get redrawn properly due to the texture_from_pixmap extension in the older drivers. They improved it in the latest one though.

---

### Post by wiraqcza on 2007-12-14
Umm, how to restore old(default) ubuntu nvidia drivers, because the new ones screwed my X'es totally.

---

### Post by PfromD on 2007-12-14
sry if this if off course, but it sounds familiar ... is this blackening what lies behind my issue described in [http://ubuntuforums.org/showthread.php?t=6385529?](http://ubuntuforums.org/showthread.php?t=6385529)

---

### Post by bigchrisrogers on 2008-03-21
Well I've come to this thread today because I have the 'Black Windows' problem.  When I've a few TABS open in firefox and several windows open elsewhere, I can then only get windows that are totally black inside (window frame etc O.K.).  Even closing windows down does not allow new ones to come clean.

I already have nvidia driver 100.14.19 installed in Gutsy and still get thr proble.

Still looking !!!

---

### Post by joehill on 2008-03-23
It was fixed under Gutsy, but when I upgraded to Hardy, the problem came back.  Any ideas on how to get rid of the black windows again? Thanks.

Joe

---

### Post by Endolith on 2008-05-31
This is definitely NOT fixed.  Every time I upgrade Ubuntu or the nvidia driver is upgraded, I turn on Compiz to see if it works yet, and it never does.  Always black windows after a few are open.  nvidia-glx-new 169.12+2.6.24.12-17.36

---

