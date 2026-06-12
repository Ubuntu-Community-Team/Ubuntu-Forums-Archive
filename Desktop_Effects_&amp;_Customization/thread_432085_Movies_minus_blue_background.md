---
title: "Movies minus blue background"
date: 2007-05-03
forum: Desktop Effects &amp; Customization
---

### Post by huzzak on 2007-05-03
In all of the videos showcasing how awesome Beryl is they show a movie being played and they wiggle that window around and they zoom in and stuff.  I have Beryl installed and if I try to do the same a blue patch replaces where the movie is.  Is there any way I can get rid of this?

---

### Post by benanzo on 2007-05-03
depending on which movie player you are using...


GSTREAMER:
For Totem with the gstreamer backend (totem-gstreamer) open a terminal and type gstreamer-properties
Then click the Video tab and under Default Output select "X Window System (No Xv)" for the plugin. then restart totem.  this will work for any video app that uses gstreamer

MPLAYER:
If you use mplayer (gmplayer) right-click on the screen and select Preferences then select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
then restart mplayer.  The issue here is that it won't go fullscreen with the video.  I suggest using VLC or totem-gstreamer.

XINE:
if you use xine then click File>>Configure>>Preferences
make sure under experience_level you select Master Of The Known Universe
you will then get a tab at the top for video.  under driver select "xshm".  then restart xine.  this also works if you are using the totem-xine backend.  just run gxine at the terminal and follow the steps.

VLC:
for VLC select Settings>>Preferences  then in the bottom-right of the window check the Advanced Options box.  Then expand the Video item on the left and select Output modules.  Then in the list on the right for Video output module change it to "X11 video output".   then resart VLC

---

### Post by huzzak on 2007-05-03
Thanks benanzo.

I swapped to VLC because totem wouldn't do it with either xine or gstreamer as its backend and mplayer did this odd thing where in fullscreen it would be on every single desktop.  VLC works great.  Thanks again.

---

### Post by fulanodetal316 on 2007-05-22
Your awesomeness is beyond compare! I have been fighting with VLC over this for about 2 days now. Thank you sooo much!

:popcorn:Now I can finally watch my movies!

---

### Post by fwendt on 2007-06-01
But, what is the real issue here? Beryl? xorg? the video driver? xv design flaw? I guess there's a bug filed in Launchpad somewhere - I just can't find it.
It's a pita to have to keep turn desktop effects on and off.

---

### Post by jon.reeve on 2007-06-24
As it may have been noted somewhere else, this workaround for VLC (changing the output to X11) looks like it fixes the problem, but then has a massive side-effect, at least for me and several others: it makes the video extremely choppy when expanded. The quality and frame rate are terrible in full-screen mode, and it seems to eat up processor power tremendously. I've resigned myself to having to turn on and off Beryl/Compiz whenever I want to play a video, which is a pain. Please let me know if there is ever a fix for this.

---

### Post by gkiller on 2007-06-24
> **fwendt said:**
> But, what is the real issue here? Beryl? xorg? the video driver? xv design flaw? I guess there's a bug filed in Launchpad somewhere - I just can't find it.
It's a pita to have to keep turn desktop effects on and off.
Do you have an ATI card? If yes, then it's the fault of ATI.

On my Nvidia with the proprietary drivers even Xv videos play normally in window or fullscreen, in every player. So maybe remember this when you buy your next graphics card ;) (I had an ATI before... Nvidia is so much better and easier to set up in this case)

---

### Post by fwendt on 2007-06-24
> **gkiller said:**
> Do you have an ATI card? If yes, then it's the fault of ATI.

On my Nvidia with the proprietary drivers even Xv videos play normally in window or fullscreen, in every player. So maybe remember this when you buy your next graphics card ;) (I had an ATI before... Nvidia is so much better and easier to set up in this case)

My card is an Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03), and it's sitting in a laptop.

I too know that Nvidia "just works", but they also keep all of their source code closed, and even their specs on how the cards work - so there's no way to get full control of your computing environment. In the ATI case, it's somewhat better (X300 cards have a true open and free driver that works). From what I know, Intel is no better than ATI.

Being able to use your computer to it's full potential sure is good, but truly owning your product tastes better.

---

### Post by gkiller on 2007-06-24
> **fwendt said:**
> My card is an Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03), and it's sitting in a laptop.

I too know that Nvidia "just works", but they also keep all of their source code closed, and even their specs on how the cards work - so there's no way to get full control of your computing environment. In the ATI case, it's somewhat better (X300 cards have a true open and free driver that works). From what I know, Intel is no better than ATI. 

Being able to use your computer to it's full potential sure is good, but truly owning your product tastes better.
You are right, but it's also a matter of personal taste. For me proprietary fully working Nvidia drivers are better than half-working open-source Ati drivers. If all things are equal or if OSS drivers have a bit less functionality, I'd take them too, but the difference in the Nvidia<>Ati case is just too big.

But normally Intel drivers should be quite good. I don't know then what causes the Xv problem. Maybe searching the forums at [http://forums.opencompositing.org](http://forums.opencompositing.org) and [http://www.compiz.org](http://www.compiz.org) or even some Intel forums might help in findind a solution.

---

### Post by chrisrx on 2007-06-24
I think this is the same problem as me and other people are having here [http://ubuntuforums.org/showthread.php?p=2904830](http://ubuntuforums.org/showthread.php?p=2904830) in the same chip (intel 945gm).
If anyone could offer a solution it would be very much aprreciated.

---

