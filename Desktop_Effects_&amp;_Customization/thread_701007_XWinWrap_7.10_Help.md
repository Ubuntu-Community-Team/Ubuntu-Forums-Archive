---
title: "XWinWrap 7.10 Help"
date: 2008-02-18
forum: Desktop Effects &amp; Customization
---

### Post by xtothez on 2008-02-18
I checked the posts about this, but can't find any luck. I have Ubuntu 7.10 GG w/ Compiz and Emerald themes installed and am trying to run XWinWrap so I can have an animated desktop running. I have a Dell D610 laptop w/ all drivers installed, but when it runs it only shows the glmatrix on the screen above everything. If I do the ring switcher, alt+tab, etc it shows the window running briefly, but then the matrix covers it back up. Does my videocard not support it? I'm not too used to Ubuntu, but would appreciate any help. Here is the command I run in alt+f2:
xwinwrap -ni -argb -fs -s -st -sp -nf -b -- /usr/lib/xscreensaver/glmatrix -window-id WID

Hopefully someone has had the same problem?

*I should mention that I have Windows XP on a 2nd partition, with a permanent icon on the desktop I cannot remove, it could have errors with it?

---

### Post by tact on 2008-02-18
I had weird problems getting xscreensavers to run with xwinwrap on my Dell D410 too.  Movies would play perfectly on the desktop behind all other windows like animated wallpaper - but screensavers, no.

---

### Post by xtothez on 2008-02-18
Hey tact,
Did it only work with the mplayer and .mpg? I might have to settle on that :(

---

### Post by tact on 2008-02-18
> **xtothez said:**
> Hey tact,
Did it only work with the mplayer and .mpg? I might have to settle on that :(

Yep kinda like that...  Only worked with mplayer and video files...  (not just mpg - worked with avi etc as well).   Couldn't get any screensaver to behave.

Don't know if its a "feature" of my video card, drivers, whatever.   I have never tried to modify or enhance my video drivers etc.  Just using whatever the default Gutsy set up for me at install time.

---

### Post by xtothez on 2008-02-18
What command did you enter in alt+f2 to start a .mpg? on /home/xzhibit/pyre.mpg is where my video is located hence:
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf mplayer -wid WID -quiet /home/xzhibit/pyre.mpg
but it will not work, any ideas? I have a plain initial background w/ the SDA1 (XP) icon still on the desktop.

---

### Post by Triggerhapp on 2008-02-18
If youre using intel graphics drivers... This might be why.
[http://ubuntuforums.org/showthread.php?t=649651](http://ubuntuforums.org/showthread.php?t=649651)

---

### Post by xtothez on 2008-02-18
Yeah, it does it when videos are playing and I rotate the cube as well. Hopefully someone has an answer to it, I really want it to work. I did get the .mpg to work in the background, haven't got it to loop yet. But I really wanted to get the xscreensavers to work, quite a few cool ones that look interesting.

---

### Post by Triggerhapp on 2008-02-18
If its the same bug im experiencing, I must say theres no obvious end in sight from our view.
Its not something as simple as a command line fix away, I can tell you now.

---

### Post by tact on 2008-02-19
> **xtothez said:**
> What command did you enter in alt+f2 to start a .mpg? on /home/xzhibit/pyre.mpg is where my video is located hence:
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf mplayer -wid WID -quiet /home/xzhibit/pyre.mpg
but it will not work, any ideas? I have a plain initial background w/ the SDA1 (XP) icon still on the desktop.

This works for me....
xwinwrap -ni -o 0.6 -fs -s -st -sp -b -nf -- mplayer -vo x11 -wid WID -quiet "/home/login_name/movies/your_movie.avi"

Some guides say you have to go into gconf and turn off desktop etc...  but I find thats not needed.  So with my normal desktop, normal wallpaper, etc...  I run that commandline above and I got a movie as a desktop.

---

