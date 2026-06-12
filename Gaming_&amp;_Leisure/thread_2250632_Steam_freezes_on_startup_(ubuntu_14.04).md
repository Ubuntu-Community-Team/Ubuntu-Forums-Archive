---
title: "Steam freezes on startup (ubuntu 14.04)"
date: 2014-10-29
forum: Gaming &amp; Leisure
---

### Post by Alex_Johansen on 2014-10-29
[COLOR=#ff0000]**[SOLVED]**[/COLOR] sudo rm /etc/fonts/conf.d/10-scale-bitmap-fonts.conf


Steam has been working like a dream for about 6 months, until the steamageddon that happened today.
I've reinstalled it, tried the wine version, purged drivers and steam, and when i install the native steam client from valve it install fine from the software center but then the icon in the bar is totally unresponsive.

I also get this error message: OpenGL GLX context is not using direct rendering, which may cause performance problems.
This is my terminal dump from steam:
Running Steam on ubuntu 14.04 32-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Gtk-Message: Failed to load module "overlay-scrollbar"
Gtk-Message: Failed to load module "unity-gtk-module"
Installing breakpad exception handler for appid(steamwebhelper)/version(20141020140456)
Installing breakpad exception handler for appid(steamwebhelper)/version(1413813896)
[1029/221644:ERROR:nss_util.cc(1018)] Failed to load NSS libraries.
Installing breakpad exception handler for appid(steamwebhelper)/version(20141020140456)
Installing breakpad exception handler for appid(steamwebhelper)/version(1413813896)
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
Installing breakpad exception handler for appid(steam)/version(1413917607)
[1029/221644:ERROR:renderer_main.cc(227)] Running without renderer sandbox
[1029/221644:ERROR:renderer_main.cc(227)] Running without renderer sandbox
Generating new string page texture 12: 48x256, total string texture memory is 49,15 KB
Generating new string page texture 13: 256x256, total string texture memory is 311,30 KB
Generating new string page texture 14: 128x256, total string texture memory is 442,37 KB
Generating new string page texture 15: 384x256, total string texture memory is 835,58 KB
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig error: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 70: non-double matrix element
Fontconfig warning: "/etc/fonts/conf.d/10-scale-bitmap-fonts.conf", line 78: saw unknown, expected number


[IMG]http://s11.postimg.org/gf8qjnirn/rsz_screenshot_from_2014_10_29_174852.png[/IMG]
It freezes here on the rare occasions that i make it this far as well.

---

### Post by Alex_Johansen on 2014-10-30
Has been solved, can be locked or something (Y)

---

