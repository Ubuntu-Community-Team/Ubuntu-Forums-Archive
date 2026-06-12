---
title: "Question about Desktop background?"
date: 2010-08-19
forum: Desktop Environments
---

### Post by hakermania on 2010-08-19
Well, When I change Desktop background, the location to the image I choose have to be written somewhere, to a file e.g. ...

So, if I edit this file and set an other path to an other image the Desktop background will change hopefully...
So, where is this file?

---

### Post by mcduck on 2010-08-19
It's one of the gconf's XML files in ~/.gconf, but you shouldn't really change the file itself manually. If you want to change the wallpaper from command line or from a script you can use the gconftool command.

Edit:

Here's an example:
```
gconftool-2 --type string --set /desktop/gnome/background/picture_filename "/home/mcduck/Pictures/wallpapers/ubuntu.png"
```

---

### Post by hakermania on 2010-08-19
Thankssssssss pre-installed !  CooL

---

### Post by chitowner2 on 2010-08-19
FYI, you can choose any image you like for a background. I have a (growing) collection that I keep in a known folder. When I find a new image I want to use as a background (aka "wallpaper"), I just add it to that folder.

Do a right-click anywhere on open desktop area, go to desktop settings, navigate to your established background folder and pick one. 

The only thing to remember is: if you change the path to your backgrounds folder, you will lose the desktop display, so choose a path accordingly.

CT

---

