---
title: "Install succesfully, boots to login screen, will not load gnome..."
date: 2009-02-17
forum: General Help
---

### Post by beattyml1 on 2009-02-17
I recently bought  a computer and installed ubuntu on it, now it will boot to the login screen, but when I try to login gnome will not load, if I go into the failsafe terminal I can load most of the gnome functionality with following terminal commands
```
gnome-settings-daemon &
metacity & 
gnome-panel &
nautilus &
```

from there I have then tried playing around with the sessions, in fact I made it so that as far as the sessions manager is concerned the commands that I ran to start things up are the only commands run at startup.  But when I run:
```
gnome-session
```
it will display the desktop and then just quit on me if I remember correctly it said something about seahorse and nautilus (in the terminal) when it quit.  Thankfully this is further then I got when I first started, at first it just hung on the colored screen.  When I get the chance I'll try it again and post the terminal output of 
```
gnome-session
```
as I know that will probably be one of the first things asked, but for right this second I don't have the time to set up the system and boot  up and all.

Oh, yeah I just remembered  something else one time I had set gnome-session up to load a terminal as well and it did that successfully although I may have pu an end to it when I continued fiddling around

---

### Post by insineratehymn on 2009-02-17
Try uninstalling compiz. Can't say for gospel that will work, but I had a problem with gnome on a fresh 8.10 and that seemed to be the culprit. No proof that compiz was bad, just know that after I uninstalled it there were no more problems.

---

### Post by razy60 on 2009-02-17
How does it run just using the install CD? I had to install mine a couple of times before i got it to run sensibly.

Raz

---

