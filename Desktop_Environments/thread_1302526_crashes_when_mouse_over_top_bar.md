---
title: "crashes when mouse over top bar"
date: 2009-10-27
forum: Desktop Environments
---

### Post by DrLFToxic on 2009-10-27
hello. I am duelbooting ubuntu 9.10RC with Vista Ultimate.

My pc boots up into either os, no problem.


when in ubuntu, i can do anything on the desktop, be it open an image, mp3 or video. (I have not played with shortcuts through USB Pen yet..)

my problem is: When my mouse runs onto the top bar (with the menu's "Applications", "Places" and "System"), the system crashes out. any sound/video will stop playing, the only responsive thing left is the mouse cursor and the button config CTRL+ALT+F1~F12 (not assigned by me). when the key config is pressed, the OS will drop the shell, start audio playing again and give me a full screen terminal..like when it boots with no boot screen.

the most recently installed (but not working) app is Kiba-Dock.

what should I do?

---

### Post by lucaspr on 2009-10-27
Everything worked before tou installed Kiba-dock? If so, try uninstalling it!
From a terminal screen:

sudo apt-get remove kiba-dock

Or use synaptic to remove it!

---

### Post by DrLFToxic on 2009-10-27
> **lucaspr said:**
> Everything worked before tou installed Kiba-dock? If so, try uninstalling it!
From a terminal screen:

sudo apt-get remove kiba-dock

Or use synaptic to remove it!

sounds simple enough...but
```
sudo make install
``` didn't work, therefor it is not installed (or properly anyway) and will not run with my level of knowlege.

here is a video of what it does: [http://www.youtube.com/watch?v=l2YMF9tJoK0](http://www.youtube.com/watch?v=l2YMF9tJoK0)

---

### Post by lucaspr on 2009-11-03
sry for my late reaction. If make install fails. Then it should not run (?).

But even so try
```

sudo make uninstall

```

Maybe this does a little magic. Otherwise delete all files related with kiba-dock (BE CAREFULL!). 

Found another thread about uninstalling here (old, but maybe usefull!):
[http://ubuntuforums.org/showthread.php?t=657754&page=2](http://ubuntuforums.org/showthread.php?t=657754&page=2)

---

