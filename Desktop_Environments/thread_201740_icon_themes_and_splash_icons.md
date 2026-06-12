---
title: "icon themes and splash icons?"
date: 2006-06-22
forum: Desktop Environments
---

### Post by linuxNewb on 2006-06-22
I changed my icon theme and I really like the new icons (CrystalClear), but this new theme sets new splash icons (the icons that are displayed over the splash image when starting a session) and one of them is a KDE icon. I want to change it to a GNOME icon, but I can't find the name or location of this icon.

How can I find out the name/location of one of my theme's splash icons? Thanks in advance.

---

### Post by Nonno Bassotto on 2006-06-22
Your icons are stored under ~/.icons/NameOfTheTheme/
This folder is subdivided first according to size (say 128x128 and so on) and then each size folder is divided into
/apps
/devices
/emblems
/extra
/gtk
/filesystems
/mimetypes
The icon you are looking for should be gnome-logo-icon.png or something similar uner apps. So you have to manually change
~/.icons/NameOfTheTheme/RightSize/apps/gnome-logo-icon.png

---

