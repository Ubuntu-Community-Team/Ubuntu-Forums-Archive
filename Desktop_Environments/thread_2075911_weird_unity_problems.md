---
title: "weird unity problems"
date: 2012-10-24
forum: Desktop Environments
---

### Post by linuxgrrl on 2012-10-24
Hi,
After upgrading to 12.04, Unity has some weird problems. When I start a terminal, I get a window with a black background but the command prompt is not visible (even if I maximize the window!)  When I go to appearance settings, the only thing I can edit is the desktop background ... the menus on the toolbar are unreadable because the background and text are both dark colored, but there's no way to edit the background color f the toolbar.

I mean, something is wrong, right? What's the deal here? 
(PS, if I select one of the other window managers, they are pretty much hosed and don't work at all, so I'm stuck w/ unity for the moment).

---

### Post by linuxgrrl on 2012-10-24
More info: 

running Gnome from command line gives the following error:
Gconf WARNING Got Disconnected from DBUS

running unity --replace gives errors like:
 Checking if settings need to be migrated ...no
Checking if internal files need to be migrated ...no
WARN  2012-10-24 21:40:21 unity.favorites FavoriteStoreGSettings.cpp:139 Unable to load GDesktopAppInfo for 'ubiquity-gtkui.desktop'
ERROR 2012-10-24 21:40:21 unity.launcher.trashlaunchericon TrashLauncherIcon.cpp:62 Could not create file monitor for trash uri: Operation not supported
WARNING: no DISPLAY variable set, setting it to :0
compiz (core) fatal: Couldn't open display :0

---

### Post by linuxgrrl on 2012-10-24
Okay, I can't even begin to guess why, but I solved these by going to a command prompt wth 
ctrl-alt-F1

then trying a command that others found helpful:
rm -rf ./.config/compiz-1

then logging back out and in. Now Unity seems to work normally.

---

