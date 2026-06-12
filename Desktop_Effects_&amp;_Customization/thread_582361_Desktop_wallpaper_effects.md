---
title: "Desktop wallpaper effects"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by yang on 2007-10-19
I currently run Gutsy and use wallpaper-tray to rotate among wallpaper, but I'm interesting in adding smooth fading transitions and slow panning.

I'm aware of one way to do this: use the glslideshow xscreensaver. I also had the idea of using KDE's Active Desktop feature to display a Flash page that displays the wallpaper with effects, but it seems people have successfully gotten the screensaver to work, and it's probably much more efficient/practical in that it uses OpenGL.

I read on this forum and on the web to either (1) use xwinwrap and/or (2) run the xscreensavers directly with the -root argument.

(1) I couldn't find xwinwrap on my system or in the repositories (using apt-file).

(2) I followed [http://www.winmatrix.com/forums/index.php?showtopic=15058&pid=148902&st=0](http://www.winmatrix.com/forums/index.php?showtopic=15058&pid=148902&st=0). I noticed that:

(a) running the gconftool command seems to only hide my icons while leaving my wallpaper there (maybe this is fine)

(b) running the screensaver (tried glslideshow and glmatrix) with -root renders the screensaver above everything else (as if it were a screensaver), but with some glitchy flashing of certain parts of certain windows. ctrl-c kills it, but leaves garbage on my screen, which I clear by forcing redrawing of the screen (e.g. by moving windows around). Pretty nasty.

My immediate hunch is that there is some unfriendly interaction going on between xscreensavers and Compiz Fusion. Any hints?

---

