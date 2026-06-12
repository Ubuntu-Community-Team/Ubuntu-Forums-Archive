---
title: "Unity Launcher .desktop options for middle click"
date: 2012-08-31
forum: Desktop Environments
---

### Post by jpate on 2012-08-31
i'm trying to come up with a good .desktop file for sublime text 2, but middle click isn't opening a 2nd window, and when I specify an Exec line with --new-window sublime opens 2 windows to start!

Is there any way to specify a different command line when you middle click (shift click etc) on the unity launcher? 
anyone have a better sublime text 2 .desktop file?


[Desktop Entry]
Type=Application
Terminal=false
Name=Sublime Text 2
StartupNotify=true
GenericName=Text Editor
Comment=Edit text files
Exec="/home/user/bin/Sublime Text 2/sublime_text" %U
Icon=/home/user/bin/Sublime Text 2/Icon/128x128/sublime_text.png
MimeType=text/plain;text/x-chdr;text/x-csrc;text/x-c++hdr;text/x-c++src;text/x-java;text/x-dsrc;text/x-pascal;text/x-perl;text/x-python;application/x-php;application/x-httpd-php3;application/x-httpd-php4;application/x-httpd-php5;application/xml;text/html;text/css;text/x-sql;text/x-diff;x-directory/normal;inode/directory;
Categories=GNOME;GTK;Utility;TextEditor;Application;Development;
Name[en_US]=Sublime Text 2
X-Ayatana-Desktop-Shortcuts=NewWindow;

[NewWindow Shortcut Group]
Name=New Editor Window
Exec="/home/user/bin/Sublime Text 2/sublime_text" --new-window
TargetEnvironment=Unity


#New Editor Window shortcut works, but i want middle/shift click #$!$!!@#!

---

