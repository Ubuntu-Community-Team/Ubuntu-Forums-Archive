---
title: "Mplayer Video Unable to Resize Problem"
date: 2005-10-15
forum: Desktop Environments
---

### Post by Anchovie on 2005-10-15
When using Mplayer to play video files and DVDs, I tried to resize the screen by right click on the picture and then click on Double Size or Full Screen, however only the window size changes, but the picture stays the same, anybody have any idea on the fix? Thanks.

---

### Post by rejser on 2005-10-15
it is probably set to x11 instead of xv. 
try running from commandline with
"gmplayer -vo xv"

---

### Post by Anchovie on 2005-10-15
[QUOTE=rejser]it is probably set to x11 instead of xv. 
try running from commandline with
"gmplayer -vo xv"[/QUOTE]
Good call! It fixed the problem, thanks!

---

### Post by rejser on 2005-10-15
you can change it under settings somewhere, don't remember where though
have all movie files to autorun mplayer -vo -xv (no gui)

---

### Post by weblars on 2005-10-15
You can edit the config file in the ~/.mplayer directory.
Just add the line

```
vo = xv

```

---

### Post by lycan on 2005-10-17
hay im a noobie on ubuntu thanx for the help .....

---

