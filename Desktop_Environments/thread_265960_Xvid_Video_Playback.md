---
title: "Xvid Video Playback"
date: 2006-09-26
forum: Desktop Environments
---

### Post by izak30 on 2006-09-26
I have the w32 codecs and ffmpeg tools installed, but still xvid video does not play on my system, the audio is fine, but the video is blank. Any ideas?  (I installed these through automatix on Dapper). Thanks

---

### Post by ahaslam on 2006-09-26
What player are you using?
Mplayer & Totem-xine should work well

Tony.

---

### Post by Dinerty on 2006-09-26
Strange, fire up Synaptic Package Manager ... System > Adminstration > Synaptic Package Manager.

Then search to see if these packages are installed:

gstreamer0.10-ffmpeg 

gstreamer0.10-pitfdll 

gstreamer0.10-plugins-bad 

gstreamer0.10-plugins-bad-multiverse 

gstreamer0.10-plugins-ugly 

gstreamer0.10-plugins-ugly-multiverse

---

### Post by izak30 on 2006-09-26
```
rq@rqUbuntu:~$ sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-pitfdll gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
Password:
Reading package lists... Done
Building dependency tree... Done
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-pitfdll is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

It doesn't work with Totem, mplayer or VLC, I'm lost.

---

### Post by Dinerty on 2006-09-26
Is think link any help?

[http://www.ubuntuforums.org/showthread.php?t=244140&page=2&highlight=xvid](http://www.ubuntuforums.org/showthread.php?t=244140&page=2&highlight=xvid)

---

### Post by izak30 on 2006-09-26
That did wonders, I'm never going back :D

---

