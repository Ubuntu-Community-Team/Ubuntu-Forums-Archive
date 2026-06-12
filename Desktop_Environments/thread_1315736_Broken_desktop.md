---
title: "Broken desktop"
date: 2009-11-05
forum: Desktop Environments
---

### Post by petermoffat on 2009-11-05
Right, I'm trying to use a folder ona different drive as my desktop.

Folder is /media/Thingies/Desktop

I edited ~/.config/user-dirs.dirs and replaced 

XDG_DESKTOP_DIR="$HOME/Desktop"

with 

XDG_DESKTOP_DIR="/media/Thingies/Desktop"

which works in Nautilus, so if I click the desktop link under Places, the folders in the 'Desktop' folder I want to use are there, but they are not on the desktop.. I also can't copy anything to the desktop or even right click on it..

Any ideas??

---

### Post by pjbgravely on 2009-11-06
Might be a permissions problem. Make sure the folder is in your name.

sudo chown -R your_username. /media/Thingies/Desktop

chmod -R 751 /media/Thingies/Desktop

Paul

---

