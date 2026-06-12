---
title: "How to restore Menu Bar in Gnome"
date: 2007-01-10
forum: Desktop Environments
---

### Post by mrzippy on 2007-01-10
I was trying to customise the Menu Bar using System > Preferences > Menu layout now the Applications menu is empty!

How do I reset this, dragging a new Menu Bar to the Panel makes no difference.

I get the felling I need to replace the file I have messed up, if I knew where it was and what it was called!

The Menu Layout app now exits immediately on launch, so I cannot do anything there.

---

### Post by mrzippy on 2007-01-10
I launched the Menu Layout editor in Terminal, that gave me the name and location of the file!

/home/neil/.config/menus/applications.menu

I fixed the error in it, and I was done :)

---

### Post by bageh on 2008-03-12
I've had this problem and got may applications menu again, but I'still can't have my menus System->Applications/Preferences back!
I tried to reinstall a lot of things, but nothing works!

Please, help!

---

### Post by chrinabuntu on 2008-03-12
I accidentally deleted the Applications and Places items on my Ubuntu Panel and cannot get them back either.  I thought it would be simple enough...but it is not.  The searches I've done on the forums have not really come up with this exact solution (not that I have been able to find anyway).  mrzippy's problem doesn't seem to be exactly the same as mine.  I can't get to any of my applications or places now at all.

---

### Post by tad1073 on 2008-03-12
right-click on panel>add to panel>look for menu bar

---

### Post by sujoy on 2008-03-12
open terminal, type alacarte, it will open the menu editor where from you can set up the menu again :)

---

### Post by eneth80 on 2008-03-25
> **chrinabuntu said:**
> I accidentally deleted the Applications and Places items on my Ubuntu Panel and cannot get them back either.  I thought it would be simple enough...but it is not.  The searches I've done on the forums have not really come up with this exact solution (not that I have been able to find anyway).  mrzippy's problem doesn't seem to be exactly the same as mine.  I can't get to any of my applications or places now at all.

To restore Allpications, Places, System:
right click on the panel, Add to panel, double click on Menu Bar

---

### Post by kimbaudi on 2008-04-06
-sol0matrix- said "to remove gnome panel completely just delete gnome-panel from your /usr/bin/ folder keep in mind that you might need it at an later time so make a copy of it"

Another solution to remove gnome panel completely using the terminal is to do the following:
1. Press ALT+F2 and type 'gnome-terminal' to access the terminal
2. type 'gnome-session-remove gnome-panel' and press ENTER

If you deleted the panel and would like to restore it, follow the two step above and in addition do the following:
3. type 'gconftool-2 --recursive-unset /apps/panel' and press ENTER
4. type 'gnome-panel &' and press ENTER

I just installed Ubuntu a few days ago and found this solution when I purposely deleted the top panel while messing around with this awesome software. I found this solution at [https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/7759](https://answers.launchpad.net/ubuntu/+source/gnome-panel/+question/7759)

Hope this helps somebody...

---

### Post by aeacides on 2008-04-07
Another workaround exist:

Go to:

*/etc/xdg/menus*

Then you should see:
*applications.menu.orig.dpkg-new*

Copy/paste it to your */home/<usr_id>/.config/menus/*

and rename it *applications.menu*

I searched a lot for this. I don't know if it helps you, but I know lots of people got problems with alacarte.

Src:
[http://forum.ubuntu-fr.org/viewtopic.php?id=199923](http://forum.ubuntu-fr.org/viewtopic.php?id=199923)


Xavier

---

