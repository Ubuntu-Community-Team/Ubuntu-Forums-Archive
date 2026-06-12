---
title: "Where are the screen resolution settings saved in Gnome?"
date: 2009-05-08
forum: General Help
---

### Post by learningcurb on 2009-05-08
While trying out some new settings with the Screen Resolution Manager, Xorg crashed and I was forced to reboot.  Now when I log into my main account, the video is highly distorted and I can't read any text. (I tried displaying 1680x1050 on a 1600x1200 monitor. Doh.)  I can still get a normal Gnome desktop by logging in as a different user, but I would like to preserve my original settings without copying everything over piecemeal or redoing them from scratch.

Where is the file that stores the settings created by the Screen Resolution Manager?  Can it be edited from a terminal? I am trying to find a way to edit this file manually from the terminal so I can restore my original resolution settings.  Someone on IRC said there should be a file called ~/.xession with these settings, but ls -la doesn't reveal one.  There are files called .Xauthority, .Xdefaults and .xsession-errors in my home directory, but they don't seem to be related to configuring the display.  I've rummaged though all the hidden files in my home dir and googled around without much success.  I've also tried looking at the files in /etc/X11, but they seem to be systemwide files and the other users are working fine at the moment.  Thanks in advance if you have any insight into this problem.

---

### Post by CatKiller on 2009-05-08
> **learningcurb said:**
> Where is the file that stores the settings created by the Screen Resolution Manager?

I believe it's stored in ~/.config/monitors.xml

---

### Post by learningcurb on 2009-05-09
Aha, that's where it is.  Thanks for the help!  It turns out you can switch the resolution by changing the values with a text editor.  I suppose you have to plug in valid values though, otherwise the login program might crash or damage your monitor...

---

