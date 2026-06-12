---
title: "Disabling KRunner Sound"
date: 2009-05-23
forum: Desktop Environments
---

### Post by Manslen on 2009-05-23
Hello,

Every since I've moved from KDE 3 to 4, I've had KRunner produce a series of annoying beeps when I type in it.
The beeps occur only once KRunner starts auto-completing my typing (i.e. typing the first two letters in KRunner do not emit sound), and upon every following keystroke.

I've looked all over KRunner and google for the answer, but found nothing.

Any ideas would be warmly welcomed.

---

### Post by ckonestroh on 2009-05-23
Go to Preferences > Sound 


or your going to have to go to gconf-editor to disable sound....

good luck....


Dont know how many options there are going to be in gconf-editor either in 

apps or go to Desktop> Gnome > Sound > turn off event sounds....

---

### Post by Manslen on 2009-10-18
The reason the beeps occur is because KRunner finds multiple matches when you start typing (same as if you would type it in the shell and hit tab). Of course, this is a completely stupid behaviour for KRunner to do.

It is possible that by disabling some of the KRunner plug-in modules this might go away. I solved the problem by disabling the partial matching sound. This can be done by going into system settings -> notifications and selecting "KDE System Notifications" in the Event Source drop-down. Then disable the Textcompletion: Partial Match entry.

---

