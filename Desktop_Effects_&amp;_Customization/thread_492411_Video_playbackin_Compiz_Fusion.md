---
title: "Video playbackin Compiz Fusion"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by slibuntu on 2007-07-04
Like many people, im getting audio with no video, and compiz is showing up no errors in the terminal either, i cant find a fix for it, is there one? Thanks

---

### Post by shafin on 2007-07-08
I need it too.

---

### Post by alex_anthony on 2007-07-08
problem is with your video output settings:
try this
GSTREAMER (TOTEM):
For Totem with the gstreamer backend (totem-gstreamer) open a terminal and type gstreamer-properties
Then click the Video tab and under Default Output select "X Window System (No Xv)" for the plugin. then restart totem. this will work for any video app that uses gstreamer

MPLAYER:
If you use mplayer (gmplayer) right-click on the screen and select Preferences then select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
then restart mplayer. The issue here is that it won't go fullscreen with the video. I suggest using VLC or totem-gstreamer.

XINE:
if you use xine then click File>>Configure>>Preferences
make sure under experience_level you select Master Of The Known Universe
you will then get a tab at the top for video. under driver select "xshm". then restart xine. this also works if you are using the totem-xine backend. just run gxine at the terminal and follow the steps.

VLC:
for VLC select Settings>>Preferences then in the bottom-right of the window check the Advanced Options box. Then expand the Video item on the left and select Output modules. Then in the list on the right for Video output module change it to "X11 video output". then resart VLC

---

### Post by shafin on 2007-07-10
Thanks a lot

---

### Post by slibuntu on 2007-07-11
Yeah thanks alex_anthony. You're the kind of person that makes these forums great!:cool:

---

### Post by mrgnash on 2007-07-12
Too bad X11 is nowhere near as nice as XV/OpenGL :(

---

### Post by duydaniel on 2007-07-18
> **alex_anthony said:**
> problem is with your video output settings:
try this
GSTREAMER (TOTEM):
For Totem with the gstreamer backend (totem-gstreamer) open a terminal and type gstreamer-properties
Then click the Video tab and under Default Output select "X Window System (No Xv)" for the plugin. then restart totem. this will work for any video app that uses gstreamer

MPLAYER:
If you use mplayer (gmplayer) right-click on the screen and select Preferences then select the Video tab and under Available Drivers select "X11 (XImage/Shm)"
then restart mplayer. The issue here is that it won't go fullscreen with the video. I suggest using VLC or totem-gstreamer.

XINE:
if you use xine then click File>>Configure>>Preferences
make sure under experience_level you select Master Of The Known Universe
you will then get a tab at the top for video. under driver select "xshm". then restart xine. this also works if you are using the totem-xine backend. just run gxine at the terminal and follow the steps.

VLC:
for VLC select Settings>>Preferences then in the bottom-right of the window check the Advanced Options box. Then expand the Video item on the left and select Output modules. Then in the list on the right for Video output module change it to "X11 video output". then resart VLC

Thanks alot.
the Totem is working now. However, it is impossible to minimize... the program fills up the screen... there is no title bar. Whenever Compiz is running... that problem happen. :confused:

---

### Post by TutoWRM on 2007-07-31
by any chance is this posible to use on vmware.... i'm havin' the same semi-transparent windows when i change to fullscreen mode, same as the video but on vmware but i can't find where to change it, i even tried to look up on the xorg.conf because somewhere i have readed that the problem may lay on my xorg... but no results, and tried to configure fusion from the general option but i did'n know what to do there :S. please, on beryl i had no problem nither with the video (solved) or vmware (unsolved). I have an Intel 945 video card, running on Ubuntu feisty, with compiz fusion.

---

### Post by kevinmedina on 2007-08-05
Be sure to give gremlinzzzz credit for the fix....

---

