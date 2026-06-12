---
title: "Gnome issues?  Can't log in"
date: 2008-02-01
forum: Desktop Environments
---

### Post by mcgodx on 2008-02-01
I just turned my computer on after a trip to SC and back, and tried logging in to Gnome.  It wouldn't work, right after I put in my credentials, it'll show the terminal (appears like the computer is shutting down) then it'll show the nVidia logo and then it'll show the log in window again.

I figured maybe the hard drive got busted up, so I checked the physical integrity of it, and it had no problems.

So...  I installed KDE using apt-get in runlevel 3.  It worked, but I really can't stand KDE so I don't want to use that.  I removed gnome and then installed it again.  It still does the same thing.

Does anyone know of a fix for this other than reinstalling Ubuntu?

---

### Post by raul_ on 2008-02-01
It seems there is something wrong about your configuration. Try renaming .gnome folder in your home directory to gnome_old or something, and see if it works.

---

### Post by mcgodx on 2008-02-01
I just gave that a shot, but it appears the same problem persists.  There are a few other folders in there as well, called .gnome2 and .gnome2_private.  When I tried to log in to Gnome there was no recreated .gnome folder that was generated, if that helps any.

---

### Post by raul_ on 2008-02-02
Well, i'm no expert. Try the same thing with gnome2 and anything with gnome in it. and gconf too (be sure to rename it only, not delete it). The idea is to force gnome to create a new configuration folder, and see if the problem was in some obscure config file

---

### Post by mcgodx on 2008-02-02
Well your tip did force it to make new configuration files, I can tell by the default login sound.  However, it is still not working.  The log in noise will play now, when it should, however by that point, it's already logging me off.

---

### Post by raul_ on 2008-02-02
The weird thing is KDE working, otherwise i would say it's a video card issue

---

### Post by jazzgossen on 2008-02-02
I had the same problem after the latest  updates, and post #6 in [this thead]("http://ubuntuforums.org/showthread.php?t=678846&highlight=gdm+login") solved it for me.

---

