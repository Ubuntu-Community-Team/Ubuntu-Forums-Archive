---
title: "How do I edit the menu on the OSX-like menubar (KDE)?"
date: 2007-12-10
forum: Desktop Effects &amp; Customization
---

### Post by IanVonSpeedfreak on 2007-12-10
Okay, so I'm having this problem with the Mac-style menubar in Kubuntu.  You see, as I was editing the menubar I decided to remove all the applets, so I could reorder them the way I wished, problem is when I removed the clock applet, the menubar shifted the text menu to the right and I haven't been able to get it back to the left.  I've tried moving icons around, restarting the computer, and I even tried setting it to the default.  I've found that using this command:
```
dcop kicker kicker restart
```
actually gets the menubar fixed temporarily, but the right-aligned menu is restored soon afterwards.  I'm guessing there's a way to manually fix this (i.e. using the command line to edit some .conf or other text file), but I don't know what document works with the menubar.  I can't recall the name of the thread, but I remember someone having a similar error and reporting it as a bug, does anyone know how to fix this?

I'd also like to get rid of that last kicker panel without losing the ability to add applets to the menubar.  Here's a [[COLOR="Green"]link[/COLOR]]("http://DanSpeedfreak.fileave.com/fixedsnapshot1.png") to the screenshot of my current desktop.

Much thanks in advance, especially if this happens to be one of my d'oh moments...

edit: I have now solved problem A, all it really took was using a workaround involving adding either the Settings or KMenu applet and then moving it so the menu would shift around it (I say only Settings or KMenu b/c they are the only applets that you can move).  For those out there who wish to implement this solution, be forewarned that it works best if KMenu or Settings is currently the only applet on the menubar, you can some more later, but if you try to fiddle with it while Quick Launcher or some other applet (including the clock) is enabled, chances are that applet will also be shifted to the left with the menu following it.  If my instructions aren't clear enough, ask me and I'll try to explain things more clearly.  Anyway, I haven't marked this problem as solved yet b/c I would like to see if someone has found a solution for problem B (i.e. actually getting rid of the final kicker panel w/out eliminating all of my nice little applets).  I know you can set the transparency so you can't see it and you can also shrink it and set it to be hidden behind other windows, but I'm hoping for a real solution, not just a workaround in this case.  I'd like it so the panel is entirely gone.  Also, how do I change the font (more especially, the font color) on the menubar?

---

