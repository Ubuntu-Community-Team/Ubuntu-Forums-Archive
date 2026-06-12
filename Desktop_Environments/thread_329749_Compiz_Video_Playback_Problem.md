---
title: "Compiz Video Playback Problem"
date: 2007-01-02
forum: Desktop Environments
---

### Post by Lem on 2007-01-02
I've just installed freedesktop compiz and it runs very well with a much smaller performance hit than beryl. (Due to my nvidia 6150 onboard card, I had to run beryl in 'copy' mode which ate about 25% of my video grunt)

However, (and I had the same problem with Beryl) if I change the size of the window or try to go fullscreen when using totem (I tried gstreamer and xine versions) it crashes.

I'm using the latest 9746 nvidia drivers and have the AddARGBGLXVisuals line in my xorg.conf

---

### Post by Lem on 2007-01-03
Disabling xv hardware acceleration by using x:shm as the driver in totem config seems to have helped, but I now have unassisted video playback.. not ideal.

---

