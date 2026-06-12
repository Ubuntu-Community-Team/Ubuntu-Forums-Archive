---
title: "Little Nautilus Window during startup--change color?"
date: 2007-06-06
forum: Desktop Environments
---

### Post by timzak on 2007-06-06
I'm not sure what this window is called, but as your system is starting up and the desktop first appears, a little tan rectangular window pops up in the center of the screen that seems to show Nautilus loading up.  This window then goes away when the desktop is done loading.

Is there a way to control the color of this window?  I've changed my desktop colors away from the brown/tan theme but this is the only holdover that stays tan and as briefly as it appears, still clashes with my color scheme.  

Not a huge deal, but I thought if there was a way to do it, I might as well.

Thanks.

---

### Post by roastdawgg on 2007-06-06
i too would like to know about this window. I have searched all around Ubuntu and can't find anything.

---

### Post by mcduck on 2007-06-06
You are talking about Gnome's splash screen.

You can use any image, just put it into /usr/share/splash and then either remove the old symlink to ubuntu-splash.png and create a new link from your splash image that points to same file ('sudo rm ubuntu-splash.png' to remove the old link, and 'sudo ln -s yourimage.png ubuntu-splash.png' to link your file) or open Configuration Editor (Alt-F2 and run gconf-editor) and change the key apps/gnome-session/splash_image to point to your image.

---

### Post by hummingbird59 on 2007-06-19
Thank you for this Q&A.   I too have been trying to figure it out for a while.  BTW, my image was in usr/share/pixmaps/splash and the sudo instructions did not work.  The GConfig worked beautifully.  Thanks again!

---

