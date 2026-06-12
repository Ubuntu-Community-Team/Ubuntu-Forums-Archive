---
title: "Top Panel Has Vanished!!!"
date: 2009-07-26
forum: Desktop Environments
---

### Post by jedimattk on 2009-07-26
I wasn't sure where this post fit, so I'm putting it here. Feel free to move it if you must.

Anyway, I seem to be facing a rather odd problem. I was trying to install VMware Player, and its icon wouldn't appear in the Applications > System Tools menu. I fiddled around with it for a while, although I didn't change anything of importance, and then restarted the computer in frustration. When Ubuntu loaded again, it was sans the top panel.

My only salvation is that I have AWN installed, and was able to open Firefox and a few other applications through the dock. I did a google search, looking for a quick fix, and found people who said that you could still access the applications menu by using ALT+F2 shortcuts and the like. I tried all the suggested keyboard shortcuts, but nothing works. I repeat, none of the ALT+F keyboard shortcuts wortk!!!

I now have no top panel and no bottom panel, and can only open the few applications I have on my dock. I've tried several things to fix it, and for a while there I was so annoyed that I actually went and dug out my Windows XP disc (fortuantely, I stopped myself before I could re-infect my computer with it.)

This is serious ... please help!!

---

### Post by ajgreeny on 2009-07-26
try Alt+F2 and enter **gnome-panel** in the box, or do the same in terminal (Alt+F2 and enter **gnome-terminal** if you have no menus) which will perhaps show any useful errors that may occur.  Post back if still no go.

---

### Post by jedimattk on 2009-07-26
Okay, the Alt+F2 keyboard shortcut DOES NOT WORK FOR ME, but I am posting a solution that did work in case anyone else has these problems. 

Right-click on the desktop and choose "Create Launcher." In the command box, type **gnome-panel**. Type whatever name you like in, and create. Then all you have to do is double-click on the launcher to get your panel back.

When you do get the panel back, go into System > Preferences > Startup Applications. Click the Add button and input the same settings you just did to create a launcher on your desktop. (In case you forgot, this means typing **gnome-panel** into the command box, and whatever name or comment you like into their respective boxes.)

Click Add, then close the window. You should now be able to delete the launcher from your desktop, and the top panel should load automatically when you boot Ubuntu, just like always.

---

### Post by ajgreeny on 2009-07-26
> Okay, the Alt+F2 keyboard shortcut DOES NOT WORK FOR ME, but I am posting a solution that did work in case anyone else has these problems.I'm glad you got it working, but the questions remain, why did it disappear in the first place, and why does Alt+F2 not work for you?  I would be lost without that on occasion, even though I could get things going with your work-around.

EDIT:
Just a thought.  If you are using compiz install compizconfig-settings-manager and when you open that make sure the Gnome compatibility plugin is enabled in the General list.  This will ensure Alt+F2 works again, I think.

---

### Post by [SomeGuy] on 2009-07-26
Could be something wrong with his key bindings.

---

