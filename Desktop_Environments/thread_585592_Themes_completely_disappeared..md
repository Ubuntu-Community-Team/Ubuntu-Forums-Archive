---
title: "Themes completely disappeared."
date: 2007-10-21
forum: Desktop Environments
---

### Post by Sillee String on 2007-10-21
I have no idea how or even when, but I noticed that my computer automatically reverted to a barebones non-theme, so I decided to restart.  I was using Human (I'm a pretty brand new Ubuntu user) but when I restarted it said that it couldn't load it.  The Login screen wasn't themed, and when I logged in it still had the barebones look.  I decided to take a look at System > Preferences > Appearance only to see that all of my themes were gone.  I went to the folder where the themes are stored so that I can try to drag the .themes into the theme selecter, but I get an "Invalid file type" error.  Does anybody have any ideas as to what may have happened here?  I hadn't installed any new themes yet so what used to be there were there when I installed Ubuntu.  Thanks guys.

---

### Post by Happy_Man on 2007-10-21
Have you looked in both /usr/share/themes and in ~/.themes? That's where the theme files should be stored.... although the defaults are in /usr/share/themes. Go there with Nautilus and look.

---

### Post by Sillee String on 2007-10-21
The themes are in /usr/share/themes but not in ~/.themes.

---

### Post by Sillee String on 2007-10-21
Ahhah!  There we are.  Copies from usr/share/themes to /.themes and they're back.  Thanks alot :)

---

