---
title: "GDM resolution too high with Modeline"
date: 2009-01-14
forum: General Help
---

### Post by macinnisrr on 2009-01-14
After much troubleshooting, I finally got my 26" Prive LCD TV to work in its native 1368x768 resolution by adding the following modeline to my xorg.conf

Modeline "1368x768_60.00" 1368 1440 1576 1784 768 771 781 798 -hsync +vsync

After I did so, however, the first resolution my display defaults to is 1600x1200 which my TV does not support.  I used ctl+alt+- to get to a usable resolution, logged in, and changed the resolution to 1368x768 in the screen resoution program. 

The problem is that the GDM login screen still tries to display at 1600x1200, and I have to use the ctl+alt+- method to downscale until I can see something (even if I cycle through all available resolutions this way I never get the correct one, it is always larger than the physical screen). Once I login, everything works great.

I've tried adding modes to the screen section (excluding higher modes and starting with the preferred one), but that just makes my tv display at 800x600, with no options in the screen resolution dialog for anything above that.

I currently have my account set to auto-login, but it's annoying to see my screen display a big blue "UNSUPPORTED MODE" for five seconds during bootup. 

Thanks in advance for any help
Dick MacInnis

---

