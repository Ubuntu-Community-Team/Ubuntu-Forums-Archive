---
title: "bottom panel bar"
date: 2007-03-21
forum: Desktop Environments
---

### Post by deafchickadee on 2007-03-21
My bottom panel went missing...   this is what i believe I am looking for

> Show the Computer, Home, and Trash desktop icons in GNOME

   1.

      Open the Configuration Editor, by running the program gconf-editor (see the run application manual for help on how to run an application without using the menu).
   2.

      Choose apps->nautilus->desktop.
   3.

      Turn on computer_icon_visible, home_icon_visible, and trash_icon_visible. The changes take effect immediately.

Where on earth do i find the configuration editor?

Pllllleaase!!!!

---

### Post by lizzard on 2007-03-21
In a terminal just type "gconf-editor"....

---

### Post by lassegs on 2007-03-21
Hehe, quite the problem youve got there. :D

But it sounds like its an easy fix.

All you need to do is:
 - Right click on your top panel.
 - Choose "New Panel"
 - Drag the new panel to where you want it
 - Right click on the new panel
 - Choose "Add to panel"
 - If you want the default look on the panels, add "Window list" and "Trash"

If this doesnt work for you, you could always run gconf-editor from a terminal (or alt+F2) and type in the command
gconf-editor


Good Luck!

---

### Post by mcduck on 2007-03-21
That gconf-editor thing is for enabling/disabling different icons on your desktop, and has nothing to do with your panels. Just follow the instructions lassegs gave and you'll have your panel back in no time :)

---

### Post by AZzKikR on 2007-03-21
Just wondering: what if both panels are gone, how does one add a new panel to the desktop, since there are no areas to right click -> add panel?

---

### Post by mcduck on 2007-03-21
> **AZzKikR said:**
> Just wondering: what if both panels are gone, how does one add a new panel to the desktop, since there are no areas to right click -> add panel?

You should not be able to remove last panel from your desktop.

---

### Post by girishv on 2007-03-21
Just open a terminal and type
gnome-panel &

the '&' is to put it in the background. And, it should be automatically start the next time.
Another easy way if you have completely messed up your gnome setup. Just login in to
a safe mode (just a terminal), remove the directories
.gnome
.gnome2
.gnome2_private

After logging out and into gnome, the directories are re-created with all the default settings.
THIS WILL REMOVE ALL YOUR MODIFICATIONS TO THE DESKTOP...

Girish

---

