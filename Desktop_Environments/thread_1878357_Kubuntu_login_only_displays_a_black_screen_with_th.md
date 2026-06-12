---
title: "Kubuntu login only displays a black screen with the mouse pointer"
date: 2011-11-09
forum: Desktop Environments
---

### Post by mansonthomas on 2011-11-09
Hi,

  I've not used my kubuntu for approximatively 2 or 3 days as I was playing GTA IV on my windows partition. At last logon, I did a aptitude update;aptitude full-upgrade. I'm using Kubuntu 11.10 with a Nvidia 8800 GTX on a core2duo.

  I've boot on it tonight, I found the overall boot quite slow compared to every days, I get the login screen properly in the correct resolution, enter login password, I've the animation that display the loading of components, a bit slower than usual, and then I get the black screen with the mouse pointer, which move. right click clik doesn't do anything. 

hitting any keys of the keyboard do nothing.

 I've logged on a console (CTRL+ALT+Fx) and check the logs but didn't find anything obvious...

  Any idea of how to debug that ?

---

### Post by mister_playboy on 2011-11-16
I had a similar problem after recent updates (I ended up with the default wallpaper and the cursor, but nothing else) and I was able to solve the issue by deleting the ~/.kde folder.

This will require you to have to rebuild your desktop panel and kickoff favorites menu, but I found that took less time than trying to solve the problem more elegantly :P

---

