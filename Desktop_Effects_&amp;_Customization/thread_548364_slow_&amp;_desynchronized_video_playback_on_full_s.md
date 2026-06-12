---
title: "slow &amp; desynchronized video playback on full screen when playing video in beryl"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by cyneuron on 2007-09-11
hello there

video playback under beryl, is slow & desynchronized with video when run full screen in beryl.

i have tried suggestions available on similar thread like :

1. add this to /etc/mplayer/mplayer.conf 

# Drop frames to preserve audio/video sync.
hardframedrop = yes


2. One potential quick fix that solved the choppy fullscreen video problem for me: In Beryl Settings Manager, General Options, Advanced, check "Unredirect Fullscreen Windows".


But none is working.

video playback still gets slowed down, and audio & video get de-synchronized when switched to full screen.

Please someone help.

---

### Post by cyneuron on 2007-09-11
please anyone....

---

### Post by mrblondeisback on 2007-10-02
Big bump here, I'm using whatever default program came with Ubuntu(Totem, right?), and the same happens to me, unless I drop the resolution down to 640x480.  I'm real new to this Ubuntu thing and Linux in general, and this is the first real problem I've encountered.  Is there a solution or at least a way to make the resolution automatically change when I'm running full screen then change back?  Any help would be awesome.

---

### Post by mrblondeisback on 2007-10-02
also, this thread seems to be in the wrong place.  I'll post again in the Video section with a link.

---

### Post by teabeartom on 2007-10-05
Bump!  
This is the reason I quit using compiz/beryl...  I used it with the closed source ATI drivers (fglrx) about six months ago.  I really wanted to play videos, so I finally ended up just going to a non-accelerated desktop.  If there is any way to fix this, please let us know!

---

### Post by cyneuron on 2007-10-05
use vlc media player.... go to its video output video settings, and use xvideo.....this can play even 2 videos simultaneously without any slow down.....

mplayer failed here..

even xine can do same with same tweaks.....but vlc gives better performance.....

---

### Post by abard on 2007-10-09
hi there :)
a way to fix it not .
workaround ... yes ...
u can use the default overlay (XGL is a secondary overlay) 
it will take all ur screen but it will give 100% juice  ...
use the prefix DISPLAY=:0 b4 the command and Behold the force of ubuntu ;-)
```

 DISPLAY=:0 xine

```

good luck 

EYL

---

### Post by prash@linuxitarian on 2007-10-14
I tried this and it seemed to work for me on totem at least:

In CompizConfig Settings Manager -> General Options and go to the Display Settings tab

In the outputs window add this :

<your screen resolution>+0+0
move it up so that it is first...

This seemed to fix it

___________________

Ubuntu Gutsy
ATI Mobility Radeon 9600
IBM T42, 1.5GB RAM, 1.8GHz Intel

---

