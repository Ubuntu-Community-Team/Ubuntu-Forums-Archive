---
title: "Thunar video thumbnails"
date: 2012-08-28
forum: Desktop Environments
---

### Post by Rob Glenn on 2012-08-28
I'm using xfce, and have noticed that Thunar has trouble thumbnailing video files.  Mostly mp4's, but some flv's as well.

I remember a similar issue with Nautilus, related to a bug in gstreamer.  I found an excellent workaround to use ffmpeg as the thumbnailer (instead of totem).  As a side benefit, it was oodles faster.

I would like to get Thunar to do the same.  However, Thunar seems to have an entirely different architecture for thumbnails, involving something called "tumblerd" and shared object plugins.  One of these contains the acronym "gst" in its name, which leads me to believe it is picking up the same gstreamer bug that breaks Totem/Nautilus.  

Anyone know how to fix this?  Hacking and recompiling a .so to use ffmpeg, instead of the broken gstreamer library, seems quite complicated.

Thanks!

---

