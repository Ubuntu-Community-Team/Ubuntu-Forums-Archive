---
title: "install DockbarX or alternative taskbar"
date: 2011-04-25
forum: Desktop Environments
---

### Post by Alfons81 on 2011-04-25
Hi all,

I'm running a nice minimal xfce4 installation and I would like to install DockbarX on it. I think it could be a useful taskbar replacement but the problem is that the installation brings some Gnome stuff. 

exists a clean way to install DockbarX witout gnome dependencies?

if not, is that an issue for my pure minimal xfce4? Wich are the consequences?

Is there an alternative taskbar?

Some links I've been looking:

[http://hackoder.com/2010/02/28/getting-windows-7-like-taskbar-hotkeys-in-ubuntu/](http://hackoder.com/2010/02/28/getting-windows-7-like-taskbar-hotkeys-in-ubuntu/)

[http://goodies.xfce.org/projects/panel-plugins/xfce4-taskbar-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-taskbar-plugin)

Thanks in advance! Cheers!

---

### Post by Copper Bezel on 2011-04-25
Just keep track of what installs, just in case, so that you can remove it if necessary. DockBarX shouldn't load any unnecessary Gnome services. Be warned that some Python dependencies have been reported as not being marked as DBX dependencies, probably because they're present in a standard Gnome system and there's relatively little DBX testing done on XFCE, so you might need to do a little searching to get it to run. (I don't know whether these have been marked in the current DBX.)

---

### Post by Krytarik on 2011-04-25
Another thing, since your profile states that you are running 10.04 (like me), if you want to get the current version of DockbarX, see my earlier post:
[http://ubuntuforums.org/showthread.php?p=10449804#post10449804](http://ubuntuforums.org/showthread.php?p=10449804#post10449804)

As for the Python deps, it's package info states a number of Python packages, with at least one pulling in some Gnome packages, but I, of course, don't know if the deps are complete:
```
Depends: python (<< 3.1), python (>= 2.6), python-support (>= 0.90.0), python-wnck, python-gnomeapplet, python-keybinder, python-numpy
```

---

### Post by Copper Bezel on 2011-04-25
Yeah, I finally remembered to look this up, and the package I was thinking of is python-gnome2, so it's not marked.

---

### Post by Alfons81 on 2011-04-25
Hi, Thanks for replies!!!

I installed it...and everything seems ok...but when I try to add DockbarX on the panel it says that cannot launch. After made Xfce4 a bit fatter...:-&

I'm running Debian and I did it like that:

root@alfons:~# aptitude install --without-recommends python-gnomeapplet python-wnck python-keybinder python-numpy zeitgeist xfce4-xfapplet-plugin

Els paquets nous següents s'instal·laran:             
  gnome-mime-data{a} gvfs{a} libart-2.0-2{a} libatasmart4{a} 
  libavahi-glib1{a} libbonobo2-0{a} libbonobo2-common{a} libbonoboui2-0{a} 
  libbonoboui2-common{a} libeggdbus-1-0{a} libgdu0{a} libgnome2-0{a} 
  libgnome2-common{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} 
  libgnomeui-0{a} libgnomeui-common{a} libgnomevfs2-0{a} 
  libgnomevfs2-common{a} libpanel-applet2-0{a} libparted0debian1{a} 
  libpolkit-backend-1-0{a} libpolkit-gobject-1-0{a} libsgutils2-2{a} 
  python-gconf{a} python-gnome2{a} python-gnomeapplet python-pyorbit{a} 
  python-wnck udisks{a} xfce4-xfapplet-plugin zeitgeist zeitgeist-core{a} 
  zeitgeist-datahub{a} 
Els paquets parcialment instal·lats següents es configuraran:
  xfce4-globalmenu-plugin{b} xfce4-panel-menu-plugin{b} 
Els paquets següents són RECOMANATS però NO s'instal·laran:
  dosfstools hdparm libgnomevfs2-extra mtools ntfs-3g ntfsprogs policykit-1 
  policykit-1-gnome 
0 paquets actualitzats, 34 instal·lats, 0 a suprimir i 0 a no actualitzar.
Es necessita obtenir 10,9 MB d'arxius. Després del desempaquetat s'utilitzaran 42,2 MB.
No s'han trobat les dependències del paquets següents:
  xfce4-panel-menu-plugin: Depèn: libdbh1.0-1 que és un paquet virtual.
                           Depèn: libxfce4mcs-client-2 que és un paquet virtual.
                           Depèn: libxfce4mcs-manager-2 que és un paquet virtual.
                           Depèn: libxfce4util-1 (>= 4.2.1-1) que és un paquet virtual.
                           Depèn: libxfcegui4-3 (>= 4.2.1-1) que és un paquet virtual.
  xfce4-globalmenu-plugin: Depèn: libgnomenu0-2 (= 0.7.9-0ubuntu1~ppa1~lucid2) que és un paquet virtual.
                           Depèn: libglobalmenu-gnome (= 0.7.9-0ubuntu1~ppa1~lucid2) que és un paquet virtual.
                           Depèn: gnome-globalmenu-common que és un paquet virtual.
Les accions següents resoldran les dependències:

     Suprimeix els següents paquets:
1)     xfce4-globalmenu-plugin      
2)     xfce4-panel-menu-plugin      

root@alfons:/home/alfons/Escriptori/dockbarx_0.43# ./setup.py install
running install
running build
running build_py
creating build
creating build/lib.linux-x86_64-2.6
creating build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/i18n.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/log.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/zg.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/mediabuttons.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/theme.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/dockbar.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/cairowidgets.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/common.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/dockmanager.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/windowbutton.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/__init__.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/groupbutton.py -> build/lib.linux-x86_64-2.6/dockbarx
copying dockbarx/iconfactory.py -> build/lib.linux-x86_64-2.6/dockbarx
running build_trans
Compiling po/de.po for dockbarx
Compiling po/fr.po for dockbarx
Compiling po/fi.po for dockbarx
Compiling po/cs.po for dockbarx
Compiling po/eu.po for dockbarx
Compiling po/pt.po for dockbarx
Compiling po/ko.po for dockbarx
Compiling po/nl.po for dockbarx
Compiling po/zh_TW.po for dockbarx
Compiling po/uk.po for dockbarx
Compiling po/lt.po for dockbarx
Compiling po/pt_BR.po for dockbarx
Compiling po/pl.po for dockbarx
Compiling po/bg.po for dockbarx
Compiling po/sk.po for dockbarx
Compiling po/hu.po for dockbarx
Compiling po/sv.po for dockbarx
Compiling po/ro.po for dockbarx
Compiling po/tr.po for dockbarx
Compiling po/es.po for dockbarx
Compiling po/ar.po for dockbarx
Compiling po/el.po for dockbarx
Compiling po/id.po for dockbarx
Compiling po/ja.po for dockbarx
Compiling po/ru.po for dockbarx
Compiling po/en_GB.po for dockbarx
Compiling po/it.po for dockbarx
Compiling po/zh_CN.po for dockbarx
Compiling po-themes/de.po for dockbarx-themes
Compiling po-themes/fr.po for dockbarx-themes
Compiling po-themes/fi.po for dockbarx-themes
Compiling po-themes/cs.po for dockbarx-themes
Compiling po-themes/eu.po for dockbarx-themes
Compiling po-themes/ko.po for dockbarx-themes
Compiling po-themes/nl.po for dockbarx-themes
Compiling po-themes/zh_TW.po for dockbarx-themes
Compiling po-themes/uk.po for dockbarx-themes
Compiling po-themes/lt.po for dockbarx-themes
Compiling po-themes/th.po for dockbarx-themes
Compiling po-themes/pt_BR.po for dockbarx-themes
Compiling po-themes/pl.po for dockbarx-themes
Compiling po-themes/sk.po for dockbarx-themes
Compiling po-themes/hu.po for dockbarx-themes
Compiling po-themes/sv.po for dockbarx-themes
Compiling po-themes/ro.po for dockbarx-themes
Compiling po-themes/es.po for dockbarx-themes
Compiling po-themes/el.po for dockbarx-themes
Compiling po-themes/ja.po for dockbarx-themes
Compiling po-themes/ru.po for dockbarx-themes
Compiling po-themes/en_GB.po for dockbarx-themes
Compiling po-themes/it.po for dockbarx-themes
Compiling po-themes/zh_CN.po for dockbarx-themes
running install_lib
creating /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/i18n.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/log.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/zg.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/mediabuttons.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/theme.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/dockbar.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/cairowidgets.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/common.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/dockmanager.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/windowbutton.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/__init__.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/groupbutton.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
copying build/lib.linux-x86_64-2.6/dockbarx/iconfactory.py -> /usr/local/lib/python2.6/dist-packages/dockbarx
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/i18n.py to i18n.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/log.py to log.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/zg.py to zg.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/mediabuttons.py to mediabuttons.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/theme.py to theme.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/dockbar.py to dockbar.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/cairowidgets.py to cairowidgets.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/common.py to common.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/dockmanager.py to dockmanager.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/windowbutton.py to windowbutton.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/__init__.py to __init__.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/groupbutton.py to groupbutton.pyc
byte-compiling /usr/local/lib/python2.6/dist-packages/dockbarx/iconfactory.py to iconfactory.pyc
running install_data
creating /usr/share/dockbarx
creating /usr/share/dockbarx/themes
copying themes/default.tar.gz -> /usr/share/dockbarx/themes
copying themes/Gaia.tar.gz -> /usr/share/dockbarx/themes
copying themes/old.tar.gz -> /usr/share/dockbarx/themes
copying themes/minimalistic.tar.gz -> /usr/share/dockbarx/themes
copying themes/sunny-c.tar.gz -> /usr/share/dockbarx/themes
copying themes/new_theme.tar.gz -> /usr/share/dockbarx/themes
copying dockbarx_factory -> /usr/bin
copying dbx_preference -> /usr/bin
copying GNOME_DockBarXApplet.server -> /usr/lib/bonobo/servers
copying dbx_preference.desktop -> /usr/share/applications/
creating /usr/local/share/icons
creating /usr/local/share/icons/hicolor
creating /usr/local/share/icons/hicolor/128x128
creating /usr/local/share/icons/hicolor/128x128/apps
copying icons/hicolor/128x128/apps/dockbarx.png -> /usr/local/share/icons/hicolor/128x128/apps
creating /usr/local/share/icons/hicolor/96x96
creating /usr/local/share/icons/hicolor/96x96/apps
copying icons/hicolor/96x96/apps/dockbarx.png -> /usr/local/share/icons/hicolor/96x96/apps
creating /usr/local/share/icons/hicolor/72x72
creating /usr/local/share/icons/hicolor/72x72/apps
copying icons/hicolor/72x72/apps/dockbarx.png -> /usr/local/share/icons/hicolor/72x72/apps
creating /usr/local/share/icons/hicolor/64x64
creating /usr/local/share/icons/hicolor/64x64/apps
copying icons/hicolor/64x64/apps/dockbarx.png -> /usr/local/share/icons/hicolor/64x64/apps
creating /usr/local/share/icons/hicolor/48x48
creating /usr/local/share/icons/hicolor/48x48/apps
copying icons/hicolor/48x48/apps/dockbarx.png -> /usr/local/share/icons/hicolor/48x48/apps
creating /usr/local/share/icons/hicolor/36x36
creating /usr/local/share/icons/hicolor/36x36/apps
copying icons/hicolor/36x36/apps/dockbarx.png -> /usr/local/share/icons/hicolor/36x36/apps
creating /usr/local/share/icons/hicolor/24x24
creating /usr/local/share/icons/hicolor/24x24/apps
copying icons/hicolor/24x24/apps/dockbarx.png -> /usr/local/share/icons/hicolor/24x24/apps
creating /usr/local/share/icons/hicolor/22x22
creating /usr/local/share/icons/hicolor/22x22/apps
copying icons/hicolor/22x22/apps/dockbarx.png -> /usr/local/share/icons/hicolor/22x22/apps
creating /usr/local/share/icons/hicolor/16x16
creating /usr/local/share/icons/hicolor/16x16/apps
copying icons/hicolor/16x16/apps/dockbarx.png -> /usr/local/share/icons/hicolor/16x16/apps
copying build/locale/nl/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/nl/LC_MESSAGES
copying build/locale/nl/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/nl/LC_MESSAGES
copying build/locale/th/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/th/LC_MESSAGES
copying build/locale/de/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/de/LC_MESSAGES
copying build/locale/de/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/de/LC_MESSAGES
copying build/locale/uk/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/uk/LC_MESSAGES
copying build/locale/uk/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/uk/LC_MESSAGES
copying build/locale/id/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/id/LC_MESSAGES
copying build/locale/hu/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/hu/LC_MESSAGES
copying build/locale/hu/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/hu/LC_MESSAGES
copying build/locale/ru/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/ru/LC_MESSAGES
copying build/locale/ru/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/ru/LC_MESSAGES
copying build/locale/es/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/es/LC_MESSAGES
copying build/locale/es/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/es/LC_MESSAGES
copying build/locale/en_GB/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/en_GB/LC_MESSAGES
copying build/locale/en_GB/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/en_GB/LC_MESSAGES
copying build/locale/it/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/it/LC_MESSAGES
copying build/locale/it/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/it/LC_MESSAGES
copying build/locale/zh_TW/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/zh_TW/LC_MESSAGES
copying build/locale/zh_TW/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/zh_TW/LC_MESSAGES
copying build/locale/bg/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/bg/LC_MESSAGES
copying build/locale/pl/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/pl/LC_MESSAGES
copying build/locale/pl/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/pl/LC_MESSAGES
copying build/locale/pt_BR/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/pt_BR/LC_MESSAGES
copying build/locale/pt_BR/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/pt_BR/LC_MESSAGES
copying build/locale/pt/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/pt/LC_MESSAGES
copying build/locale/ro/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/ro/LC_MESSAGES
copying build/locale/ro/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/ro/LC_MESSAGES
copying build/locale/fr/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/fr/LC_MESSAGES
copying build/locale/fr/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/fr/LC_MESSAGES
copying build/locale/ar/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/ar/LC_MESSAGES
copying build/locale/zh_CN/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/zh_CN/LC_MESSAGES
copying build/locale/zh_CN/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/zh_CN/LC_MESSAGES
copying build/locale/cs/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/cs/LC_MESSAGES
copying build/locale/cs/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/cs/LC_MESSAGES
copying build/locale/sk/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/sk/LC_MESSAGES
copying build/locale/sk/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/sk/LC_MESSAGES
copying build/locale/sv/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/sv/LC_MESSAGES
copying build/locale/sv/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/sv/LC_MESSAGES
copying build/locale/ko/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/ko/LC_MESSAGES
copying build/locale/ko/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/ko/LC_MESSAGES
copying build/locale/tr/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/tr/LC_MESSAGES
copying build/locale/lt/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/lt/LC_MESSAGES
copying build/locale/lt/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/lt/LC_MESSAGES
copying build/locale/eu/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/eu/LC_MESSAGES
copying build/locale/eu/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/eu/LC_MESSAGES
copying build/locale/fi/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/fi/LC_MESSAGES
copying build/locale/fi/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/fi/LC_MESSAGES
copying build/locale/ja/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/ja/LC_MESSAGES
copying build/locale/ja/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/ja/LC_MESSAGES
copying build/locale/el/LC_MESSAGES/dockbarx.mo -> /usr/share/locale/el/LC_MESSAGES
copying build/locale/el/LC_MESSAGES/dockbarx-themes.mo -> /usr/share/locale/el/LC_MESSAGES
running install_egg_info
Writing /usr/local/lib/python2.6/dist-packages/Dockbarx-0.3.1.egg-info

Any idea?

---

### Post by Copper Bezel on 2011-04-25
Well, let's test it independent of the panel, first.

```
dockbarx_factory run-in-window
```

Sorry about the extra pounds, by the way. = (

---

### Post by Alfons81 on 2011-04-26
Here is the result after trying to run it out of panel...seems something is wrong:

alfons@alfons:~$ dockbarx_factory run-in-window
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory", line 31, in <module>
    import dockbarx.dockbar
  File "/usr/local/lib/python2.6/dist-packages/dockbarx/dockbar.py", line 37, in <module>
    from groupbutton import *
  File "/usr/local/lib/python2.6/dist-packages/dockbarx/groupbutton.py", line 35, in <module>
    from iconfactory import IconFactory
  File "/usr/local/lib/python2.6/dist-packages/dockbarx/iconfactory.py", line 25, in <module>
    import Image
ImportError: No module named Image

If I can manage to run DockbarX, extra pounds are worth...

This is DocbarX: [http://gnome-look.org/content/show.php/DockbarX?content=101604](http://gnome-look.org/content/show.php/DockbarX?content=101604)

---

### Post by Copper Bezel on 2011-04-26
Oh, I agree - it's a brilliant taskbar, easily the best I've used.

Okay, this one's an easy fix, at least - install python-imaging-dbg . Let's hope there aren't any more calls to standard-for-Gnome modules that aren't contained in a minimal XFCE install.

---

### Post by Alfons81 on 2011-04-26
Is working!!! Now the problem is that when I switch on the computer...doesn't launch. It appears a box saying something like: "Dockbarx cannot be launch because an internal error"

Then I need to remove Xfapplet, put it back again on the panel and then put again Dockbarx on it...

I don't know whats going on...but is almost done. Thanks a lot for your help!!!

see it on my panel

---

### Post by Alfons81 on 2011-04-26
This is the error I got on DockbarX.log, when I start up my computer. Once is started and I place it on the panel is working great...but I don't know how to solve the start up problem...

---

### Post by Copper Bezel on 2011-04-26
Sweet, we're most of the way there, then!

Damn, though, I only see two threads anywhere on this subject, and no one has any solutions. What happens if, instead of removing and reattaching xfapplet, you just restart the panel? 

```
killall xfce4-panel; xfce4-panel
```

Edit: I didn't see your second post, there.

Turn off Zeitgeist support in your DockBarX preferences and see if that fixes it. It's either looking for Zeitgeist data to populate the Recent Documents lists for your applications in the DockBarX taskbar, or looking for the a setting itself. It's possible that DBX's own data isn't loaded at that time in the boot process for some reason (so we go back to restarting the taskbar) but changing the setting might preempt the check.

Edit again: Thanks for providing the log, by the way! = D

---

### Post by Alfons81 on 2011-04-26
Wow man you really know how is it working!!! you really hit the nail on the head [-o<

Kill xfce4-panel and restart it...make it works...then we are almost there

About disabling Zeitgeist (also a nice documentary by the way) on Docbarx preferences...I don”t find how.

Kind of "dirty" solution could be a script...killing the panel and restarting it, i'm tryng something like but not working

#!/bin/bash

killall xfce4-panel && sleep 5 && xfce4-panel

Kills the panel but not restart it

---

### Post by Copper Bezel on 2011-04-26
Excellent!

Well, [FONT="Courier New"]&&[/FONT] instructs Bash to move on to the next command as soon as the first one's been sent. Did you try it with a semicolon after the delay (like [font="Courier New"]sleep 5; [/font]) instead?

As for Zeitgeist - and yes, a decent documentary as well = ) - you can deactivate the plugin in DockBarX Preferences under the Plugins tab; click the "Helpers" button and scroll to the bottom. It may be disabled by default, anyway, but it seemed worth checking.

---

### Post by M7S on 2011-04-27
Zeitgeist in helpers isn't the zeitgeist used in DockbarX since DockbarX used zeitgeist before it got helpers. For now there are no option to turn of zeitgeist besides uninstalling zeitgeist or hacking the code. 

I think that error in Alfons log should be fix in bzr and I'm about to release a new version of DockbarX some times after Natty has been released and the worst release hysteria has calmed down.

---

### Post by Copper Bezel on 2011-04-27
Sweet. Thanks for the clarification and the words of comfort - I was going to go add the python-image dependency to the bug concerning python-gnome2, but I guess you know now. = ) 

If you haven't seen me saying it, I love the hell out of your dock, so thank you for the awesome contribution to the Linux desktop experience. = )

---

### Post by Alfons81 on 2011-04-27
Hi all!!!

I removed Zeitgeist and I changed the start up script, as Cooper Bezel suggested, to:

#!/bin/bash

killall xfce4-panel; sleep 5; xfce4-panel

And now DockbarX is working randomly, sometimes it starts without problem and sometimes pop up the error window and doesn't launch.

M7S, you think better I wait the new release or there is a way to fix it?

---

### Post by M7S on 2011-04-28
If you uninstalled zeitgeist it's probably not the same error anymore and the workround should not be needed either. Could you post the log again (after a crash has occurred of course)? 



@Copper Bezel
Thanks. I've seen and appreciated the promotion you do for DockbarX here on the forums. If you like to contribute in another way as well I'm as always in the need of more beta testers who uses the newest code from bzr and report bugs to launchpad. To many bugs get reported first after a new release is made. Or perhaps you do this already but with another alias/name?

---

### Post by Alfons81 on 2011-04-29
Here is the last log, but is from yesterday, after removing Zeitgeist. Today it crash again (always only on start up) and no log under 

home/user/.dockbarx/log

Also many logs are empty, witch I suppose is because everything went ok, but I had 3 consecutive crashes and not seen log. As I said when I kill xfce4-panel and restart it...works as a charm. Fast, solid and esthetically perfect!!! 

Cheers!

---

### Post by Alfons81 on 2011-05-06
Hi!

Last discover... I've configured xfce4 to open any software running on last session when I power on my computer. Then when I leave any application open when I power off my computer on next boot DockbarX is not crashing on startup and it's runnig perfectly. It's only matter to leave always terminal open

Cheers!

---

