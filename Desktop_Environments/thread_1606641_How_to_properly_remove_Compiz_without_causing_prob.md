---
title: "How to properly remove Compiz without causing problems"
date: 2010-10-26
forum: Desktop Environments
---

### Post by spaceboy909 on 2010-10-26
Back again, with more problems.  :(  I just finished upgrading to the latest version offered in the upgrade panel, and every time I do, I always have more issues to sort out!

But this problem I apparently created myself, thinking that removing all of the Compiz items listed in Synaptic would get rid of the beast, but it also has removed certain necessary items from my application menu bars (min,max,X), disallowed me from dragging the window via the title bar, and covers up my taskbar/panel with unmovable application title bars!

I don't want Compiz because Linux has always been a resource hog even without it.  I was using Compiz switch, but that stopped working after my latest upgrade (and before my Compiz package removals)

Any help is appreciated!

---

### Post by 3Miro on 2010-10-26
There are couple of ways to handle compiz.

1. Lower its settings: You can install CCSM (compiz config settings manager) and then remove most of the options. I only have Move/Resize windows, the simple Alt+Tab switch, Desktop wall, View Port Switch and some of the "workarounds" and "compatibility" things. It works well on a fairly low end machine.

2. Remove it: Go to System -> Preferences -> Desktop Effects and select "None".

Compiz is actually an important part of your system, simply removing it is not the right thing to do. You have to replace it with something lighter. The something lighter is called Metacity. You can hit Alt + F2 and type
```
 metacity --replace 
```
This is equivalent to desktop effects being set to none, except it will be temporary until you reboot (or type compiz --replace).

---

