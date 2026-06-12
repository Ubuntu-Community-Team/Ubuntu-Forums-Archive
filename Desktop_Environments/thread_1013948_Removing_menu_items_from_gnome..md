---
title: "Removing menu items from gnome."
date: 2008-12-17
forum: Desktop Environments
---

### Post by Fitz_the_gap on 2008-12-17
Hello People, I'm trying to find gconftool-2 commands that will achive the following:

1. Remove Preferences and Administration from the system main menu.

2. Remove the 'Edit Menus' option when right clicking on the main menu.

Cheers 

Fitz

---

### Post by gettinoriginal on 2008-12-17
Well, you can remove preferences and admin in edit menu, just untick them. But I do not think you can edit out the edit menu option.  Is there some special reason that you would want to do this ??  :confused:

---

### Post by Fitz_the_gap on 2008-12-17
Thanks for the hasty reply, the reason I would like to do it this way is I have a list of other gconftool-2 commands that I will execute via a script. I need to deploy Ubuntu on 250 machines, the easiest way to lock down the desktop and deploy my changes are with a script. I've tried to use sabayon but it seems to crash when I try to lock down the desktop. The reason for the removel of the Edit Menu is so the users at the school can get on with work, so the less distrations the better.
Cheers 
Fitz

---

### Post by gettinoriginal on 2008-12-17
Then why not just remove the panel and make a dock with custom launcers for what you want them to have ??  Or (I don't know, not a guru LOL) is it possible to edit the properties in gksu nautilus, gnome panel.

---

### Post by Fitz_the_gap on 2008-12-17
Using the force, I feel that there is a way to achieve this with gconftool-2, but hay thanks any way!

---

