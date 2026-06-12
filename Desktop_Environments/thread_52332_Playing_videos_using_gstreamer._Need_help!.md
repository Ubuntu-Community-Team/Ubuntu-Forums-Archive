---
title: "Playing videos using gstreamer. Need help!"
date: 2005-07-27
forum: Desktop Environments
---

### Post by fresco on 2005-07-27
Hi all!

*For some time I am forced to use xine-lib+totem-xine or xfmedia (it doesn't matter) to open video files. When I use totem-gstreamer for example, audio runs nice, but not video. It looses smooth playback - framerate is lower than natural. It feels like something is slowing its performance.  :?  What's with gstreamer? Are there settings I can play with?

The System is Duron 1200 256 ram 40gb hdd, but I'm not sure it is hardware.

*And second. After installing all the codecs and realplayer, process realplay-bin duplicates and freezes when trying to open real audio files so i have to switch it off and manually open files in totem.


Thanks...  ;-)

---

### Post by jadugarr on 2005-07-27
[QUOTE=fresco]Hi all!

*For some time I am forced to use xine-lib+totem-xine or xfmedia (it doesn't matter) to open video files. When I use totem-gstreamer for example, audio runs nice, but not video. It looses smooth playback - framerate is lower than natural. It feels like something is slowing its performance.  :?  What's with gstreamer? Are there settings I can play with?

The System is Duron 1200 256 ram 40gb hdd, but I'm not sure it is hardware.

*And second. After installing all the codecs and realplayer, process realplay-bin duplicates and freezes when trying to open real audio files so i have to switch it off and manually open files in totem.


Thanks...  ;-)[/QUOTE]
 This is just a wild guess but gstreamer may be more memory intensive than xine.  Try playing a video using totem-gstreamer and watching the gnome system monitor to see how much memory is being used.  Also make sure your using the latest version of gstreamer from backports.  Other than that i don't know why xine would play smoother than gstreamer.

As for your problem with realplayer, I don't have any clue as I have never messed with real audio.  Sorry.

---

