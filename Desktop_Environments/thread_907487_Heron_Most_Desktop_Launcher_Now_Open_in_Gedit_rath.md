---
title: "Heron: Most Desktop Launcher Now Open in Gedit rather than application"
date: 2008-09-01
forum: Desktop Environments
---

### Post by dpod on 2008-09-01
Hi all,

I have a problem on two clean install Heron machines: most of my custom launchers now try to load in gedit rather than the appropriate application. I also do not get a "open with" option when I right click. I have looked at gconf-editor and all the files types seem to be appropriate. All the launchers worked (and still work) fine either on Gutsy machines or on Heron machines that were upgraded. This only happens on clean installs. The same problem exists both with old, pre-heron launchers copied from backups and new launchers created in Heron.

There is an additional complication: while almost all url types open in gedit, some http and https urls (*but not all*) open correctly in firefox.

Here are some examples of working and non-working .desktop files:

Working:

[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Link
URL=https://www.uleth.ca/bridge/twgkwbis.P_WWWLogin
Name[en_US]=Bridge
Icon[en_US]=/usr/share/pixmaps/bridge.jpg
Name=Bridge
Icon=/usr/share/pixmaps/bridge.jpg

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=CD Collection
Type=Link
Name[en_CA]=CD Collection
URL=http://kakelbont.webhop.net/
Icon[en_CA]=/usr/share/pixmaps/CD.png
Icon=/usr/share/pixmaps/45.png
GenericName[en_CA]=

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=JazzFM Contemporary
Type=Link
Icon[en_US]=gnome-panel-launcher
URL=http://streamergamma.jazz.fm/tunein.php/ContemporaryJazz/playlist.asx
Name[en_US]=JazzFM Contemporary
Icon=/usr/share/pixmaps/jazzfm91.png
GenericName[en_US]=
GenericName[en_CA]=


NOT WORKING

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Router
Type=Link
Name[en_US]=Router
URL=https://192.168.0.1/
Icon[en_US]=/usr/share/pixmaps/router.png
Icon=/usr/share/pixmaps/router.png
GenericName[en_CA]=

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Router
Type=Link
Name[en_US]=Router
URL=http://192.168.0.1/
Icon[en_US]=/usr/share/pixmaps/router.png
Icon=/usr/share/pixmaps/router.png
GenericName[en_CA]=

[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=KPLU Jazz 24
Type=Link
Icon[en_CA]=/usr/share/pixmaps/jazz24.gif
URL=mms://wm-live.abacast.com/kplu-jazz24hi-64
Name[en_CA]=KPLU Jazz 24
Icon=/usr/share/pixmaps/jazz24.gif
GenericName[en_CA]=

ftp doesn't seem to work either. I've gone through these over and over and can't figure out what the differences are between the working and non-working ones: some working ones have filetype extensions, some don't. All have URL prefaces. Permissions, owners, and groups are the same. Some are new, some are old. All have working targets.

There must be some difference, though: if you right click on the launcher and choose properties, the ones that work have a known launcher and mime-type, while the ones that don't work are listed as unknown launcher type and a mime type of "application/octet-stream"--presumably if I could figure out where the properties tag is getting this information I could fix them!

Ideas?

Edit: I also went through the .desktop discussion at {{}} freedesktop and tried the solution mentioned here: [http://ubuntuforums.org/showthread.php?t=8723](http://ubuntuforums.org/showthread.php?t=8723). Specifying the mimetype explicitly doesn't seem to do any good, and it isn't changed after running sudo update-mime-database /usr/share/mime and sudo update-desktop-database Desktop.

---

### Post by rkdwv on 2009-06-03
Have the same problem. How to force .desktop url links to be opened by a browser? Now when I click .desktop icon - I get html code into gedit window. Please help. :(

---

### Post by lns on 2009-11-19
Same here - creating type=link .desktop files opens in gedit rather than Firefox. VERY frustrating! Using Ubuntu 8.04 LTS...

*** EDIT ***
Well after about 2 days of searching around, I found that it was MY problem. I manually edited /usr/share/applications/firefox.desktop and removed from the Exec= line, %u (which opens the link passed to the program) and had put google.com in manually. This caused firefox.desktop (specified launcher in mime type text/html in /usr/share/applications/defaults.list) to fail and for it to presumably fall back on the default text editor (gedit).

Ugh. Hope this helps anyone else who hacked their system and then expected it to work properly. ;)

---

