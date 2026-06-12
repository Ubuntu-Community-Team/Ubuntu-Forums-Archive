---
title: "Teewars images error"
date: 2008-01-01
forum: Gaming &amp; Leisure
---

### Post by omega_user on 2008-01-01
I recently have been playing Teewars (one of the best games ever).  However, after only a little while, when I would start the game from the standard Lin-0.3.2 executable, the game would load, but all images wouldn't, leaving just blank white rectangles for everything [including text].  I searched on the Teewars.com forums, but there was only one post there and it was regarding the Windows version.

I know this is the wrong place to be asking, but if anyone has any ideas that would be much appreciated

---

### Post by Ardrias on 2008-01-01
I had the error when I moved the directory and made a launcher for it. It didnt like being run like that, so instead I made a bash-script that put me in the games directory and ran the app. Has worked since.

---

### Post by omega_user on 2008-01-01
Okay I solved the problem.  Any renaming or changing of the location of the parent directory screws up the config files Teewars auto-makes in /home/NAME/.teewars  To fix the problem if it arises, just delete the .teewars directory in your home folder, start up teewars and it'll be fine.  Your character will be lost and your settings too, but just don't move the directory afterwords and you'll be fine

---

