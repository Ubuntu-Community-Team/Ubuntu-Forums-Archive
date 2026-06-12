---
title: "Gnome won't start because background not found?"
date: 2005-01-04
forum: Desktop Environments
---

### Post by jakeslife on 2005-01-04
I switched the splash image on the login screen, and when I restarted Gnome it said that it couldn't find the image path. I click OK and the dialog box won't go away. I looked at [this thread](http://ubuntuforums.org/showthread.php?t=4268&highlight=login+screen) and tried to change it from an old Beatrix CD I had laying around since Gnome wouldn't start and I have no idea what to do.

I'm trying to find the GConf key /apps/gnome-session/options/splash_screen, but I can't find where it is pointing to the certain image. What can I do to change this and get it back to the default?

---

### Post by jbh on 2005-01-04
this should work:

gconftool-2  --type string --set /apps/gnome-session/options/splash_image \
/usr/share/pixmaps/splash/ubuntu-splash.png

or instead you could have gconftool-2 point to /usr/share/pixmaps/splash/(yourfilename)

---

### Post by jakeslife on 2005-01-04
I fixed it...I changed something else to that file name and put it in the themes folder. Now I just need to figure out how to make my default browser (Firefix) run whenever I click a link in TBird...

---

