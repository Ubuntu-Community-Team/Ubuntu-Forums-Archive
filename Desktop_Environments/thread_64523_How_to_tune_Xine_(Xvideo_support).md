---
title: "How to tune Xine? (Xvideo support?)"
date: 2005-09-11
forum: Desktop Environments
---

### Post by cd-r80 on 2005-09-11
xine-check:
 hint ] Your X server doesn't support YV12 overlays.
         That means xine will have to to color space transformation and scaling
         in software, which is quite CPU intensive. Maybe upgrading your
         X server will help here.
         If you have an ATI card, you'll find accelerated X servers on
         [http://www.linuxvideo.org/gatos/](http://www.linuxvideo.org/gatos/)

[ hint ] Your X server doesn't have any XVideo support...
         XVideo is an X server extension introduced by XFree86 4.x. This
         extension provides access to hardware accelerated color space
         conversion and scaling, which gives a great performance boost.
         If you have a fast (>1GHz) machine, you may be able to watch all
         kinds of video, anyway. You will waste lots of CPU cycles, though...

How to start tuning xine & X? With these hints? Any easy apt-get methods? I have Ati R9250 running well, Duron 750, 128RAM. That URL: not found...

---

