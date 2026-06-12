---
title: "[SOLVED] gnome wallpaper"
date: 2008-08-25
forum: Desktop Environments
---

### Post by leon.hh on 2008-08-25
Hello everybody! I'm having a trouble:

It's there any way to stablish a policy to deny users to change gnome wallpaper? (excepting root of course).

The reason for do that it's because I belong to an Organizations and we have the instruction to use the Institutional wallpaper, but users change it all the time, I created a script that tracks this changes and reverts them, so no matter how many times the users try to change the wallpaper, it returns to the Institutional automatically.

The problem is that the script consumes plenty memory and processor resources. Of course I can re-write it and make it better, but before I would like to reseach for an easier way to do the same.

Then, can somebody help me?

---

### Post by leon.hh on 2008-08-25
Never mind, I allready found the answer:

gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.mandatory --type string --set /desktop/gnome/background/picture_filename *filename.png*

Executing this simple instruction as root and restarting X, cause that the wallpaper of every user is set to *filename.png* and the user is no longer able to change it!

---

