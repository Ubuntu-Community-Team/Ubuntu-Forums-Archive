---
title: "Uninstalling CF completely the safe and effective way?"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by vortex_noob on 2007-08-27
Hi,

I tried removing Compiz-Fusion a few times over but still after these steps were done and do a re-install, CF still wont work. Can't seem to find any error in terminal when using "compiz --replace" command. Trevino's repos worked the first time (v.0.5.1) but after an update, all went down the drain. Then I tried compiling using ElemonGW's script but a few plugin i.e. scale, ring-switcher, and some others refuse to work so i uninstalled again.

Then  I installed trevino's latest update, ran it through the terminal "compiz --replace" but nothing happens, and no error in the terminal. Weird.

Emerald also refused to work at all using "emerald --replace" command. 

In my frustration, i type this in the terminal

"locate compiz"

these came up:

ferry@ferry-6400via880:~$ locate compiz
/var/lib/dpkg/info/libcompizconfig0.postrm
/var/lib/dpkg/info/compiz-gtk.list
/var/lib/dpkg/info/compiz-gnome.list
/var/lib/dpkg/info/compiz-gnome.postrm
/var/lib/dpkg/info/compiz-gtk.postrm
/var/lib/dpkg/info/libcompizconfig0.list
/var/crash/_usr_bin_compiz.real.1000.crash
/var/cache/apt/archives/compiz-dev_1%3a0.5.5~git20070824+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-gnome_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
/var/cache/apt/archives/libcompizconfig-backend-gconf_0.1+git20070710~3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-core_1%3a0.5.3~git20070817+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-core_1%3a0.5.5~git20070824+3v1ubuntu0_i386.deb
/var/cache/apt/archives/libcompizconfig-backend-gconf_0.5.2~git20070821+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compizconfig-settings-manager_0.1.0+git20070729~3v1ubuntu1_i386.deb
/var/cache/apt/archives/libcompizconfig0_0.5.2~git 20070824+3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-main_0.5.2~git20070818+3v1ubuntu0_i386.deb
/var/cache/apt/archives/libcompizconfig0_0.0.1+git 20070728~3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-core_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
/var/cache/apt/archives/python-compizconfig_0.5.2~git20070818+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.5.3~git20070817+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.0.1+git20070730~3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-unsupported_0.5.2~git20070822+3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.5.2~git20070817+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz_1%3a0.5.1+git200707 30~3v1ubuntu0_all.deb
/var/cache/apt/archives/libcompizconfig0_0.5.2~git 20070814+3v1ubuntu0_i386.deb
/var/cache/apt/archives/python-compizconfig_0.5.2~git20070824+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
/var/cache/apt/archives/python-compizconfig_0.1.0+git20070617~3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz_1%3a0.5.5~git200708 24+3v1ubuntu0_all.deb
/var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070731~3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz_1%3a0.5.3~git200708 17+3v1ubuntu0_all.deb
/var/cache/apt/archives/compiz-dev_1%3a0.5.3~git20070817+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070824+3v1ubuntu0_i386.deb
/var/cache/apt/archives/libcompizconfig0-dev_0.5.2~git20070824+3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-gnome_1%3a0.5.3~git20070817+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-dev_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
/var/cache/apt/archives/libcompizconfig-backend-gconf_0.5.2~git20070814+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.5.5~git20070824+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compizconfig-settings-manager_0.5.2~git20070818+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.5.2~git20070823+3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-main_0.0.1+git20070730~3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-bcop_0.6.99~git20070820+3v1ubuntu0_i386.deb
/etc/compizconfig
/etc/compizconfig/config
/home/ferry/.gnome2/panel2.d/default/launchers/com piz-1.desktop
/home/ferry/.gnome2/panel2.d/default/launchers/com piz.desktop
/home/ferry/PDF/Compiz_Fusion/TechBlog_-_How_to__Enable_compiz-fusion_in_Ubuntu_Feisty.pdf
/home/ferry/PDF/Compiz_Fusion/Ubuntu_Forums_-_No_window_borders_with_compiz_fusion_____I_m_goin g_crazy.pdf
/home/ferry/Downloads/backup_compiz_bin
/home/ferry/Downloads/backup_compiz_bin/compiz.bac kup
/home/ferry/test_compiz_profile-1
/home/ferry/.config/compiz
/home/ferry/.config/compiz/compizconfig
/home/ferry/.config/compiz/compizconfig/Default.in i
/home/ferry/.config/compiz/compizconfig/config
/usr/lib/window-manager-settings/libcompiz.a
/usr/lib/window-manager-settings/libcompiz.so
/usr/lib/window-manager-settings/libcompiz.la
/usr/include/compiz
/usr/include/compiz/decoration.h
/usr/local/lib/compizconfig
/usr/local/lib/compizconfig/backends
/usr/local/lib/pkgconfig/compiz-scale.pc
/usr/local/lib/pkgconfig/compiz.pc
/usr/local/lib/pkgconfig/compiz-cube.pc
/usr/local/lib/pkgconfig/compiz-gconf.pc
/usr/local/lib/compiz
/usr/local/lib/compiz/libzoom.la
/usr/local/lib/compiz/libscale.so
/usr/local/lib/compiz/libpng.a
/usr/local/lib/compiz/libclone.so
/usr/local/lib/compiz/libwobbly.a
/usr/local/lib/compiz/librotate.a
/usr/local/lib/compiz/libcube.a
/usr/local/lib/compiz/libdecoration.la
/usr/local/lib/compiz/libini.so
/usr/local/lib/compiz/libinotify.a
/usr/local/lib/compiz/libwobbly.la
/usr/local/lib/compiz/libdbus.a
/usr/local/lib/compiz/libscreenshot.a
/usr/local/lib/compiz/libplace.a
/usr/local/lib/compiz/libannotate.so
/usr/local/lib/compiz/libglib.so
/usr/local/lib/compiz/libminimize.a
/usr/local/lib/compiz/libfade.so
/usr/local/lib/compiz/libzoom.so
/usr/local/lib/compiz/libplane.la
/usr/local/lib/compiz/libzoom.a
/usr/local/lib/compiz/libpng.la
/usr/local/lib/compiz/libmove.la
/usr/local/lib/compiz/libfs.a
/usr/local/lib/compiz/libfs.so
/usr/local/lib/compiz/libscreenshot.so
/usr/local/lib/compiz/libglib.a
/usr/local/lib/compiz/libdbus.so
/usr/local/lib/compiz/libscreenshot.la
/usr/local/lib/compiz/libswitcher.a
/usr/local/lib/compiz/libglib.la
/usr/local/lib/compiz/libregex.so
/usr/local/lib/compiz/libregex.a
/usr/local/lib/compiz/libvideo.a
/usr/local/lib/compiz/libsvg.a
/usr/local/lib/compiz/libblur.la
/usr/local/lib/compiz/libgconf.a
/usr/local/lib/compiz/libswitcher.la
/usr/local/lib/compiz/libfade.la
/usr/local/lib/compiz/libdecoration.so
/usr/local/lib/compiz/libinotify.la
/usr/local/lib/compiz/libregex.la
/usr/local/lib/compiz/libblur.a
/usr/local/lib/compiz/libpng.so
/usr/local/lib/compiz/libscale.a
/usr/local/lib/compiz/libresize.so
/usr/local/lib/compiz/libdecoration.a
/usr/local/lib/compiz/libminimize.la
/usr/local/lib/compiz/libclone.la
/usr/local/lib/compiz/libvideo.so
/usr/local/lib/compiz/libplane.so
/usr/local/lib/compiz/libblur.so
/usr/local/lib/compiz/libini.a
/usr/local/lib/compiz/libwobbly.so
/usr/local/lib/compiz/libswitcher.so
/usr/local/lib/compiz/libgconf.la
/usr/local/lib/compiz/libwater.a
/usr/local/lib/compiz/libfs.la
/usr/local/lib/compiz/libclone.a
/usr/local/lib/compiz/libplace.so
/usr/local/lib/compiz/libannotate.la
/usr/local/lib/compiz/librotate.so
/usr/local/lib/compiz/libini.la
/usr/local/lib/compiz/libmove.a
/usr/local/lib/compiz/librotate.la
/usr/local/lib/compiz/libinotify.so
/usr/local/lib/compiz/libcube.so
/usr/local/lib/compiz/libplace.la
/usr/local/lib/compiz/libsvg.la
/usr/local/lib/compiz/libvideo.la
/usr/local/lib/compiz/libscale.la
/usr/local/lib/compiz/libminimize.so
/usr/local/lib/compiz/libwater.la
/usr/local/lib/compiz/libfade.a
/usr/local/lib/compiz/libresize.a
/usr/local/lib/compiz/libwater.so
/usr/local/lib/compiz/libresize.la
/usr/local/lib/compiz/libsvg.so
/usr/local/lib/compiz/libdbus.la
/usr/local/lib/compiz/libgconf.so
/usr/local/lib/compiz/libcube.la
/usr/local/lib/compiz/libannotate.a
/usr/local/lib/compiz/libmove.so
/usr/local/lib/compiz/libplane.a
/usr/local/include/compizconfig
/usr/local/include/compiz
/usr/local/include/compiz/cube.h
/usr/local/include/compiz/compiz.h
/usr/local/include/compiz/decoration.h
/usr/local/include/compiz/scale.h
/usr/local/share/locale/ja/LC_MESSAGES/compiz.mo
/usr/local/share/locale/xh/LC_MESSAGES/compiz.mo
/usr/local/share/locale/vi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cy/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/he/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_TW/LC_MESSAGES/compiz.m o
/usr/local/share/locale/zh_CN/LC_MESSAGES/compiz.m o
/usr/local/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/compiz.m o
/usr/local/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/compiz.m o
/usr/local/share/locale/ko/LC_MESSAGES/compiz.mo
/usr/local/share/locale/uk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/km/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ro/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/it/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ru/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt/LC_MESSAGES/compiz.mo
/usr/local/share/locale/da/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bg/LC_MESSAGES/compiz.mo
/usr/local/share/locale/cs/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ka/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/et/LC_MESSAGES/compiz.mo
/usr/local/share/locale/bn/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/id/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/de/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sl/LC_MESSAGES/compiz.mo
/usr/local/share/locale/fi/LC_MESSAGES/compiz.mo
/usr/local/share/locale/mk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/es/LC_MESSAGES/compiz.mo
/usr/local/share/locale/nb/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sk/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lo/LC_MESSAGES/compiz.mo
/usr/local/share/locale/hr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ca/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ta/LC_MESSAGES/compiz.mo
/usr/local/share/locale/af/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pa/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_US/LC_MESSAGES/compiz.m o
/usr/local/share/locale/el/LC_MESSAGES/compiz.mo
/usr/local/share/locale/tr/LC_MESSAGES/compiz.mo
/usr/local/share/locale/gu/LC_MESSAGES/compiz.mo
/usr/local/share/locale/lt/LC_MESSAGES/compiz.mo
/usr/local/share/compizconfig
/usr/local/share/compiz
/usr/local/share/compiz/water.xml
/usr/local/share/compiz/decoration.xml
/usr/local/share/compiz/dbus.xml
/usr/local/share/compiz/rotate.xml
/usr/local/share/compiz/annotate.xml
/usr/local/share/compiz/fade.xml
/usr/local/share/compiz/icon.png
/usr/local/share/compiz/inotify.xml
/usr/local/share/compiz/kconfig.xml
/usr/local/share/compiz/scale.xml
/usr/local/share/compiz/screenshot.xml
/usr/local/share/compiz/minimize.xml
/usr/local/share/compiz/png.xml
/usr/local/share/compiz/cube.xml
/usr/local/share/compiz/schemas.xslt
/usr/local/share/compiz/freedesktop.png
/usr/local/share/compiz/core.xml
/usr/local/share/compiz/glib.xml
/usr/local/share/compiz/blur.xml
/usr/local/share/compiz/wobbly.xml
/usr/local/share/compiz/resize.xml
/usr/local/share/compiz/regex.xml
/usr/local/share/compiz/zoom.xml
/usr/local/share/compiz/switcher.xml
/usr/local/share/compiz/clone.xml
/usr/local/share/compiz/gconf.xml
/usr/local/share/compiz/place.xml
/usr/local/share/compiz/fs.xml
/usr/local/share/compiz/svg.xml
/usr/local/share/compiz/ini.xml
/usr/local/share/compiz/plane.xml
/usr/local/share/compiz/move.xml
/usr/local/share/compiz/video.xml
/usr/local/etc/compizconfig
/usr/local/etc/gconf/schemas/compiz-inotify.schemas
/usr/local/etc/gconf/schemas/compiz-switcher.schemas
/usr/local/etc/gconf/schemas/compiz-move.schemas
/usr/local/etc/gconf/schemas/compiz-place.schemas
/usr/local/etc/gconf/schemas/compiz-gconf.schemas
/usr/local/etc/gconf/schemas/compiz-resize.schemas
/usr/local/etc/gconf/schemas/compiz-decoration.schemas
/usr/local/etc/gconf/schemas/compiz-minimize.schemas
/usr/local/etc/gconf/schemas/compiz-kconfig.schemas
/usr/local/etc/gconf/schemas/compiz-dbus.schemas
/usr/local/etc/gconf/schemas/compiz-plane.schemas
/usr/local/etc/gconf/schemas/compiz-ini.schemas
/usr/local/etc/gconf/schemas/compiz-svg.schemas
/usr/local/etc/gconf/schemas/compiz-regex.schemas
/usr/local/etc/gconf/schemas/compiz-water.schemas
/usr/local/etc/gconf/schemas/compiz-cube.schemas
/usr/local/etc/gconf/schemas/compiz-screenshot.schemas
/usr/local/etc/gconf/schemas/compiz-glib.schemas
/usr/local/etc/gconf/schemas/compiz-wobbly.schemas
/usr/local/etc/gconf/schemas/compiz-core.schemas
/usr/local/etc/gconf/schemas/compiz-video.schemas
/usr/local/etc/gconf/schemas/compiz-fs.schemas
/usr/local/etc/gconf/schemas/compiz-rotate.schemas
/usr/local/etc/gconf/schemas/compiz-clone.schemas
/usr/local/etc/gconf/schemas/compiz-png.schemas
/usr/local/etc/gconf/schemas/compiz-zoom.schemas
/usr/local/etc/gconf/schemas/compiz-blur.schemas
/usr/local/etc/gconf/schemas/compiz-fade.schemas
/usr/local/etc/gconf/schemas/compiz-annotate.schemas
/usr/local/etc/gconf/schemas/compiz-scale.schemas
/usr/local/bin/compiz
/usr/share/locale-langpack/en_GB/LC_MESSAGES/compiz.mo
/usr/share/locale-langpack/id/LC_MESSAGES/compiz.mo
/usr/share/app-install/desktop/gnome-compiz-preferences.desktop
/usr/share/app-install/icons/_usr_share_gnome-compiz-manager_gnome-compiz-manager.png
/usr/bin/compiz~

Will it be safe for my system as a whole (no breakage please) if i remove these files? (Aside from the .deb, .pdf and the .png files of course ). I want to have a clean slate for CF re-installation. After trying it, I'm already addicted and computing without it feels so prehistoric :lolflag:

---

### Post by praet on 2007-08-28
Following this guide should remove compiz properly.  I recommend reinstalling with amaranth's repos.

[http://ubuntuforums.org/showthread.php?t=533476](http://ubuntuforums.org/showthread.php?t=533476)

---

### Post by Inxsible on 2007-08-28
Try [this]("http://ubuntuforums.org/showthread.php?t=533201") to remove Compiz Fusion completely. You can then install it again, using any repo you like.

---

### Post by vortex_noob on 2007-08-29
thanks for the replies, dudes...

Inxsible, i tried the steps that u outlined in the thread that u made but the files that i found using "locate compiz" still exist and i still can't use the repos from trevino nor the CF_Installer_Updater afterwards. Trevino's does nothing at all after install with no error in terminal while the compile script managed to make CF work with malfunctioned plugins like i mentioned earlier.

My question is should i delete all these files related to compiz that i found in my system without breaking the system? (I've had a couple fresh install after automatix managed to break my ubuntu edgy system).
No more automatix for me till the experts from this forum validate its use :)

---

### Post by Inxsible on 2007-08-29
> **vortex_noob said:**
> thanks for the replies, dudes...

Inxsible, i tried the steps that u outlined in the thread that u made but the files that i found using "locate compiz" still exist and i still can't use the repos from trevino nor the CF_Installer_Updater afterwards. Trevino's does nothing at all after install with no error in terminal while the compile script managed to make CF work with malfunctioned plugins like i mentioned earlier.

My question is should i delete all these files related to compiz that i found in my system without breaking the system? (I've had a couple fresh install after automatix managed to break my ubuntu edgy system).
No more automatix for me till the experts from this forum validate its use :)

I am not a big fan of automatix either. It has created more problems for me than solved anything. When you are a noob, you want every help that you can get, which Automatix says it will provide, but you are really left hanging if something doesn't work. Its better to know what you are doing yourself.

But hey, some people swear by it. So I can't really say for them :)

For you Compiz problem, did you try the commands that I gave. I didnt use the "locate" command. I simulate the uninstall and then manually remove all the compiz related packages.

---

### Post by vortex_noob on 2007-08-29
yes i did man... every steps that u outlined.

I typed "locate compiz" after i did ur steps and tried installing trevino's repos and it CF refused to work without saying any error in the terminal. So I uninstalled them again and did ur steps again. U might say that i was trying to hunt down every last remnants of CF in my system so i can install CF again in a clean slate.

Any thoughts why this is happening? And would it be safe to remove these files that i found relating to CF? Thanks again for trying to help me with these annoyances, man! :)

---

