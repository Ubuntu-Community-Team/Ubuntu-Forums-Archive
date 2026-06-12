---
title: "gnome screensaver configuration question"
date: 2006-12-04
forum: Desktop Environments
---

### Post by praxis22 on 2006-12-04
Hi,

Dumb question, but is there any way to configure the "Pictures folder" screensaver? I want to increase the speed at which the screensaver changes pictures, and have a static transition from picture to picture, no fade, nothing fancy.

Any Ideas? 

/usr/share/applications/screensavers/personal-slideshow.desktop doesn't appear to contain much of any use as regards the above, is there another config file I can tweak?

**Update** The answer would appear to be use xscreensaver :)

sudo apt-get install xscreensaver

launch xscreensaver and pick glslideshow tweak it's settings to your liking in the "advanced" section. Then save out the resulting command line.

in my case:

glslideshow -root -duration 2 -zoom 100 -pan 0 -fade 0 -delay 0

Then edit the gnome slideshow settings:

sudo vi /usr/share/applications/screensavers/personal-slideshow.desktop

and change the following two lines, (at the end of the file) thus:

Exec=glslideshow -root -duration 2 -zoom 100 -pan 0 -fade 0 -delay 0
TryExec=glslideshow

Save the file and then go to the gnome screensaver and try it out.

---

