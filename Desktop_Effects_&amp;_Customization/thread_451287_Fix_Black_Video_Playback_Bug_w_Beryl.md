---
title: "Fix: Black Video Playback Bug w/ Beryl"
date: 2007-05-22
forum: Desktop Effects &amp; Customization
---

### Post by abbot on 2007-05-22
I have been searching for a while for a fix for this problem and through multiple topic connections and a bit of trial and error I found out how to fix it.  The problem happens when the Beryl window manager is running and you try to play video in any video player.  The sound plays fine but nothing but black is displayed where the video should be playing (except maybe while your moving or resizing the video window).  In order to fix the problem you have to change the video output module in the settings of the video player you are trying to use.  I am copying the directions for the different video players from Benanzo's post in this thread about a similar video problem in Beryl.

[http://ubuntuforums.org/showthread.php?t=432085](http://ubuntuforums.org/showthread.php?t=432085)

> GSTREAMER (TOTEM):
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

Hopefully that works for everyone.

---

### Post by xarmian on 2007-05-22
If you're using Gnome, go to System->Preferences->Multimedia Systems Selector and select the Video tab.. Then select the drop-down box for Plugin and select "X Window System (X11/Shm/Xv)"

This will correct all media players, irregardless of the player (since they default to getting their settings from the system settings).. Unfortunately changing to the Xv plugin gives a very noticable degredation in video quality, and therefore in order to get good video quality you need to use either Totem-xine or gxine..

-Dave

---

### Post by ananddev0 on 2007-05-26
Hi,

    I am also facing the same problem with beryl but,
    I don't see a multimedia in the menu when I go to system -> preferences.

thanks,
Dev

---

### Post by orb9220 on 2007-05-26
> If you're using Gnome, go to System->Preferences->Multimedia Systems Selector ?

I don't have it either

---

### Post by ilantz on 2007-06-02
this fixed my problem with beryl & video playback Thanks !

about the menuitem  "System->Preferences->Multimedia Systems Selector" Being missing,
just open a terminal and type:

```
sed -i 's/NoDisplay=true/#NoDisplay=true/' /usr/share/applications/gstreamer-properties.desktop
```

This will show the menu in the right place.
I'm quite sure this a minor bug related to the menubar, I've posted it @ [https://answers.launchpad.net/ubuntu/+question/7593]("https://answers.launchpad.net/ubuntu/+question/7593")

;)

Enjoy.

---

### Post by jon.reeve on 2007-06-20
This works but when enlarging the video or watching it in fullscreen mode it slows down considerably, the quality sucks, and a whole bunch of frames are lost.

---

