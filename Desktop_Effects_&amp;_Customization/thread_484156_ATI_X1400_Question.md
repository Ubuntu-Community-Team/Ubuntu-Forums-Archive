---
title: "ATI X1400 Question"
date: 2007-06-25
forum: Desktop Effects &amp; Customization
---

### Post by hunkybill on 2007-06-25
Hi,

Fujitsu Lifebook 8210, ATI X1400, Feisty 7.04.

I seem to have a working system, but a nagging issue I would like an answer to.

glxgears works, giving me 

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
34818 frames in 5.0 seconds = 6961.226 FPS
36599 frames in 5.0 seconds = 7316.544 FPS

So I started checking and it seems I am having DRI issues.

I checked my /var/log/Xorg.log.0 file and I see this:

(II) Loading extension XFree86-DRI
(==) fglrx(0): NoDRI = NO
(II) Loading extension ATIFGLRXDRI
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): DRI initialization successfull!
(II) fglrx(0): [DRI] installation complete

fglrxinfo command shows me this:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6334 (8.34.8)


Currently I tried Compiz Fusion and it has problems.Beryl continues to work fine. I am pretty sure I used to have no problems with DRI. Is there something I can troubleshoot here, or is this normal?

I am running the ATI fglrx Driver in my xorg.conf, and have Composite disabled command in there too...

Any tips most appreciated to getting this straightened out. I cannot run fgl-glxinfo program without getting this:

Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig

which tells me either something IS wrong with my system, or, I should expect to see that as I cannot use that??

Thanks!!

---

### Post by golfing22 on 2007-07-02
Hi, I have an Inspiron 1501 laptop with an ATI Express 200 or something and I'm having the exact same error as you are.  I've tried everything to fix it also, including manuallying installing the driver, installing from apt-get and the restricted driver manager.  Beryl work perfect but 3d games like Warsow are extremely slow.  If you find a fix please inform please, as I will do likewise.

Thanks,
Tyler

---

### Post by newbie2 on 2007-07-03
[http://ubuntuforums.org/showthread.php?t=490937](http://ubuntuforums.org/showthread.php?t=490937)

---

