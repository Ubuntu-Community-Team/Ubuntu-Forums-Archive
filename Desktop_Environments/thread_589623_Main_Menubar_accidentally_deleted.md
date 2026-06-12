---
title: "Main Menubar accidentally deleted"
date: 2007-10-24
forum: Desktop Environments
---

### Post by Cariboo1938 on 2007-10-24
Fooling around, I accidentally deleted the "Main Menubar" with Applications Menu, Places Menu and System Menu, all gone....clock, volume control, notification applet, all gone. 
What can I do to get it back?
Please help, I went through all the relevant threads but couldn't find an answer.:confused:

---

### Post by HMartinho on 2007-10-24
Hi;

I've add a similar problem and someone helped me, so it's up to me now to help you.
do u have the bottom bar? if yes right click it and add new bar, set to be up bar, the right click again and select "add to bar/pannel" and select the features you want.
hope this helps you.

cheers.

---

### Post by Lardarse on 2007-10-24
Right click any panel (it won't ever let you delete the last one) and select "New Panel". then right click that new panel and select "Add to Panel...". Then add the following items:

Menu Bar
Notification Area
User Switcher
Clock
Deskbar
Volume Control
Quit...

That should add everything except the buttons to launch Firefox, Evolution, and Help, which can all be found in the menus, or you can use the "Application Launcher" button to add them.

If you accidentally delete the bottom panel instead, the items you need to add are:

Window List
Show Desktop
Deleted Items
Workspace Switcher

---

### Post by Cariboo1938 on 2007-10-24
Thank you both for the response ....
I have to go to work now ......and try later ....keep you posted.....

Edit:
That was easy....It worked exactly as described....Cool!
Thank you....:guitar:

---

### Post by simucal on 2008-01-24
Type in these 3 commands in a console:

gnome-session-remove gnome-panel
gconftool-2 --recursive-unset /apps/panel
gnome-panel &

Your gnome bars should be set back to the default now.

---

