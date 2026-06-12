---
title: "compiz fglrx - blinking opengl windows"
date: 2008-02-05
forum: Desktop Effects &amp; Customization
---

### Post by hrabeX on 2008-02-05
I have succesfuly activated compiz, and everything works smoothly. Only OpenGL windows flicking (horizontal) (glxgears, videoplayback through gl extension). 
I have ati radeon xpress 200m with fglrx 8.01. with direct rendering updated. No XGL.

---

### Post by hrabeX on 2008-02-06
see video here:

[http://www.youtube.com/watch?v=XKMxi-V1AjI](http://www.youtube.com/watch?v=XKMxi-V1AjI)
[http://www.youtube.com/watch?v=meuQiZEM2kw](http://www.youtube.com/watch?v=meuQiZEM2kw)

---

### Post by circle on 2008-03-02
Similar here. But I don't have problem when playing video. Only all OpenGL windows blinks, this include applications like glxgears and the x-screensavers using OpenGL.

My another observation is that all OpenGL drawing area (not its windows frame) are always on top, i.e. other applications can only cover the window frame of a OpenGL Application, it seems that the OpenGL part is always drawn on screen even if it should be covered. My wild guess is, this improper drawing of the covered OpenGL area cause the re-draw of the top application, and result in a flickering problem. Attached a screenshot showing an instant that glxgears was covered by Firefox, but still being drawn. Part of the the drawn part was possibly re-cover by Firefox.

I am using the latest ATI propriety driver (8.43.x) on a mobility radeon X1400 card:
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7281 Release

And I am running compiz fusion with AIGLX (not XGL). There is no problem when I use back metacity.

Any clues? Thanks.

*Edited*
I got the same problem for playing video when using the gl (OpenGL) or xv (X11/Xv) video driver in mplayer, but no problem when using the x11 (XImage/Shm) driver, you may try too. But the drawback is that I am not able to view image in size other than the original one, only the windows resize, but not the video... :-(

---

### Post by bixejo on 2008-03-03
I also get the same problem. Video playing area always blinks, and moreover it's always on the top plane regardless of whether I set the focus on another window that is totally or partially over it.

glxgears does not display properly, but just appear what I guess it's the moving gears image split in many small fragments over the screen. I've been reading other threads and looks it's a known bug of fglrx 8.02 driver, which is the one I'm using right now.

The only workaround I found is to temporally disable desktop effects (which is equivalent to going back to metacity) while I'm playing videos. glxgears works also fine with compiz disabled.

I have a 64bits 7.10-Gutsy running on my Toshiba laptop. My video card is an ATI Mobility Radeon HD 2600.

---

### Post by Melcar on 2008-03-03
A thread on this should really be a sticky so people stop posting about it like 100 times.  Maybe a link to the Ubuntu wiki entry on it?
[https://wiki.ubuntu.com/RedirectedDirectRendering]("https://wiki.ubuntu.com/RedirectedDirectRendering")


Currently, you can't use Compiz (running with AIGLX) and any opengl/Xv accelerated rendering at the same time, without suffering from the blinking.

---

### Post by circle on 2008-03-04
> **Melcar said:**
> A thread on this should really be a sticky so people stop posting about it like 100 times.  Maybe a link to the Ubuntu wiki entry on it?
[https://wiki.ubuntu.com/RedirectedDirectRendering](https://wiki.ubuntu.com/RedirectedDirectRendering)


Currently, you can't use Compiz (running with AIGLX) and any opengl/Xv accelerated rendering at the same time, without suffering from the blinking.

Thanks Melcar for the clarification. It would really be better if the above is linked to some pages related to Compiz (CompositManager). :)

Looking forward to the Xorg team and other great guys to fix the issue :)

---

### Post by circle on 2008-03-04
As mentioned by Melcar, seems that this issue is unlikely to be fixed soon. In the mean time, you may use the XImage/Shm video driver as a workaround. BTW is it a known issue that I cannot resize the video (only the windows frame) in mplayer when using the XImage/Shm driver?

Thanks.

---

### Post by bixejo on 2008-03-05
To what video playing concerns, in the following thread you may find a "solution" to avoid blinking video playing:

[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=507332](http://ubuntuforums.org/showthread.php?t=507332)[/COLOR]

I say "solution" because it's actually not a solution, but moving most of the video processing from video card to CPU, which considerably increases the CPU usage during video playing, specially in full screen mode or large windows. It also has another drawback: you may get a rather ugly image pixelation if try to enlarge small resolution videos.

But seems that it actually works (it does for me) and may be enough for some people, so there's the link.

Hope this helps,

---

