---
title: "compiz, nvidia-settings don't work together nicely"
date: 2008-12-27
forum: General Help
---

### Post by rmcgowan on 2008-12-27
I've been playing around with compiz on my KDE/kubuntu system for several weeks, now.  IIRC, in some piece of documentation, I read about some programs having problems with the DISPLAY value used by compiz (:1.0), and it gave instructions on how to set up these so they would work.  This included setting the DISPLAY value to :0.0, but I think there was more than just that.

The problem is that I can't seem to find this document.  And every search idea I've had has either not had it, or the list is so long that it would take an eternity to look through each item.

So, I ask if anyone knows the place where this information is to be found?

Additional details:  When I run 'nvidia-settings' to change, for example, the display device from my LCD to a projector, the program generates this error:  "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."  However, I am using the Nvidia driver, as the compiz special effects are working, and would not be without it.

The problem is the DISPLAY is set to :1.0 rather than :0.0, so I set up the environment so the value is correct and the program now starts, but without any decorations.  I cannot resize, minimize or otherwise change the window.  In addition, the left/right mouse button reversal (I'm left handed) has no effect, I need to reverse the button usage when working within the displayed application window.

Worse yet, when I change to the projector, which runs at 1024x760 (the LCD laptop is 1440x960), it appears that the screen :1.0 does not "resize" to the lesser resolution, leaving me with windows that extend beyond the physical boundary of the projector display, and which cannot be cleanly adjusted to fit in the real estate available.  In particular, going to full screen mode, for a slide show, only shows the center of the full photograph.

Thanks,

Bob

---

