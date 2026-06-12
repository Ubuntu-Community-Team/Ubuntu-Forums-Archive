---
title: "fiesty, beryl, radeon mobility 9000, 2 problems, water effects, play videos"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by travm on 2007-10-28
So I have gotten most beryl functions working my laptop (dell latitude d600), but I cannot seem to get the water effects working.  When i hit the shortcut keys, nothing happens.  
Not really sure where to start since everything else works.  only thing that comes to mind is that maybe the os radeon driver doesnt support dx8 functions for my card?
Also i've seen its a common problem, but the fix is unacceptable (blocky video).  When I play videos and have beryl running the desktop I cannot see the videos.  If i select xfce4 as the video manager I have no problem with the videos.  The fix is to change gstreamer-properties, video properties to x11(noXV).  This produces very blocky video and is unacceptable.  Is there a better workaround for this or must I always disable beryl to watch videos?
I am using fiesty still.

---

### Post by CarpKing on 2007-10-28
Last I heard the radeon drivers didn't support water effects.  For video issues, I'd recommend upgrading to Gutsy, as that workaround isn't necessary there.  If you want to stay with Feisty, I would recommend using gXine or Mplayer for videos, as I had more luck with those (the video will still go black if you adjust the window's opacity or drag it with wobbly windows on; this hasn't changed in Gutsy either but all the video players now work the same as those two did in Feisty).

---

### Post by travm on 2007-10-29
i would love to upgrade.  ill post in 2 weeks when my dialup has finished downloading the new version.

---

### Post by travm on 2007-10-29
> **CarpKing said:**
> Last I heard the radeon drivers didn't support water effects.  For video issues, I'd recommend upgrading to Gutsy, as that workaround isn't necessary there.  If you want to stay with Feisty, I would recommend using gXine or Mplayer for videos, as I had more luck with those (the video will still go black if you adjust the window's opacity or drag it with wobbly windows on; this hasn't changed in Gutsy either but all the video players now work the same as those two did in Feisty).

i use totem.  gXine doesnt seem to use gstreamer which i need to use the restricted codecs.  totem may also be mplayer, im not sure.  In the menu it is called Movie Player

---

