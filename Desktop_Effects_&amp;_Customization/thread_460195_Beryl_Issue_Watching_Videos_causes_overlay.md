---
title: "Beryl Issue: Watching Videos causes overlay?"
date: 2007-05-31
forum: Desktop Effects &amp; Customization
---

### Post by GabrielDunn on 2007-05-31
When I am using Beryl and try to watch a video using any video program (VLC by default) I see these overlaid lines or no image at all.  When I switch to metacity it works fine.  I hate switching desktop managers everytime I want to see a video.

Is this a driver issue or a beryl issue?  Have any of you had the same problem?

I'm running fiesty 7.04 on a dell e1705.

---

### Post by Soybean on 2007-05-31
There's a trick to it... it varies by video player, and I don't know the answer for VLC off the top of my head. In mplayer, you go to the preferences menu, the video tab, and pick a different driver (I believe "xv" or "x11" are good). I seem to recall it being something similar in VLC. Hopefully you can find it.

Note that this can decrease video playback performance, so depending on your hardware, it may be better to just drop to metacity for videos. #-o The problem has to do with the way Beryl draws windows conflicting with the higher-performance methods of video playback... I don't really know the details, but it is a Beryl thing.

---

