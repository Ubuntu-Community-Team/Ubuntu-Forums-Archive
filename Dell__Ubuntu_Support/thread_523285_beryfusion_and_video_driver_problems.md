---
title: "bery/fusion and video driver problems"
date: 2007-08-11
forum: Dell  Ubuntu Support
---

### Post by jmnormand on 2007-08-11
I was wondering if anyone running the intel x3100 (dell 1420n) has managed to get beryl or fusion to play nice with video.  I have both working fine but they really seem to be screwing with the video output.  on metacity video works flawlessly.

when running beryl or fusion i run into the following issues:

xv just crashes the players completely though was expecting this.

x11 plays fine but will not scale video at all.

opengl plays but the video floats over everything, including the command menus of the player.  plus any windows in the back ground cause the video to cut in and out in that area.

any suggestions would be greatly appreciated.

---

### Post by iggykoopa on 2007-08-11
I've run into the same problem, I've just been using gl2 and just making sure there are no windows behind the video. If i figure anything else out then I'll post in here.

---

### Post by phynix on 2007-08-11
try this 

[http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback]("http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback")

---

### Post by jmnormand on 2007-08-12
yeah did get it working in vlc using x11 with no problem.  gstreamer seems to work as well.  mplayer xine are just the buggy ones apparently, of course the ones i was working with.

---

### Post by notwen on 2007-08-12
I'm using Beryl on my 1420n and hve also resorted to using X11 on vlc to watch video files.  Good thing for me I only use VLC for video files, lol.  I was really concerned I would not be able to use Beryl/Compiz/Compiz-Fusion for awhile w/ this new X3100 Intel chipset, glad there some how-to on how to  make it happen. =]

---

### Post by iggykoopa on 2007-08-12
I'm using totem now and it's working good just had to change the video output to No XV in gstreamer-properties.

---

### Post by jacob01 on 2007-08-13
> **jmnormand said:**
> I was wondering if anyone running the intel x3100 (dell 1420n) has managed to get beryl or fusion to play nice with video.  I have both working fine but they really seem to be screwing with the video output.  on metacity video works flawlessly.

when running beryl or fusion i run into the following issues:

xv just crashes the players completely though was expecting this.

x11 plays fine but will not scale video at all.

opengl plays but the video floats over everything, including the command menus of the player.  plus any windows in the back ground cause the video to cut in and out in that area.

any suggestions would be greatly appreciated.

im running beryl on a dell e520 with an intel gma x3000 if that helps

---

