---
title: "Dual Video Fails Out of nVidia IGP Mobo"
date: 2009-01-24
forum: Desktop Environments
---

### Post by Quantumstate on 2009-01-24
I just can't seem to get xorg.conf right.  Have a mobo with nVidia 9300 IGP, and am trying to feed a 720p projector and 1024x768 case display.  Running Intrepid and nVidia driver 180.22.

When I boot, if the VGA case display is plugged that is all that will ever display.  The projector gets nothing.  If VGA is not plugged and HDMI is, I get all video on the projector from POST through KDE.  So it seems I have to do without the case display, unless I un/plug each boot?

Also I can't get the resolution on the projector right.  It's native 1280x720, but when I use the default xorg.conf file the PJ only comes up in 640x480.  OK says I, its EDID is busted, so I hard-coded a modeline in xorg.conf and set the monitor to use that.  

Now it insists on coming up in 1024x768 no matter what.  I run nvidia-settings and the choice for 1280x720 is not there.  So I set it to one that's close, like 1340x768, and it seems to switch to that so I save in xorg.conf.  Reboot, but back to 1024x768.  I see that in xorg.conf a "MetaMode" is set to the higher resolution, but it seems to be ineffective.

I just want native pixel-for-pixel 1280x720.  Why won't X cooperate?

---

