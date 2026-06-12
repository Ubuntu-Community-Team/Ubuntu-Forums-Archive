---
title: "Cannot Create Desktop Icon ElementaryOS"
date: 2013-02-18
forum: Desktop Environments
---

### Post by trenth on 2013-02-18
So i'm using eOS, and i'm trying to create a .desktop file and add it to /usr/share/applications. It gets succesfully added, but it's not appearing in my Applications?

I've tried "sudo mv" and that didn't help. Not exactly whats going on here.

[Desktop Entry]
Value=1.0
Type=Application
Name=TeamSpeak
GenericName=TeamSpeak
Exec=/home/trent/Downloads/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh
Icon=/home/trent/Downloads/TeamSpeak3-Client-linux_amd64/icon.png
StartupNotify=true
Categories=Internet;

This is the code i'm saving as TeamSpeak3.desktop

Any help is appreciated, and yes all the paths are 100% correct.

---

### Post by trenth on 2013-02-18
[Desktop Entry]
Name=TeamSpeak 3
Comment=TeamSpeak
Exec=/home/trent/Downloads/TeamSpeak3-Client-linux_amd64/ts3client_runscript.sh
Terminal=false
Type=Application
Icon=/home/trent/Downloads/TeamSpeak3-Client-linux_amd64/icon.png
# StartupNotify=true
Categories=GTK;GNOME;Utility;
NotShowIn=KDE;

I copied the text from a different file and used it and typed in my information. This works now! :)

---

