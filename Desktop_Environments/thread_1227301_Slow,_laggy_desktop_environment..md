---
title: "Slow, laggy desktop environment."
date: 2009-07-30
forum: Desktop Environments
---

### Post by arguo_uere_utum on 2009-07-30
Hi all. First time poster, go easy on me.

My machine is running Ubuntu Netbook Remix on an Acer Aspire One ZA3. And trust me, it was not easy. I spent two days after the original install just dealing with horrible lag and resolution issues. Upon first install, the computer's xorg.conf file was essentially blank. Though I installed the drivers suggested by <a href="https://help.ubuntu.com/community/AspireOne">this</a> FAQ for Jaunty, it simply had no device to run the monitor. This error kept cropping up:

(EE) PSB: Failed to load module “Xpsb” (module does not exist, 0)
(EE) PSB(0): the stolenBase is:0×3f800000.
(EE) PSB(0):screnIndex is:0;fbPhys is:0×3f800000;fbsize is:0×007df000.
(EE) PSB(0): First SDVO output reported failure to sync or input is not trainded!!!
(EE) [drm] drmOpen failed.
(EE) PSB (0): [dri] DRIScreenInit failed. Disabiling DRI.
(EE)[drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.

I spent about 6 hours trying to get the xorg.conf file to run the way that other people have managed to do it. No luck. So I opened up NBR in low graphics mode, and manually installed all libraries related to "drm," "dri," and "psb." I was also told to remove the xorg.conf file in order for the machine to manually sense what it has running on it. Reboot, and voila. I have a new xorg file (xorg.conf.new in my Home directory). My resolution is fixed, the interface is much less laggy, and I can play videos. But it's not the end. My mouse cursor still lags as it passes over the screen, and things take forever to load. This is not a slow machine - 1.33ghz on an Intel Atom core should not be doing this to me. Does anyone have any ideas on a fix?

---

