---
title: "Gnome session splash screen"
date: 2005-09-04
forum: Desktop Environments
---

### Post by Owdy on 2005-09-04
How do i change that? 
Tryed: [http://art.gnome.org/faq.php#q8](http://art.gnome.org/faq.php#q8) , aint working.

Utumbu default is gone, but now i see some gray default gnome sreen.

---

### Post by bin on 2005-09-04
Browse to:-

/usr/share/pixmaps/splash

There's a symlink called ubuntu-splash.png

By default it points to ubuntu-sparkles.png. If that link is broken or points somewhere else that would explain your problem.

sudo ln -s /usr/share/pixmaps/ubuntu-splash.png /usr/share/pixmaps/ubuntu-sparkles.png should do it.

in light

bin

---

### Post by Owdy on 2005-09-04
Its in there, with that gnome image. But i dont want ubuntu one, i wanna totally new one :) Where do i change that?

---

### Post by bin on 2005-09-04
So, grab the image you want - say from gnome-look or wherever. Put in in usr/share/pixmap/splash and link to it from ubuntu-splash.png

in light

bin

---

### Post by Owdy on 2005-09-04
Link to it *from* *.png? Now i dont get this. Wher do i change this link setting?  :)

There are that gnome-splash.png and that is showing in logging. What that blue arrow means in ubuntu-splash.png, btw?

---

### Post by Owdy on 2005-09-04
Found it: settings -> apps -> gnome sessions -> options -> splash image

Okay, next issue, where are those icons what are loading over that splash image?

---

### Post by Perfect Storm on 2005-09-04
They are part of the icon themes. So if you want other icon(s) you have to find the icon theme at gnome-look.org or art.gnome.org
Another option is to find them at /usr/share/piximaps and change them with your prefered icons.

---

