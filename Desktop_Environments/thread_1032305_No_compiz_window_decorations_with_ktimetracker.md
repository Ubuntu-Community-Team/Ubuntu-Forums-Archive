---
title: "No compiz window decorations with ktimetracker"
date: 2009-01-06
forum: Desktop Environments
---

### Post by rubberglove on 2009-01-06
This has been bugging me for a while. I really like ktimetracker for tracking my work hours, but since the app changed from karm to ktimetracker, I get no window decorations or borders on the application when using compiz (in gnome). Also, left-clicks on the ktimetracker window seem to be read as right-clicks.

The problem is the same using gtk-decorator (what I usually use) or emerald. I don't have this problem with any of the other kde4 (or kde3) applications that I use under gnome, just ktimetracker... 

I've tried using quite a few alternatives (including gnotime), but ktimetracker just does what I need it to do. Using it without borders/decorations is a bit tedious, though. 

Is this likely a compiz bug or a ktimetracker bug... or is there some magical workaround that I am missing? 

In CCSM, 'Decoration Windows' and 'Shadow windows' are both set to 'any'.

---

### Post by 1awesomeguy on 2009-01-15
I am having the same problem. When KTimeTracker was still called KArm, this was not a problem for me either. What I end up doing is just clicking on the taskbar button to make the application go away until I need it. This is still very annoying, so if anybody has any suggestions, I would also greatly appreciate it.

---

### Post by rubberglove on 2009-01-18
Note -- if you want to move the ktimetracker window around, you should be able to alt-click on the window and drag it around.

but yes, this is still annoying. Glad to hear at least I'm not alone ;-)

---

### Post by essgrocott on 2009-03-31
Found a solution by mistake - 
sudo apt-get install alltray
Start up ktimetracker
use alltray to dock ktimetracker into the system tray
right-click on the alltray/ktimetracker system tray icon
undock
decorations restored
smiles and backslapping all around

---

