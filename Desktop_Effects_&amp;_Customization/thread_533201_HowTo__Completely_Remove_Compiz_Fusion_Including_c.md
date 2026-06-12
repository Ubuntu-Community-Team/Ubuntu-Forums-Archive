---
title: "HowTo : Completely Remove Compiz Fusion Including config files for a clean re-install"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by Inxsible on 2007-08-23
A lot of people experienced the headaches associated with updates to Compiz Fusion no matter what repos they were using.

Here's how I removed every trace of CF and then installed using Trevino's repos and I now have everything working( except the Shift switcher plugin :( )

Open a terminal and do a 
[COLOR=Red]EDIT: Thanks to corney91, I added a -s option to the command so it simply simulates the command rather than executing it. That way you dont have to Abort any commands[/COLOR]

```
 sudo apt-get remove --purge compiz* libcompizconfig* -s
```This will spit out a bunch of selected packages for the regex compiz* and libcompizconfig* 

[COLOR=Red]This is now defunct : Now ABORT this un-install, because even though it selects all the packages, they are not removed for some reason.[/COLOR]

Then remove all the packages that have a "compiz" in them.
The next command has all the packages that were on my system, so if you have the same packages, then you can skip the earlier step and simply copy paste this one

```
 sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
```[COLOR=Red]Note : Please make sure you dont have any additional packages.[/COLOR] Thats why I listed the first step so you can check.

After removing all those packages, backup /home/*<your username>*/.compizconfig and /home/*<your username>*/.config/compiz and /home/*<your username>*.gconf/apps/compiz  to some other location just in case.(your desktop for eg) and then delete them from the /home/*<your username>* folder

Now you have a clean system ready for installation of CF. I used Trevino's repos and almost everything works. You can use other repos if you know they work. :)

This certainly helped me. I hope it helps you guys too :popcorn:

---

### Post by luckyd on 2007-08-24
it didnt help me with the enhanced zoom, does it work for you?

---

### Post by bigbrovar on 2007-08-24
it worked !!! it worked!!! i did everything u recommended and enable trevino's repo..installed compiz and all the plugins and guess what.....:guitar:

---

### Post by bricksen on 2007-08-24
I used the CF_Installer-Updater_v.3.sh to install and it didn't work out and when I try to uninstall I get this return? Can't remember any messages while I installed it?

bricksen@bricksen:~$ sudo apt-get remove --purge compiz* libcompizconfig*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libgnome-compiz-manager0 for regex 'compiz*'
Note, selecting compiz-extra for regex 'compiz*'
Note, selecting libcompizconfig0 for regex 'compiz*'
Note, selecting ocaml-native-compilers for regex 'compiz*'
Note, selecting zinc-compiler for regex 'compiz*'
Note, selecting compiz-dev for regex 'compiz*'
Note, selecting lisp-compiler for regex 'compiz*'
Note, selecting compiz-gtk for regex 'compiz*'
Note, selecting compiz-kde for regex 'compiz*'
Note, selecting libsnmp-mib-compiler-perl for regex 'compiz*'
Note, selecting compiz-settings for regex 'compiz*'
Note, selecting libcompizconfig-backend-gconf for regex 'compiz*'
Note, selecting compiz-config-ini for regex 'compiz*'
Note, selecting c-compiler-avr for regex 'compiz*'
Note, selecting gcc-avr instead of c-compiler-avr
Note, selecting gcompizthemer for regex 'compiz*'
Note, selecting haskell-compiler for regex 'compiz*'
Note, selecting ghc6 instead of haskell-compiler
Note, selecting c-compiler for regex 'compiz*'
Note, selecting fortran-compiler for regex 'compiz*'
Note, selecting compiz-plugins for regex 'compiz*'
Note, selecting libgnome-compiz-manager-dev for regex 'compiz*'
Note, selecting chill-compiler for regex 'compiz*'
Note, selecting chill-2.95 instead of chill-compiler
Note, selecting compilercache for regex 'compiz*'
Note, selecting compizconfig-backend-kde for regex 'compiz*'
Note, selecting c-sharp-2.0-compiler for regex 'compiz*'
Note, selecting mono-gmcs instead of c-sharp-2.0-compiler
Note, selecting compizconfig-settings-manager for regex 'compiz*'
Note, selecting ocaml-compiler-libs-3.09.2 for regex 'compiz*'
Note, selecting ocaml-compiler-libs instead of ocaml-compiler-libs-3.09.2
Note, selecting python-compizconfig for regex 'compiz*'
Note, selecting ocaml-best-compilers for regex 'compiz*'
Note, selecting ocaml-native-compilers instead of ocaml-best-compilers
Note, selecting objc++-compiler for regex 'compiz*'
Note, selecting compiz-config-gnome for regex 'compiz*'
Note, selecting taskbar-compiz for regex 'compiz*'
Note, selecting compizconfig-plugin for regex 'compiz*'
Note, selecting compiz-freedesktop-dev for regex 'compiz*'
Note, selecting compiz-fusion-plugins-unofficial for regex 'compiz*'
Note, selecting fortran95-compiler for regex 'compiz*'
Note, selecting gfortran-4.1 instead of fortran95-compiler
Note, selecting pnet-compiler for regex 'compiz*'
Note, selecting c-sharp-compiler for regex 'compiz*'
Note, selecting objc-compiler for regex 'compiz*'
Note, selecting compiz-bcop for regex 'compiz*'
Note, selecting java-compiler for regex 'compiz*'
Note, selecting compiz-ccs-settings-manager for regex 'compiz*'
Note, selecting pascal-compiler for regex 'compiz*'
Note, selecting java2-compiler for regex 'compiz*'
Note, selecting libgnome-compiz-manager for regex 'compiz*'
Note, selecting c++-compiler for regex 'compiz*'
Note, selecting libcompizconfig0-dev for regex 'compiz*'
Note, selecting compizconfig-settings-legacy for regex 'compiz*'
Note, selecting compiz-fusion-plugins-extra for regex 'compiz*'
Note, selecting fp-compiler for regex 'compiz*'
Note, selecting compiz-compcomm-plugins-main for regex 'compiz*'
Note, selecting compiz-fusion-plugins-unsupported for regex 'compiz*'
Note, selecting compiz for regex 'compiz*'
Note, selecting compiz-extra-plugins for regex 'compiz*'
Note, selecting compiz-fusion-plugins-main instead of compiz-extra-plugins
Note, selecting libcompizconfig-backend-kconfig for regex 'compiz*'
Note, selecting ada-compiler for regex 'compiz*'
Note, selecting gnat-4.1 instead of ada-compiler
Note, selecting compiz-core for regex 'compiz*'
Note, selecting compiz-decorator for regex 'compiz*'
Note, selecting gnome-compiz-manager for regex 'compiz*'
Note, selecting compiz-fusion-plugins-main for regex 'compiz*'
Note, selecting c-compiler-m68hc11 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc11
Note, selecting c-compiler-m68hc12 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc12
Note, selecting compizconfig-backend-gnome for regex 'compiz*'
Note, selecting ocaml-compiler-libs for regex 'compiz*'
Note, selecting fortran77-compiler for regex 'compiz*'
Note, selecting compiz-gnome for regex 'compiz*'
Note, selecting libcompizconfig-dev for regex 'compiz*'
Note, selecting libgnome-compiz-manager0-dev for regex 'compiz*'
E: Couldn't find package compiz*
bricksen@bricksen:~$ 

I tried your command and it returned this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Note: selecting "emerald" instead of the
      virtual package "gcompizthemer"
Couldn't find any package whose name or description matched "compiztools"
Note: selecting "compiz-fusion-plugins-main" instead of the
      virtual package "compiz-extra-plugins"
"compiz-decorator" is a virtual package provided by:
  compiz-gnome compiz-kde 
You must choose one to install.
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

How can this be. All the directories are there except kde stuff cause i use gnome?
I really need to get rid of all the stuff from my resently failure install.

---

### Post by corney91 on 2007-08-24
Thanks for the howto, I've been struggling with the update for days.

Instead of cancelling the first command, I would assume simulating it would be safer:```
sudo apt-get remove --purge compiz* libcompizconfig* -s
```

And then to reinstall all plugins I ran ```
sudo apt-get install compiz-fusion* libcompizconfig0 compizconfig-settings-manager libcompizconfig-backend-gconf
```

---

### Post by vortex_noob on 2007-08-26
Hi,

I tried removinh CF a few times over but still after these steps were done and do a re-install, CF still wont work. Can't seem to find any error in terminal when using "compiz --replace" command.

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
/var/cache/apt/archives/libcompizconfig0_0.5.2~git20070824+3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-main_0.5.2~git20070818+3v1ubuntu0_i386.deb
/var/cache/apt/archives/libcompizconfig0_0.0.1+git20070728~3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-core_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
/var/cache/apt/archives/python-compizconfig_0.5.2~git20070818+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.5.3~git20070817+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.0.1+git20070730~3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-unsupported_0.5.2~git20070822+3v1ubuntu1_i386.deb
/var/cache/apt/archives/compiz-fusion-plugins-extra_0.5.2~git20070817+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz_1%3a0.5.1+git20070730~3v1ubuntu0_all.deb
/var/cache/apt/archives/libcompizconfig0_0.5.2~git20070814+3v1ubuntu0_i386.deb
/var/cache/apt/archives/python-compizconfig_0.5.2~git20070824+3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz-plugins_1%3a0.5.1+git20070730~3v1ubuntu0_i386.deb
/var/cache/apt/archives/python-compizconfig_0.1.0+git20070617~3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz_1%3a0.5.5~git20070824+3v1ubuntu0_all.deb
/var/cache/apt/archives/compiz-fusion-plugins-unofficial_0.0.1+git20070731~3v1ubuntu0_i386.deb
/var/cache/apt/archives/compiz_1%3a0.5.3~git20070817+3v1ubuntu0_all.deb
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
/home/ferry/.gnome2/panel2.d/default/launchers/compiz-1.desktop
/home/ferry/.gnome2/panel2.d/default/launchers/compiz.desktop
/home/ferry/PDF/Compiz_Fusion/TechBlog_-_How_to__Enable_compiz-fusion_in_Ubuntu_Feisty.pdf
/home/ferry/PDF/Compiz_Fusion/Ubuntu_Forums_-_No_window_borders_with_compiz_fusion_____I_m_going_crazy.pdf
/home/ferry/Downloads/backup_compiz_bin
/home/ferry/Downloads/backup_compiz_bin/compiz.backup
/home/ferry/test_compiz_profile-1
/home/ferry/.config/compiz
/home/ferry/.config/compiz/compizconfig
/home/ferry/.config/compiz/compizconfig/Default.ini
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
/usr/local/share/locale/zh_TW/LC_MESSAGES/compiz.mo
/usr/local/share/locale/zh_CN/LC_MESSAGES/compiz.mo
/usr/local/share/locale/sv/LC_MESSAGES/compiz.mo
/usr/local/share/locale/en_GB/LC_MESSAGES/compiz.mo
/usr/local/share/locale/ar/LC_MESSAGES/compiz.mo
/usr/local/share/locale/pt_BR/LC_MESSAGES/compiz.mo
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
/usr/local/share/locale/en_US/LC_MESSAGES/compiz.mo
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

Will it be safe for my system as a whole (no breakage please) if i remove these files? (Aside from the .deb, .pdf and the .png files of course :)  )

---

### Post by sdowney717 on 2007-08-26
I simply hit the reset to defaults button and it started working.
Might try that before uninstalling.

---

### Post by shantzg001 on 2007-08-26
I cant seem to find the "reset to defaults" button in ccsm. When I open any particular option within it for a plugin, i can see the reset button for a particular option for that plugin but cant find an "overall" reset to defaults button.

---

### Post by sdowney717 on 2007-08-26
it is under preferences or something right on the main page

there are 2 items at the bottom left panel on the main page and one of them takes you to it.

---

### Post by Prowler_1 on 2007-08-28
WOW it works now

and the strange thing is that it work after i turnd ATI's
Restricted Driver Manager off!

(Error: Couldn't activate plugin 'ccp'
ABI version 20070708 and actual version is 20070815)

Thanks.
:popcorn:

---

### Post by Sunflower1970 on 2007-08-28
I've done this on two computers so far...

Is it me, or does it run much faster now...?

---

### Post by ayoli on 2007-08-28
wow, this thread just fixed a freeze problem after compiz-fusion upgrade, and also seems to run smoother for me :)
edit: a quick note, i also use the simulate option for the first step (as suggested few posts above) which is a better way than hit CTRL+C
```
 sudo apt-get remove --purge compiz* libcompizconfig* -s
```

---

### Post by Hyperkill on 2007-08-28
To those having problems with CF_Installer-Updater and having a huge list of things to remove (half of which you shouldn't be removing such as your compilers) please do these steps as it just worked for me.

Go into Synaptic Package Manager and do a search for compiz.  Remove everything that has a green checkbox by it.

Now, go to this site:  
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

Follow all of the instructions and you should be all set.  Also, I was a little weary of uninstalling desktop effects (which are installed by ubuntu by default) but my system is up and running great right now and I got all kinds of cool effects.  Enjoy.

---

### Post by Inxsible on 2007-08-28
I like what corney91 suggested and I have now updated my command to reflect his idea of simulating it :)

---

### Post by ayoli on 2007-08-28
> **Inxsible said:**
> I like what corney91 suggested and I have now updated my command to reflect his idea of simulating it :)
good idea :) you may also want to update/delete  this :
> Now ABORT this un-install, because even though it selects all the packages, they are not removed for some reason.
cheers.

---

### Post by Inxsible on 2007-08-28
> **ayoli said:**
> good idea :) you may also want to update/delete  this :

cheers.
I changed the font color, so everyone would know I goofed up initially and then rectified it when corney91 told me :D

---

### Post by ayoli on 2007-08-28
> **Inxsible said:**
> I changed the font color, so everyone would know I goofed up initially and then rectified it when corney91 told me :D

lol, that's a way :D

---

### Post by open2linux on 2007-08-30
> **Inxsible said:**
> This will spit out a bunch of selected packages for the regex compiz* and libcompizconfig* 

Could you please elaborate a bit on this "regex" for a beginner ?

I have exactly this problem, trying to clean previous (failed) installations of compiz.
After running the command you recomend, I get the list of the files related to compiz, now, how to get rid of them?

Thanks a lot in advance !!

---

### Post by ayoli on 2007-08-30
> **open2linux said:**
> Could you please elaborate a bit on this "regex" for a beginner ?

regex means "regular expression" ie: compiz* means all words (packages names in this case which begin with compiz
> **open2linux said:**
> 
I have exactly this problem, trying to clean previous (failed) installations of compiz.
After running the command you recomend, I get the list of the files related to compiz, now, how to get rid of them?

Thanks a lot in advance !!

to get rid of them in a terminal type :
```
sudo aptitude remove <list here all compiz related packages name you find>
```
then:
> After removing all those packages, backup  /home/<your username>/.compizconfig and /home/<your username>/.config/compiz and /home/<your username>.gconf/apps/compiz to some other location just in case.(your desktop for eg)
I recommend to also delete these config after backup.
Then you can do a fresh and clean install.

---

### Post by open2linux on 2007-08-31
Thanks a lot, now I got it.

One more thing I dont understand very well:
Why to make backup of those config files of compiz?
You also recomend to delete those files after backing them up.
Then what for backing them up?
Are not them created again for the fresh install?

Excuse me if this is something very obvious for you.
I do not have much experience with Linux.

---

### Post by Inxsible on 2007-08-31
> **open2linux said:**
> Thanks a lot, now I got it.

One more thing I dont understand very well:
Why to make backup of those config files of compiz?
You also recomend to delete those files after backing them up.
Then what for backing them up?
Are not them created again for the fresh install?

Excuse me if this is something very obvious for you.
I do not have much experience with Linux.It is always a good practice to backup something before deleting it. This helps if and when something goes really wrong with your installation. After you install something and everything works properly, you can go ahead and delete the backups you have made, if you so wish.

---

### Post by open2linux on 2007-08-31
> **Inxsible said:**
> It is always a good practice to backup something before deleting it. This helps if and when something goes really wrong with your installation. After you install something and everything works properly, you can go ahead and delete the backups you have made, if you so wish.

Sounds like a good advice.
Thanks again.

---

### Post by open2linux on 2007-08-31
I don't understand what I am doing wrong, but I cannot delete the compiz files.

After running the command
> sudo apt-get remove --purge compiz* libcompizconfig* -s


I get this list:

> Reading package lists... DoneBuilding dependency tree       Reading state information... Done
Note, selecting libgnome-compiz-manager0 for regex 'compiz*'
Note, selecting compiz-extra for regex 'compiz*'
Note, selecting ocaml-native-compilers for regex 'compiz*'
Note, selecting zinc-compiler for regex 'compiz*'
Note, selecting compiz-dev for regex 'compiz*'
Note, selecting lisp-compiler for regex 'compiz*'
Note, selecting compiz-gtk for regex 'compiz*'
Note, selecting compiz-kde for regex 'compiz*'
Note, selecting libsnmp-mib-compiler-perl for regex 'compiz*'
Note, selecting c-compiler-avr for regex 'compiz*'
Note, selecting gcc-avr instead of c-compiler-avr
Note, selecting gcompizthemer for regex 'compiz*'
Note, selecting emerald instead of gcompizthemer
Note, selecting haskell-compiler for regex 'compiz*'
Note, selecting ghc6 instead of haskell-compiler
Note, selecting c-compiler for regex 'compiz*'
Note, selecting fortran-compiler for regex 'compiz*'
Note, selecting compiz-plugins for regex 'compiz*'
Note, selecting libgnome-compiz-manager-dev for regex 'compiz*'
Note, selecting chill-compiler for regex 'compiz*'
Note, selecting chill-2.95 instead of chill-compiler
Note, selecting compilercache for regex 'compiz*'
Note, selecting c-sharp-2.0-compiler for regex 'compiz*'
Note, selecting mono-gmcs instead of c-sharp-2.0-compiler
Note, selecting ocaml-compiler-libs-3.09.2 for regex 'compiz*'
Note, selecting ocaml-compiler-libs instead of ocaml-compiler-libs-3.09.2
Note, selecting ocaml-best-compilers for regex 'compiz*'
Note, selecting ocaml-native-compilers instead of ocaml-best-compilers
Note, selecting objc++-compiler for regex 'compiz*'
Note, selecting fortran95-compiler for regex 'compiz*'
Note, selecting gfortran-4.1 instead of fortran95-compiler
Note, selecting pnet-compiler for regex 'compiz*'
Note, selecting c-sharp-compiler for regex 'compiz*'
Note, selecting objc-compiler for regex 'compiz*'
Note, selecting java-compiler for regex 'compiz*'
Note, selecting pascal-compiler for regex 'compiz*'
Note, selecting java2-compiler for regex 'compiz*'
Note, selecting libgnome-compiz-manager for regex 'compiz*'
Note, selecting c++-compiler for regex 'compiz*'
Note, selecting fp-compiler for regex 'compiz*'
Note, selecting compiz for regex 'compiz*'
Note, selecting ada-compiler for regex 'compiz*'
Note, selecting gnat-4.1 instead of ada-compiler
Note, selecting compiz-core for regex 'compiz*'
Note, selecting gnome-compiz-manager for regex 'compiz*'
Note, selecting c-compiler-m68hc11 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc11
Note, selecting c-compiler-m68hc12 for regex 'compiz*'
Note, selecting gcc-m68hc1x instead of c-compiler-m68hc12
Note, selecting ocaml-compiler-libs for regex 'compiz*'
Note, selecting fortran77-compiler for regex 'compiz*'
Note, selecting compiz-gnome for regex 'compiz*'
Note, selecting libgnome-compiz-manager0-dev for regex 'compiz*'

Then I compile all files that contains compiz and run:

> sudo aptitude remove libgnome-compiz-manager0 compiz-extra compiz-dev compiz-gtk compiz-kde emerald compiz-plugins libgnome-compiz-manager-dev libgnome-compiz-manager compiz compiz-core gnome-compiz-manager compiz-gnome libgnome-compiz-manager0-dev


Then I get this message:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Nothing deleted :(

Any ideas?

---

### Post by Inxsible on 2007-08-31
you are missing gcompizthemer. Apart from that I don't know why it isnt working :(

---

### Post by The Pinny Parlour on 2007-09-01
Darn it   this doesn't remove anything.  I tried it all and I still have an icon for Compiz-Fusion and it still works

Thanks for trying though.

---

### Post by Inxsible on 2007-09-01
> **The Pinny Parlour said:**
> Darn it   this doesn't remove anything.  I tried it all and I still have an icon for Compiz-Fusion and it still works

Thanks for trying though.

did you shut off Compiz Fusion before you removed it ?

Just reboot and see...if you removed the packages like its listed, they will not reload on boot and you should be good to go.

---

### Post by matther22 on 2008-01-08
> **Inxsible said:**
> A lot of people experienced the headaches associated with updates to Compiz Fusion no matter what repos they were using.

Here's how I removed every trace of CF and then installed using Trevino's repos and I now have everything working( except the Shift switcher plugin :( )

Open a terminal and do a 
[COLOR=Red]EDIT: Thanks to corney91, I added a -s option to the command so it simply simulates the command rather than executing it. That way you dont have to Abort any commands[/COLOR]

```
 sudo apt-get remove --purge compiz* libcompizconfig* -s
```This will spit out a bunch of selected packages for the regex compiz* and libcompizconfig* 

[COLOR=Red]This is now defunct : Now ABORT this un-install, because even though it selects all the packages, they are not removed for some reason.[/COLOR]

Then remove all the packages that have a "compiz" in them.
The next command has all the packages that were on my system, so if you have the same packages, then you can skip the earlier step and simply copy paste this one

```
 sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev
```[COLOR=Red]Note : Please make sure you dont have any additional packages.[/COLOR] Thats why I listed the first step so you can check.

After removing all those packages, backup /home/*<your username>*/.compizconfig and /home/*<your username>*/.config/compiz and /home/*<your username>*.gconf/apps/compiz  to some other location just in case.(your desktop for eg) and then delete them from the /home/*<your username>* folder

Now you have a clean system ready for installation of CF. I used Trevino's repos and almost everything works. You can use other repos if you know they work. :)

This certainly helped me. I hope it helps you guys too :popcorn:



How do you use trtevinos repos??

---

### Post by Forlong on 2008-01-08
If you're on Gutsy: you don't.

If you're on Feisty: [http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/index.html](http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/index.html)

---

### Post by TheeMahn2003 on 2008-02-13
> **Forlong said:**
> If you're on Gutsy: you don't.

If you're on Feisty: [http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/index.html](http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/index.html)

Sorry fellas I don't spend much time on this forum, have my own to contend with...
I have had it integrated in [Ultimate Edition]("http://ultimateedition.info/") since 1.6 now at [UE 1.7]("http://www.youtube.com/watch?v=QduOWC37I7Q") 1.6 is gutsy based & had CF.  I also offer ways of getting [additional plugins]("http://forumubuntusoftware.info/viewtopic.php?f=32&t=422") working in it, for those brave enough to take the nestea plunge ;) All hosted on 4 separate servers.  I also host a [repo]("http://repoubuntusoftware.info/") that has compiz fusion, I was somehow left from the list ;)

---

