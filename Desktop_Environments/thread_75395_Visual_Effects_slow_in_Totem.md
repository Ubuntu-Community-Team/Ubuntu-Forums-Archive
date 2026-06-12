---
title: "Visual Effects slow in Totem"
date: 2005-10-13
forum: Desktop Environments
---

### Post by trey on 2005-10-13
Why are the visual effects such as Goom, smoothwave, chart and monoscope really slow to update on the screen?  It's not that the computer itself is slow, it's like the refresh rate is a really low FPS instead of something much faster like XMMS using OSS/ALSA?  I really like Totem, that's why I'm interested in increasing the refresh rate for gstreamer or whatever it is I need to do.

---

### Post by darkmatter on 2005-10-13
Do you have your 3D drivers installed? 

Slow rendering of visualizations is usually the result of  no 3D acceleration.

---

### Post by trey on 2005-10-13
[QUOTE=darkmatter]Do you have your 3D drivers installed? 

Slow rendering of visualizations is usually the result of  no 3D acceleration.[/QUOTE]

Yes, sorry to not mention that earlier.  I'm also using totem-gstreamer.

$ glxinfo | grep direct
direct rendering: Yes

I even changed the default sound output to ALSA and OSS directly but even though I can hear sound, the visualizations are a really slow FPS refresh rate.  XMMS visualizations are fast, practically real-time, even for full screen.  It looks like constant moving video, whereas the totem/gstreamer visualizations are like "image, sleep, updated image, sleep, updated image, sleep, updated image, sleep, etc."  i'm probably putting to much in to this.

---

### Post by trey on 2005-10-13
the visualizations are normal speed when i install totem-xine instead of totem-gstreamer.  of course they aren't the same visualizations, but they appear real time instead of slideshow-like.  is it just gstreamer that's no good?

---

### Post by trey on 2005-10-16
[QUOTE=trey]Why are the visual effects such as Goom, smoothwave, chart and monoscope really slow to update on the screen?  It's not that the computer itself is slow, it's like the refresh rate is a really low FPS instead of something much faster like XMMS using OSS/ALSA?  I really like Totem, that's why I'm interested in increasing the refresh rate for gstreamer or whatever it is I need to do.[/QUOTE]

noone else cares that the default visualizations are slow in totem?  maybe noone even uses totem?

---

### Post by moopere on 2005-10-16
[QUOTE=trey]noone else cares that the default visualizations are slow in totem?  maybe noone even uses totem?[/QUOTE]

I use Totem for everything, particularly now since Rhythmbox seems to be terminally broken.

But, the very first thing I do after an install is change totem to totem-xine and ditch gstreamer which never works and never has.  I don't know why people package the gstreamer video decoder mess as default (even Kubuntu has gone this way!).    

I moved to Alsa direct multimedia, totem-xine and everything is peachy :)

Cheers,
Craig

---

