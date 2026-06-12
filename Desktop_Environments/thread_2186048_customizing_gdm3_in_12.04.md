---
title: "customizing gdm3 in 12.04"
date: 2013-11-05
forum: Desktop Environments
---

### Post by JKyleOKC on 2013-11-05
After a couple of years doing battle with lightdm, I've switched my display manager to gdm. However I've not found any way to set the background or logo for the login window. Currently it's pure black, which isn't bad but I'd prefer a nice scene. I've installed the latest version of gdm3setup, but it triggers apport errors when attempting to change the background. The ubuntu-tweak program has no effect at all; it appears to be written for earlier versions of gdm; my system has version 3.0.4. I also have xfrce 4.10 installed via the PPA, rather than the default. Can anyone tell me where the background image is likely to be stored on my systems, or whether I need to have all Gnome libraries loaded as the default (at the moment both the Gnome and KDE boxes are un-checked in the startup and sessions dialog)?

Many thanks!

---

### Post by JKyleOKC on 2013-11-25
After a kernel update that required a reboot, I discovered that gdm was incompatible with my system at boot time; it seemed to be missing a dependency or two used only during initialization. Rather than debug the issue, I simply switched back to lightdm and abandoned gdm altogether.

I'm marking this thread solved to warn others who might try it...

---

