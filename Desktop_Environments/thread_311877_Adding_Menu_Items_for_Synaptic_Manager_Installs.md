---
title: "Adding Menu Items for Synaptic Manager Installs"
date: 2006-12-03
forum: Desktop Environments
---

### Post by quall on 2006-12-03
Hello. I am installing some (universe) programs with the Synaptic Package Manager. However, I cannot get menu item shortcuts to show up for all users. 

I can create a shortcut for zsnes in my games menu with the [System]->[Preferences]->[Menu Layout] tool, but it does not show up for anyone else. How would I get these newly installed applications to show up for all users? I have been searching for a bit and someone suggested to make a desktop link and place it in the folder "/usr/share/applications", but it does not show up (even after restarting gnome). Here is an example of desktop link for ZSNES:
```
[Desktop Entry]
Encoding=UTF-8
Name=ZSNES SNES Emulator
Comment=emulates SNES games
Categories=Applications;Games;
Exec=zsnes %u
Terminal=false
Icon=zsnes.xpm
Type=Application
X-GNOME-DocPath=zsnes/zsnes.xml
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=zsnes
X-GNOME-Bugzilla-Component=general
StartupNotify=true
MimeType=text/plain;text/x-readme;application/x-shellscript;
```
It is named zsnes.desktop (and runs when clicked). I placed it in the "/usr/share/applications" folder, but it does not show up in my menu lists (it is not hidden either). 

Can anyone help with this?

---

### Post by quall on 2006-12-04
for anyone that comes across a similar problem, check the category. 

I had:
Categories=Applications;Games;

It should be:
Categories=Application;Game;

sorry, it was the wrong category.

---

