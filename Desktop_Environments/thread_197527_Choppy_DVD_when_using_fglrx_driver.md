---
title: "Choppy DVD when using fglrx driver"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Mr. Sinister on 2006-06-15
If I use the fglrx driver in my xorg.conf file, my DVD playback is choppy. If I use the ati driver, my DVD playback is smooth (but I can't run any 3D app).

I ran xine-check with both drivers. With the ati driver, everything was good, but with the fglrx one I get the following:
```
[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to do color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         http://www.linuxvideo.org/gatos/
         press <enter> to continue...

[ hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to do color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         http://www.linuxvideo.org/gatos/
         press <enter> to continue...

[ hint ] Your X server doesn't have any XVideo support...
         XVideo is an X server extension introduced by XFree86 4.x. This
         extension provides access to hardware accelerated color space
         conversion and scaling, which gives a great performance boost.
         If you have a fast (>1GHz) machine, you may be able to watch all
         kinds of video, anyway. You will waste lots of CPU cycles, though...
         press <enter> to continue...
```

I'm running Dapper with all the latest fixes on a P4 1.7GHz Notebook with a Radeon R250 Lf [Radeon Mobility 9000 M9] video card.

---

