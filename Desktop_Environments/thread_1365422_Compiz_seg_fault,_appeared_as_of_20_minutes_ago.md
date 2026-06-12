---
title: "Compiz seg fault, appeared as of 20 minutes ago"
date: 2009-12-27
forum: Desktop Environments
---

### Post by Omicron Machine on 2009-12-27
So I got a brand new laptop for Christmas (so I apologize in advance for typos due to things like a less-than sign where my shift key once was), because the old one had weird wireless problems, and everyone was sick of me agonizing over it. This one works fine, except for one thing. I install Ubuntu, start "moving in" and transferring things, downloading, setting up, etc. I get my compiz settings the way I like them and then move on to some other aesthetic aspects under Sys>Pref>Appearances. I accidentally activate the visual effects from there, and then immediately turn them back off. I go back into Compiz, recheck everything I want active. But now, it has no effect. When I use compiz --replace or compiz check, I get this error:

> Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: Segmentation fault
not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: Segmentation fault
not present. 
aborting and using fallback: /usr/bin/metacity 


The terminal window never gets back to the $ input prompt, and making it close seems to crash metacity because the window borders disappear and everything gets discombobulated (being, of course, a highly technical term) and I have to log out and log back in.

So, what fool thing did I just do to my nice, smooth, clean install?

---

### Post by Omicron Machine on 2009-12-27
I just made an extra user (I'm the only one on here) and went to try it out. Same result trying to edit the settings, same output from compiz check, same crash on exiting the terminal. Dagnabbit, right when I had it how I like.

---

