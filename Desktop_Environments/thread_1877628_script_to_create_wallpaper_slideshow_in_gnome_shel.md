---
title: "script to create wallpaper slideshow in gnome shell."
date: 2011-11-08
forum: Desktop Environments
---

### Post by gsgleason on 2011-11-08
Most of the solutions I found to create a custom slide show were cumbersome, so I wrote a little script to create wallpaper slideshow in gnome shell.

It will look for images in your current directory (not recursive), generate the xml file in that directory, then use gsettings to activate the slideshow.

I currently have it set for 30 minutes between images, but that can be easily changed.

If the xml file is already there, it will back it up with the unix timestamp.

---

