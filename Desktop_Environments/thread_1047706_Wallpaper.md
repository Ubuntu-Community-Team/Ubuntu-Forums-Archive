---
title: "Wallpaper"
date: 2009-01-22
forum: Desktop Environments
---

### Post by theozzlives on 2009-01-22
How do you switch walpaper at random. There's gotta be a program.

---

### Post by gettinoriginal on 2009-01-22
Here's one for you :p
[http://drapes.mindtouchsoftware.com/](http://drapes.mindtouchsoftware.com/)

---

### Post by 2hot6ft2 on 2009-01-22
wallpaper tray
```
sudo apt-get install wallpaper-tray
```in a terminal
Applications>Accessories>Terminal
then it will be in
Applications>Graphics>Wallpaper Tray

---

### Post by MikeBrown on 2009-01-22
Here's a posting on this forum about a similar subject: [http://ubuntuforums.org/showthread.php?t=534455](http://ubuntuforums.org/showthread.php?t=534455)

If I remember correctly, wallpaper tray was easier to use than Drapes. Or more preferable to what I wanted.

---

### Post by theozzlives on 2009-01-22
Wallpaper Tray works good but my text in my panels is red and my panels are trasparent. Any way to change that automagically?

---

### Post by gettinoriginal on 2009-01-22
You can install "gnome-color-chooser", it allows changing the color of font and background of the panel.

---

### Post by shane2peru on 2009-02-08
Wallpaper-tray seemed to work for me.  Although I didn't quite understand it's option of choosing a background folder, and then it would say it didn't have any pictures as backgrounds after I had choosen a directory full of Pictures I use for backgrounds?  Odd, any rate after selecting a few backgrounds it worked fine.  

Drapes on the other hand didn't work for me.  I don't know why, it wouldn't automagically change backgrounds and disappeared from the Notification area.  Perhaps you are supposed to put it on the panel, not sure, but it didn't like my setup.

I'm using Ubuntu Intrepid 64bit.  All up to date, for the record.  

Shane

PS - Gnome desktop. :)

---

### Post by pbotros1234 on 2009-02-08
This is a script that I stumbled upon awhile ago that changes your wallpaper to a random wallpaper in a given directory.

```
#!/usr/bin/env python

BACKGROUND_DIRS = ['~/PATH/TO/WALLPAPERS,~/PATH/TO/WALLPAPERS/2']

import os, glob, random, itertools, gconf, subprocess

files = list(itertools.chain(*[[os.path.join(dirpath, name)
                                for name in filenames]
                               for dirpath, dirnames, filenames in
                               itertools.chain(*[os.walk(os.path.expanduser(d))
                                                 for d in BACKGROUND_DIRS])]))
gconf.client_get_default().set_string(
    '/desktop/gnome/background/picture_filename',
    random.choice(files))

```

You can have as many directories as you want, just separate by commas. This script makes it perfect to be linked to a keyboard shortcut, so you can change your wallpaper with a random keypress.

---

