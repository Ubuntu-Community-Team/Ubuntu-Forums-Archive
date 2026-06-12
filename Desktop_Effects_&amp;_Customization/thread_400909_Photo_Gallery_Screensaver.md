---
title: "Photo Gallery Screensaver"
date: 2007-04-04
forum: Desktop Effects &amp; Customization
---

### Post by duckeo on 2007-04-04
I'm having trouble setting up a simple slide show style screensaver in Ubuntu.

I've populated the pictures folder, the pictures are displayed but the screensaver is auto-resizing the images to fit the screen. Are there any options for this that I can customise? 

I'd like the images to stay the same size, and if possible customise the transition effects as well (it's currently too slow :) )

---

### Post by mgmiller on 2007-04-04
Unfortunately, the current gnome screen saver has lost most of it's old abilities.  Search these forums for gnome screen saver and you can find out how to install the old screen saver that allows you to set up all that stuff.

---

### Post by fakie_flip on 2007-08-11
How is it possible to get gnome-screensaver to look in another directory besides ~/Pictures for the screensaver? I've looked in gconf, but no luck yet.

---

### Post by leoaln on 2007-08-12
sudo nautilus

Navigate to /usr/share/applications/screensaver

Right click on" Pictures folder" icon and select Properties

Select Launcher tab

Command should read  "slideshow --location=full path to folder where your photos are

Close everything out and you should be good to go

Leo

---

