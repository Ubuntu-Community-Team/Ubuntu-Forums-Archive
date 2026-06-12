---
title: "No direct rendering on second xserver"
date: 2007-12-27
forum: Gaming &amp; Leisure
---

### Post by JoSch on 2007-12-27
Okay I tried forum search - I promise!
But I couldn't find anyone with my problem since everyone has no direct rendering on his FIRST display.

I started a new xserver on tty9 with startx /usr/bin/xterm -- :1 and can play wine games like starcraft and diablo II just perfect even though glxinfo shows mesa driver and no direct rendering - everything is perfectly fast.
But when I try to run a SDL game like xmoto **it's terribly slow so I search for a way to enable direct rendering even on my second xserver.**
How do I do this? everything should be perfect since it uses the same xorg.conf as with my first display.
I have ubuntu gutsy with intel X3100 on a dell d830.
glxinfo shows direct rendering for first display and there I can play everything I cannot on the second display.

---

### Post by radaczynski on 2008-12-29
Seems that I have the same issue here, even though it is Intrepid, the same thing happens...
```
(==) Using config file: "/etc/X11/xorg.conf"                                     
(EE) [drm] Could not set DRM device bus ID.                                      
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI.                        
```

---

