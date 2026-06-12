---
title: "Don't want KDE apps to appear in Gnome, vice versa"
date: 2008-06-29
forum: Desktop Environments
---

### Post by VicAlpha on 2008-06-29
How to do that?

---

### Post by eniel on 2008-06-29
Take a look at the following link:

[http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/](http://ubuntu.wordpress.com/2006/01/13/ubuntu-to-kubuntu-keeping-the-menus-clean/)

You can find the .desktop files in /usr/share/applications 
and /usr/share/applications/kde

Those files determine amongst others how the application is shown in the menus. You can add the line
OnlyShowIn=GNOME;
or
OnlyShowIn=KDE;
to the desktop file.
Take a look at nautilus to see how this works:
 sudo gedit /usr/share/applications/nautilus.desktop 
(doubleclicking on the file will start nautilus)
you'll see a line OnlyShowIn=GNOME;

---

