---
title: "[SOLVED] How to install kiba dock?"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by 4l13n666 on 2008-03-23
Hey,

I have tried installing Kiba dock using several methods but without any success whatsoever.
I used AWN but i don't really like it. I want the kiba physics.

I am running CompizConfig, latest version on Gutsy. 

Does anyone know how to install kiba dock and have it stable on Gutsy?

---

### Post by gottifour on 2008-03-23
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)


I followed these directions and it worked great. I tried a few other ways prior to this with no luck.

---

### Post by 4l13n666 on 2008-03-23
Yeah i have followed that guide several times but since im a complete noob with ubuntu his guide is quite complicated for me. When i followed his instructions i only got the kiba dock file folder downloaded and not installed. If it's not too much to ask, can you post his guide in very simple steps for me to follow? Detailed if you don't mind!

---

### Post by 4l13n666 on 2008-03-23
Alright i followed the guide and this is what happened...

The only thing i got is a folder called kiba-dock which has the files inside it. No install, nothing!

This is the entire installation terminal output. **_Any thoughts?_**

erik@erik-laptop:~$ mkdir kiba-dock
mkdir: cannot create directory `kiba-dock': File exists
erik@erik-laptop:~$ cd kiba-dock
erik@erik-laptop:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? p
A    akamaru/include
A    akamaru/include/akamaru.h
A    akamaru/include/Makefile.am
A    akamaru/AUTHORS
A    akamaru/INSTALL
A    akamaru/configure.in
A    akamaru/ChangeLog
A    akamaru/akamaru.pc.in
A    akamaru/src
A    akamaru/src/akamaru.c
A    akamaru/src/Makefile.am
A    akamaru/COPYING
A    akamaru/Makefile.am
A    akamaru/autogen.sh
A    akamaru/NEWS
A    akamaru/README
Checked out revision 732.
erik@erik-laptop:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock
A    kiba-dock/include
A    kiba-dock/include/kiba-icon.h
A    kiba-dock/include/kiba-cairo-utils.h
A    kiba-dock/include/kiba-desktop-editor.h
A    kiba-dock/include/kiba-win.h
A    kiba-dock/include/kiba-desktop-icon.h
A    kiba-dock/include/kiba-dialog.h
A    kiba-dock/include/kiba-utils.h
A    kiba-dock/include/kiba.h
A    kiba-dock/include/kiba-fixed-object.h
A    kiba-dock/include/kiba-types.h
A    kiba-dock/include/kiba-progress.h
A    kiba-dock/include/kiba-triangle.h
A    kiba-dock/include/kiba-object.h
A    kiba-dock/include/kiba-x11.h
A    kiba-dock/include/kiba-prefs-schema.h
A    kiba-dock/include/kiba-screen.h
A    kiba-dock/include/kiba-app-chooser.h
A    kiba-dock/include/kiba-dock.h
A    kiba-dock/include/kiba-title.h
A    kiba-dock/include/kiba-image.h
A    kiba-dock/include/kiba-debug.h
A    kiba-dock/include/kiba-info-win.h
A    kiba-dock/include/kiba-tooltip.h
A    kiba-dock/include/kiba-icon-view-win.h
A    kiba-dock/include/kiba-inline-pixbufs.h
A    kiba-dock/include/kiba-surface-factory.h
A    kiba-dock/include/kiba-plugin.h
A    kiba-dock/include/kiba-separator.h
A    kiba-dock/include/kiba-icon-view.h
A    kiba-dock/include/kiba-plugin-loader.h
A    kiba-dock/include/kiba-key-file.h
A    kiba-dock/include/kiba-window.h
A    kiba-dock/include/kiba-prefs.h
A    kiba-dock/include/Makefile.am
A    kiba-dock/include/kiba-menu-items.h
A    kiba-dock/include/kiba-globals.h
A    kiba-dock/include/kiba-macros.h
A    kiba-dock/VERSION
A    kiba-dock/AUTHORS
A    kiba-dock/ChangeLog
A    kiba-dock/src
A    kiba-dock/src/desktop-icon.c
A    kiba-dock/src/dialog.c
A    kiba-dock/src/sdl-helper.c
A    kiba-dock/src/utils.c
A    kiba-dock/src/prefs-callbacks.h
A    kiba-dock/src/separator-menu.c
A    kiba-dock/src/fixed-object.c
A    kiba-dock/src/progress.c
A    kiba-dock/src/sdl-helper.h
A    kiba-dock/src/triangle.c
A    kiba-dock/src/object.c
A    kiba-dock/src/marshallers.list
A    kiba-dock/src/kiba.c
A    kiba-dock/src/glitz-helper.c
A    kiba-dock/src/separator-menu.h
A    kiba-dock/src/x11.c
A    kiba-dock/src/dnd-window.c
A    kiba-dock/src/win-private.h
A    kiba-dock/src/glitz-helper.h
A    kiba-dock/src/prefs-schema.c
A    kiba-dock/src/dnd-window.h
A    kiba-dock/src/screen.c
A    kiba-dock/src/app-chooser.c
A    kiba-dock/src/dock.c
A    kiba-dock/src/title.c
A    kiba-dock/src/image.c
A    kiba-dock/src/default-shape.c
A    kiba-dock/src/info-win.c
A    kiba-dock/src/debug.c
A    kiba-dock/src/startup-notification.c
A    kiba-dock/src/default-shape.h
A    kiba-dock/src/tooltip.c
A    kiba-dock/src/icon-view-win.c
A    kiba-dock/src/startup-notification.h
A    kiba-dock/src/podest-shape.c
A    kiba-dock/src/surface-factory.c
A    kiba-dock/src/plugin.c
A    kiba-dock/src/title-private.h
A    kiba-dock/src/icon-view.c
A    kiba-dock/src/separator.c
A    kiba-dock/src/podest-shape.h
A    kiba-dock/src/plugin-loader.c
A    kiba-dock/src/key-file.c
A    kiba-dock/src/window.c
A    kiba-dock/src/prefs-dbus.c
A    kiba-dock/src/surface-factory-private.h
A    kiba-dock/src/prefs-dbus.h
A    kiba-dock/src/prefs.c
A    kiba-dock/src/dock-menu.c
A    kiba-dock/src/menu-items.c
A    kiba-dock/src/main.c
A    kiba-dock/src/dock-menu.h
A    kiba-dock/src/icon.c
A    kiba-dock/src/Makefile.am
A    kiba-dock/src/prefs-dbus.xml
A    kiba-dock/src/cairo-utils.c
A    kiba-dock/src/prefs-callbacks.c
A    kiba-dock/src/prefs-private.h
A    kiba-dock/src/desktop-editor.c
A    kiba-dock/src/win.c
A    kiba-dock/kiba-dock.pc.in
A    kiba-dock/README
A    kiba-dock/files
A    kiba-dock/files/populate-dock.sh.in
A    kiba-dock/files/general.xml.in.in
A    kiba-dock/files/kiba-dock.desktop.in.in
A    kiba-dock/files/Makefile.am
A    kiba-dock/files/dock.xml.in.in
A    kiba-dock/configure.ac
A    kiba-dock/kiba-settings
A    kiba-dock/kiba-settings/kiba-gradient-chooser-dialog.c
A    kiba-dock/kiba-settings/settings-dbus.h
A    kiba-dock/kiba-settings/kiba-gradient-chooser.c
A    kiba-dock/kiba-settings/kiba-gradient-chooser-dialog.h
A    kiba-dock/kiba-settings/kiba-settings.c
A    kiba-dock/kiba-settings/kiba-settings.desktop.in.in
A    kiba-dock/kiba-settings/kiba-gradient-chooser.h
A    kiba-dock/kiba-settings/widgets.c
A    kiba-dock/kiba-settings/Makefile.am
A    kiba-dock/kiba-settings/kiba-settings.h
A    kiba-dock/kiba-settings/settings-dbus.c
A    kiba-dock/kiba-settings/widgets.h
A    kiba-dock/TODO
A    kiba-dock/INSTALL
A    kiba-dock/COPYING
A    kiba-dock/Makefile.am
A    kiba-dock/icons
A    kiba-dock/icons/kiba-dock-panel.svg
A    kiba-dock/icons/kiba_16.png
A    kiba-dock/icons/kiba-dock.svg
A    kiba-dock/icons/kiba_64.png
A    kiba-dock/icons/kiba_128.png
A    kiba-dock/icons/kiba_48.png
A    kiba-dock/icons/broken-glass.svg
A    kiba-dock/icons/Makefile.am
A    kiba-dock/icons/kiba-dock-objects.svg
A    kiba-dock/icons/kiba-window.svg
A    kiba-dock/icons/gear-dark.svg
A    kiba-dock/icons/gear.svg
A    kiba-dock/icons/kiba_24.png
A    kiba-dock/icons/visual-effects.svg
A    kiba-dock/autogen.sh
A    kiba-dock/NEWS
A    kiba-dock/po
A    kiba-dock/po/pt.po
A    kiba-dock/po/LINGUAS
A    kiba-dock/po/es.po
A    kiba-dock/po/fr.po
A    kiba-dock/po/bg.po
A    kiba-dock/po/de.po
A    kiba-dock/po/ChangeLog
A    kiba-dock/po/ja.po
A    kiba-dock/po/it.po
A    kiba-dock/po/POTFILES.in
Checked out revision 732.
erik@erik-laptop:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins
A    kiba-plugins/files
A    kiba-plugins/files/sysinfo_themes
A    kiba-plugins/files/sysinfo_themes/custom_tango
A    kiba-plugins/files/sysinfo_themes/custom_tango/sysinfo-frame.svg
A    kiba-plugins/files/sysinfo_themes/custom_tango/sysinfo-hand.svg
A    kiba-plugins/files/sysinfo_themes/custom_tango/sysinfo-face.svg
A    kiba-plugins/files/sysinfo_themes/default
A    kiba-plugins/files/sysinfo_themes/default/sysinfo-frame.svg
A    kiba-plugins/files/sysinfo_themes/default/sysinfo-hand.svg
A    kiba-plugins/files/sysinfo_themes/default/sysinfo-face.svg
A    kiba-plugins/files/sysinfo_themes/gold
A    kiba-plugins/files/sysinfo_themes/gold/sysinfo-frame.svg
A    kiba-plugins/files/sysinfo_themes/gold/sysinfo-hand.svg
A    kiba-plugins/files/sysinfo_themes/gold/sysinfo-face.svg
A    kiba-plugins/files/dbus.png
A    kiba-plugins/files/volume.xml.in.in
A    kiba-plugins/files/sysinfo.xml.in.in
A    kiba-plugins/files/taskbar.svg
A    kiba-plugins/files/dbus.xml.in.in
A    kiba-plugins/files/Makefile.am
A    kiba-plugins/files/akamaru.xml.in.in
A    kiba-plugins/files/plugins.xml.in.in
A    kiba-plugins/files/trash.xml.in.in
A    kiba-plugins/files/clock_theme
A    kiba-plugins/files/clock_theme/clock-hour-hand-shadow.svg
A    kiba-plugins/files/clock_theme/clock-glass.svg
A    kiba-plugins/files/clock_theme/clock-minute-hand.svg
A    kiba-plugins/files/clock_theme/clock-frame.svg
A    kiba-plugins/files/clock_theme/clock-minute-hand-shadow.svg
A    kiba-plugins/files/clock_theme/clock-marks.svg
A    kiba-plugins/files/clock_theme/clock-face.svg
A    kiba-plugins/files/clock_theme/clock-face-shadow.svg
A    kiba-plugins/files/clock_theme/clock-second-hand.svg
A    kiba-plugins/files/clock_theme/clock-hour-hand.svg
A    kiba-plugins/files/clock_theme/clock-second-hand-shadow.svg
A    kiba-plugins/files/clock_theme/clock-drop-shadow.svg
A    kiba-plugins/files/stack.xml.in.in
A    kiba-plugins/AUTHORS
A    kiba-plugins/TODO
A    kiba-plugins/INSTALL
A    kiba-plugins/configure.in
A    kiba-plugins/ChangeLog
A    kiba-plugins/src
A    kiba-plugins/src/stack-plugin.c
A    kiba-plugins/src/launcher.c
A    kiba-plugins/src/switch.c
A    kiba-plugins/src/stack.c
A    kiba-plugins/src/marshallers.list
A    kiba-plugins/src/launcher.h
A    kiba-plugins/src/trash-monitor.c
A    kiba-plugins/src/volume.c
A    kiba-plugins/src/calendar.c
A    kiba-plugins/src/stack.h
A    kiba-plugins/src/bounce.c
A    kiba-plugins/src/gmenu.c
A    kiba-plugins/src/trash-monitor.h
A    kiba-plugins/src/calendar.h
A    kiba-plugins/src/trash.c
A    kiba-plugins/src/panel-applet.c
A    kiba-plugins/src/clipman.c
A    kiba-plugins/src/alsa_mixer.c
A    kiba-plugins/src/taskbar.c
A    kiba-plugins/src/alsa_mixer.h
A    kiba-plugins/src/winlist.c
A    kiba-plugins/src/sysinfo.c
A    kiba-plugins/src/stack-icon.c
A    kiba-plugins/src/dbus.c
A    kiba-plugins/src/eggtraymanager.c
A    kiba-plugins/src/rotate.c
A    kiba-plugins/src/stack-icon.h
A    kiba-plugins/src/gst_mixer.c
A    kiba-plugins/src/eggtraymanager.h
A    kiba-plugins/src/gst_mixer.h
A    kiba-plugins/src/kiba-dbus.xml
A    kiba-plugins/src/tray.c
A    kiba-plugins/src/akamaru.c
A    kiba-plugins/src/mixer.c
A    kiba-plugins/src/eggmarshalers.c
A    kiba-plugins/src/zoom.c
A    kiba-plugins/src/kiba-akamaru.c
A    kiba-plugins/src/pulse.c
A    kiba-plugins/src/Makefile.am
A    kiba-plugins/src/mixer.h
A    kiba-plugins/src/eggmarshalers.h
A    kiba-plugins/src/kiba-akamaru.h
A    kiba-plugins/src/clock.c
A    kiba-plugins/src/launcher-plugin.c
A    kiba-plugins/COPYING
A    kiba-plugins/Makefile.am
A    kiba-plugins/autogen.sh
A    kiba-plugins/NEWS
A    kiba-plugins/README
A    kiba-plugins/po
A    kiba-plugins/po/pt.po
A    kiba-plugins/po/LINGUAS
A    kiba-plugins/po/es.po
A    kiba-plugins/po/fr.po
A    kiba-plugins/po/bg.po
A    kiba-plugins/po/de.po
A    kiba-plugins/po/ChangeLog
A    kiba-plugins/po/ja.po
A    kiba-plugins/po/it.po
A    kiba-plugins/po/POTFILES.in
Checked out revision 732.
erik@erik-laptop:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins
A    kiba-dbus-plugins/configure.ac
A    kiba-dbus-plugins/AUTHORS
A    kiba-dbus-plugins/TODO
A    kiba-dbus-plugins/VERSION
A    kiba-dbus-plugins/themes
A    kiba-dbus-plugins/themes/kiba-signal
A    kiba-dbus-plugins/themes/kiba-signal/0.png
A    kiba-dbus-plugins/themes/kiba-signal/100.png
A    kiba-dbus-plugins/themes/kiba-signal/20.png
A    kiba-dbus-plugins/themes/kiba-signal/40.png
A    kiba-dbus-plugins/themes/kiba-signal/60.png
A    kiba-dbus-plugins/themes/kiba-signal/80.png
A    kiba-dbus-plugins/themes/kiba-weather
A    kiba-dbus-plugins/themes/kiba-weather/nightcloud.png
A    kiba-dbus-plugins/themes/kiba-weather/nightsnow.png
A    kiba-dbus-plugins/themes/kiba-weather/raincloud.png
A    kiba-dbus-plugins/themes/kiba-weather/Copyright.txt
A    kiba-dbus-plugins/themes/kiba-weather/nightrain.png
A    kiba-dbus-plugins/themes/kiba-weather/daycloud.png
A    kiba-dbus-plugins/themes/kiba-weather/daysnow.png
A    kiba-dbus-plugins/themes/kiba-weather/nightfog.png
A    kiba-dbus-plugins/themes/kiba-weather/sun.png
A    kiba-dbus-plugins/themes/kiba-weather/cloud.png
A    kiba-dbus-plugins/themes/kiba-weather/snow.png
A    kiba-dbus-plugins/themes/kiba-weather/dayrain.png
A    kiba-dbus-plugins/themes/kiba-weather/moon.png
A    kiba-dbus-plugins/themes/kiba-weather/dayfog.png
A    kiba-dbus-plugins/themes/kiba-weather/fog.png
A    kiba-dbus-plugins/themes/kiba-mail
A    kiba-dbus-plugins/themes/kiba-mail/none.png
A    kiba-dbus-plugins/themes/kiba-mail/AUTHORS
A    kiba-dbus-plugins/themes/kiba-mail/new.png
A    kiba-dbus-plugins/themes/Makefile.am
A    kiba-dbus-plugins/themes/kiba-battery
A    kiba-dbus-plugins/themes/kiba-battery/0.png
A    kiba-dbus-plugins/themes/kiba-battery/none.png
A    kiba-dbus-plugins/themes/kiba-battery/100.png
A    kiba-dbus-plugins/themes/kiba-battery/50.png
A    kiba-dbus-plugins/themes/kiba-battery/25.png
A    kiba-dbus-plugins/themes/kiba-battery/75.png
A    kiba-dbus-plugins/themes/kiba-feeder
A    kiba-dbus-plugins/themes/kiba-feeder/old.png
A    kiba-dbus-plugins/themes/kiba-feeder/new.png
A    kiba-dbus-plugins/INSTALL
A    kiba-dbus-plugins/ChangeLog
A    kiba-dbus-plugins/scripts
A    kiba-dbus-plugins/scripts/kiba-weather.py.in
A    kiba-dbus-plugins/scripts/quod_dbus_cover.py.in
A    kiba-dbus-plugins/scripts/kiba-mail.py.in
A    kiba-dbus-plugins/scripts/Makefile.am
A    kiba-dbus-plugins/scripts/kiba-amarok.py.in
A    kiba-dbus-plugins/scripts/kiba-battery.py.in
A    kiba-dbus-plugins/scripts/kiba-feeder.py.in
A    kiba-dbus-plugins/scripts/kiba-signal.py.in
A    kiba-dbus-plugins/scripts/firefox.py.in
A    kiba-dbus-plugins/COPYING
A    kiba-dbus-plugins/Makefile.am
A    kiba-dbus-plugins/data
A    kiba-dbus-plugins/data/python_scripts.xml.in.in
A    kiba-dbus-plugins/data/kiba-amarok.spec
A    kiba-dbus-plugins/data/Makefile.am
A    kiba-dbus-plugins/autogen.sh
A    kiba-dbus-plugins/NEWS
A    kiba-dbus-plugins/README
A    kiba-dbus-plugins/po
A    kiba-dbus-plugins/po/pt.po
A    kiba-dbus-plugins/po/LINGUAS
A    kiba-dbus-plugins/po/es.po
A    kiba-dbus-plugins/po/bg.po
A    kiba-dbus-plugins/po/de.po
A    kiba-dbus-plugins/po/ja.po
A    kiba-dbus-plugins/po/it.po
A    kiba-dbus-plugins/po/POTFILES.in
Checked out revision 732.
erik@erik-laptop:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins

---

