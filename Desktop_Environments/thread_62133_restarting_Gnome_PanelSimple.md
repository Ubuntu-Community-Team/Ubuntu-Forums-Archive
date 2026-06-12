---
title: "restarting Gnome Panel**Simple ?**"
date: 2005-09-03
forum: Desktop Environments
---

### Post by tamarku on 2005-09-03
I'm very new to ubuntu/linux, so I'm not sure how to do this and can't find anything in the forums.  There have been how-to's say to stop the gnome-panel.  I can get that far but how do I get started again?  When it stops I get a black screen that seems to show the 'kill' and eventually I get a 'Login' prompt.  What do I do from here?  I can get logged in as my user but I can't seem to get gnome restarted?? 

Any help would be greatly appreciated.  THANKS!!

---

### Post by trash on 2005-09-03
Gnome-panel is just the panels at the top and bottom of your desktop. to restart those in a terminal you type:
killall gnome-panel

It sounds to me like you killed the gdm(desktop/gnome) and you end up at a terminal(black screen)... if so, like you did, login and then type startx.

hope that helps.

---

### Post by tamarku on 2005-09-03
Yep I think that is what I did thanks for the help!!

---

