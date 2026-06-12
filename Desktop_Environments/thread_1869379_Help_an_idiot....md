---
title: "Help an idiot..."
date: 2011-10-25
forum: Desktop Environments
---

### Post by ZootHornRollo on 2011-10-25
Hi,

I switched to ubuntu 11.10 and so far other than a problem with freezing every now and again it seems fine.  

I switched to Gnome Shell to give it a whirl and have to say i like it.  I installed gnome tweak and changed the setting for use File Manger for desktop just to experiment and now i can't get out of it!  Every time i boot it goes straight to the file manager desktop stylee...

Any idea how i switch back to the regular gnome shell?

---

### Post by Frogs Hair on 2011-10-25
Is this the setting you are writing about ?

---

### Post by ZootHornRollo on 2011-10-26
Yes, thats it!

Alt+F2 doesn't open a run dialogue.

---

### Post by crdlb on 2011-10-26
What session are you choosing at the login screen? If 'GNOME', can you log into 'GNOME Classic' successfully? In that session, open a terminal and run ```
gnome-shell --replace || metacity
``` If the Shell fails to start here, you should get a useful error.

---

### Post by Frogs Hair on 2011-10-26
> **ZootHornRollo said:**
> Yes, thats it!

Alt+F2 doesn't open a run dialogue.

That setting allows the file manager handle items such as , documents or photos dragged onto the desktop . I don't how that is effecting the shells appearance when you login . That Feature can be toggled on or or off from advanced settings .

---

### Post by crdlb on 2011-10-26
If GNOME Shell is otherwise working, there is a known bug that results in Alt+F2 being unset by default. You can fix it in System Settings > Keyboard > Shortcuts > System.

---

### Post by ZootHornRollo on 2011-10-27
thanks for your help.

When ubuntu booted up it would go to a fairly bare desktop with only the menus from nautilus - file, edit, view, go and bookmarks - at the top of the screen.  No other menus or icons were visible.

booting into gnome classic allowed me to access the applications menu and load up gnome-tweak.  after reseting the option to manage the desktop with the file manager i couldn't get a desktop to boot on any gnome/unity session so ended up reinstalling a fresh copy of 11.10.

So far so good...

certainly won't be touching that setting again!

cheers.

---

