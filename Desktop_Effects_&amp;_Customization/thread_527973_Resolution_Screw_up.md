---
title: "Resolution Screw up"
date: 2007-08-17
forum: Desktop Effects &amp; Customization
---

### Post by uncleclinto on 2007-08-17
Hey peeps,

I hope I'm posting in the right forum.  I recently bought a new 19" Acer Monitor.  My 1024x768 screen resolution looked a little funky on it. I wanted to set my resolution for 1440x900.  I found a suggestion online that said I should go to the terminal and type "sudo dpkg-reconfigure xserver-xorg".  Then it suggested I "Go through the menus choosing the defaults and when given resolution options make sure to select the 1440×900 resolution. Once finished, restart X by hitting Ctrl+Alt+Backspace (save any unsaved work before doing this). Upon restarting the server the screen resolution should be set to 1440×900."

I did this with much trepidation because it asked a lot of questions I didn't know the answers to like horizontal refresh rate(??).  I chose the "defaults" and when it came to resolution I selected 1440x900.  I restarted the computer and now my screen is at 640x480 with no other options!!!  This is great for the visually impaired, but it looks like crap on this wide monitor.  Can I go back to default or my previous config somehow??  Please please please help.  I don't even know where to start.

Thanks,
Clint

---

### Post by blakegrover on 2007-08-17
When you reconfigure the xserver it backs up the configuration in the same directory /etc/X11, go into the directory and look for a file similar to xorg.conf, it should have the timestamp of when you ran the configuration program.  Just copy this file over the top of your existing xorg.conf and restart xorg again.

Blake

---

### Post by uncleclinto on 2007-08-17
Giddy up!  Thanks a lot.  I actually managed to get 1440x900 working.  I found a command to open a GUI Xorg config.  Your post was still a savior.  640x480 really sucks.  I had to scroll severaltimes to the right just to read your post, and it was brief.  Thanks a lot!!:-D

---

### Post by treetaxi on 2007-08-21
And just what WAS that gui xorg conf command?:confused:

---

