---
title: "Many problems after installing XFCE"
date: 2008-07-22
forum: Desktop Environments
---

### Post by spaceboy909 on 2008-07-22
I originally was using Gnome on Ubuntu-Hardy.  I then tried installing XFCE via synaptec, but that didn't work.  So I tried  via apt, and that worked, sort of, but now I have all kinds of problems.  I'm hoping there's one or two simple solutions for all of these, otherwise, I'll just have to go back to gnome.

Here's a short list of the problems that I've kept track of.  It's not all of them though.

* Error message: ```
 "Unable to quit session.

Quitting the session requires that Xfce's session manager (xfce4-session) is running, but it was not detected.  Please quit Xfce via another means."
```* Some applications installed in gnome don't appear in XFCE, such as Konqueror.  I know that's a KDE based app, but why wouldn't it carry over?  It shows up in the app list for XFCE.

* Lost user prefs, such as browser prefs/bookmarks, and Pidgin info, and other things.

* Save locations have been altered, such as my default browser save location was the desktop for gnome, and now it's 'root'...........somewhere.......

* The "Move to Trash" option in the right click menu has disappeared, and some files that I have downloaded via XFCE even have the 'delete' option greyed out so I'm stuck with them!

* At least one of my codecs seems to be missing or non-fucntional, FLAC.  VLC won't even play it now.

* File transfer status box is missing when dragging files from ROM drive to hard disk.

* (Solved.......I think...)  Missing taskbar/panel.

Like I said, this is the short list, and I'm already going crazy!  Is this because XFCE was not my original installed desktop, or is this what every XFCE user has to deal with?

If there's no magic fix for this, then I'll have to go back to gnome, as I don't have time to babysit a new desktop with all the stuff I have to do.

Any help is much appreciated!

---

### Post by spaceboy909 on 2008-07-22
bump!  Any ideas?

---

### Post by snowpine on 2008-07-22
Hi Spaceboy, please describe exactly what you installed (xubuntu-desktop, xfce4, something else).

It sounds like maybe you are trying to run xfce from within ubuntu somehow. The correct method is to restart the computer, then at the login screen (gdm) click on 'sessions' and choose xfce. Does that help?

---

### Post by snowpine on 2008-07-22
ps if you already have ubuntu and want go get xubuntu, which is ubuntu+xfce, 'sudo aptitude install xubuntu-desktop' or 'sudo apt-get install xubuntu-desktop' is the easiest.

---

### Post by spaceboy909 on 2008-07-22
> **snowpine said:**
> ps if you already have ubuntu and want go get xubuntu, which is ubuntu+xfce, 'sudo aptitude install xubuntu-desktop' or 'sudo apt-get install xubuntu-desktop' is the easiest.
That's how I installed it.

I'll try your other suggestion just to make sure I'm loading it right.  I'm pretty sure I selected xfce session, but I'll try again.

---

### Post by mali2297 on 2008-07-24
> 
* Lost user prefs, such as browser prefs/bookmarks, and Pidgin info, and other things.

* Save locations have been altered, such as my default browser save location was the desktop for gnome, and now it's 'root'...........somewhere.......


Might you have logged in as another user? (root?)

To find out, open a terminal and type
```
whoami
```

---

