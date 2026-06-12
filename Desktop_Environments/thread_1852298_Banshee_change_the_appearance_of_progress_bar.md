---
title: "Banshee: change the appearance of progress bar"
date: 2011-09-29
forum: Desktop Environments
---

### Post by Idefix82 on 2011-09-29
I would like to slightly change my [Slickness Green]("http://gnome-look.org/content/show.php/Slickness+Green?content=142782") GTK2 theme. Namely, I would like to change the appearance of the progress bar slider in Banshee, which you can see at the top of the screen shot. How would I go about doing that? Where does Banshee look to find out how to render this slider?

---

### Post by hhh on 2011-09-30
Normally that's handled by color hex codes in the theme's gtk-2.0/gtkrc file located in the theme's folder, either in /usr/share/.themes or in ~/themes. But you were good enough to link the theme so I could look at it, here's what I found... the progressbars (and matching scrollbars) are handled by image files, which means you'll have to open them with GIMP (or similar) and do some color-shifting (Colors>>Hue-Saturation>>Hue).

That's going to change the color of all progress bars, there's no easy way to do it just for Banshee.

---

### Post by Idefix82 on 2011-09-30
Thanks very much! I seem to remember from the light themes that it is possible to give the part of the bar that signifies time elapsed a different colour from the time remaining part. Do you happen to know which files are used for what parts of the bar?

---

