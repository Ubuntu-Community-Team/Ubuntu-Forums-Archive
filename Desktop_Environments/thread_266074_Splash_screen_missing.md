---
title: "Splash screen missing"
date: 2006-09-26
forum: Desktop Environments
---

### Post by canadianwriterman on 2006-09-26
Something happened with a recent set of updates so that I am missing the splash screen. After GRUB, I get code showing the bootup process and then the proper log-in screen. The splash artwork is still in usr/share/pixmaps/splash.

What do I need to do to reinstate the splash screen during bootup? Thanks for your help.

---

### Post by canadianwriterman on 2006-09-26
Added note: I have tried reconfiguring usplash, uninstalling usplash and then reinstalling it through Synaptic and using the Splashscreen utility to "activate" the splashscreen. Nothing worked and still get only code when booting or shutting down. It's not critical, of course, but annoying. Any help would be appreciated. Thanks.

---

### Post by canadianwriterman on 2006-09-27
RESOLVED

I stupidly installed the Mepis version of Automatix on my Dapper box. then uninstalled it and installed the right version. However, before I could install the correct version, system update did an update and replaced the kernel with a Mepis kernel, which nuked my usplash. When I removed the Mepis kernel through Synaptic, everything returned to normal.

---

