---
title: "undeserved high CPU load"
date: 2008-05-07
forum: Desktop Environments
---

### Post by afasias on 2008-05-07
I have been using Ubuntu since version 6.10. The only complaint I have is that my computer raises high cpu laods without reason.
My computer is a Pentium4 @ 2.66GHz, with 1.5GB DDR Ram and a GeForce 6200 with 256MB.
Most of the experience is very sluggish.
On a clean system with 8.04LTS and with the latest nvidia driver intall (from System -> Administration -> Hardware Drivers), I can run visual effects with amazing speed (for example, the cube rotation, and window selection, and wobbly windows are doing very fast!), but the computer raises very high cpu load on "simple stuff", like moving the scrollbar on Firefox, or moving a window arround (with "wobbly" turned off), or simply doing... nothing! Even if I leave the computer sitting idle on an empty desktop without apps running, I can constantly see a 30-50% cpu usage, which raises up to 100% if a do the simplest thing, even if I move the mouse arround the screen.
I believe that the cpu is utilized to perform action that normally should go to the GPU. However, 3D effects are amazingly fast and I can't give an explanation why the computer can do 3D very well, but goes sluggish in simple 2D stuff.
The high cpu usage slows down everything, and the experience is very poor. For example, it takes several seconds to open a new Firefox window, and I can actually see the window's component drawing one by one, and in the same system with XP I can open a new Firefox instantly in a few fractions of the second and the response is blazing fast.
I would really like to hear some good suggestions! thank you!

---

### Post by stream303 on 2008-05-07
Remember that Firefox in Hardy is still beta-5.  There have been some suggestions about turning off a security measure about "attack sites" in the FF prefs, and deleting some sqlite files in your mozilla profile.  Check out the sticky in the General help forum for a few of the bugs and workarounds as they get worked on.

In the meantime, can you try a lighter-weight browser, such as Epiphany-Browser?  There are many other browsers to choose so I don't want to start a war - just a suggestion that if you go looking for it, look specifically for epiphany-browser.  Uses the same Gecko engine that FF does, at least for now.

---

### Post by DaVince21 on 2008-05-07
Actually, Firefox's scrolling has always demanded high CPU usage as far as I know. Something seems wrong/bottlenecking in the Gecko rendering engine, methinks...

...Well, I'm just glad enough that Firefox doesn't suddenly take up a lot of CPU if you're only waiting for a page to load anymore. :P But still, these kinds of problems really shouldn't exist.

---

### Post by afasias on 2008-05-07
I forgot to mention that I'm using Firefox 2.
Maybe Firefox is not the lightest browser I can try, but I believe that this whole slowness has deeper causes. As I said the CPU goes up high (30-50%) even when no other applications are running at all. The CPU is eaten by Xorg, gnome-panel, compiz.real (if desktop effects are enabled).
It seems that for some reason, the CPU is used to paint stuff on the screen, while this should be the GPU's responsibility. From glxinfo I can see that I'm using NVidia's driver and that Direct Rendering is enabled.
Any ideas?

---

### Post by dhelix on 2008-05-11
Hi,
I have the same problem after i upgraded to 8.04.I use FF3 beta 5 which is shipped with the os.FF not only makes my CPU load high,but it also starts to read endlessly from hdd which results of my laptop being very slow.So i switched to galeon until the final release of FF3.No problems with it,so i think maybe we shud wait a bit...

---

