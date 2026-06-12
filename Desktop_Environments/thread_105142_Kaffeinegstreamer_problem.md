---
title: "Kaffeine/gstreamer problem"
date: 2005-12-17
forum: Desktop Environments
---

### Post by Antoine.L on 2005-12-17
When I click on a video file (an mpeg or avi or some-such) in Konq, Kaffeine launches and imediatly spits out the following error:
> xvimagesink.c(740): gst_xvimagesink_get_xv_support: /internal_thread/thread_vbin/vbin/videosink:
No port available
The sdl video sink sort of works - it can't do full-screen playback.  I'm hoping that if I get xvimagesink working, maybe it will support full-screen playback.

I'm using the flgrx xorg drivers, if that makes a difference, but I was having this problem before I switched away from whatever the default is.

---

### Post by Antoine.L on 2005-12-19
Fixed it.  It was broken twice, for two different reasons:

It was broken by the default install because the default xorg driver doesn't support xvideo.

It was then also broken because the flgrx driver doesn't support xvideo (on a Radeon 9500 Pro).

Switching to the ati driver fixed xvideo, but now 3d performance sucks.  Oh well, hardware-overlay is more important.

---

