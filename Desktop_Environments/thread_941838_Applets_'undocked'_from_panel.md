---
title: "Applets 'undocked' from panel"
date: 2008-10-08
forum: Desktop Environments
---

### Post by crebs on 2008-10-08
I've accidentally 'undocked' some applets from the top right corner of my desktop panel (don't know how - think it was a slip of the mouse!) I have attached a screen shot.

The applets are now floating around, orphaned and I can't work out how to get them back in the panel where they were before (sat to the left of the date and time).

Would really appreciate someone telling me how to get them back in to the panel!

The applets are: pidgin and the bluetooth applet.

---

### Post by ajgreeny on 2008-10-08
Never seen that before!  Have you tried just dragging them back in?  If that doesn't work try uninstalling the applet by right clicking and "Remove from panel" then add them back in again.

---

### Post by crebs on 2008-10-10
When I right click inside those little boxes, there is no context menu. I have also tried 'dragging and dropping' the icons/boxes and they cannot go any further than the panel boundary.

---

### Post by ajgreeny on 2008-10-10
That is very odd.  What, if anything shows up in nautilus under your home folder Desktop folder.  You may be able to delete them from there.  If not it may be better to try in the hidden folder .gconf in your home folder.  Navigate to the ~/.gonf/apps/panel/applets and delete from there.  You can find out what each applet refers to by opening the xml file in each numbered applet folder and looking for clues in that file output.  You may also find out what each is by using the command ```
gconf-editor
``` but I find it more difficult to delete applets that way.  Finally, if you don't mind setting up your gnome prefences again, you could just try renaming the .gconf folder and starting gnome again by logging out and in again.

---

### Post by crebs on 2008-10-10
Thank you for your help ajgreeny. I have found the solution to the problem by experimenting (isn't that always the best way!) 

I fixed it by adding a new notification area as it turns out I had inadvertently deleted it. For reference, I did this by: 

[LIST=1]
[*]Right clicking on the top panel
[*]Choosing 'add to panel' 
[*]Scrolling down to 'notification area' in the list 
[*]Clicking the 'add' button
[*]Restarted Gnome/X by pressing CTRL + ALT + Backspace
[/LIST]

When I logged back in, the orphaned applets 're-docked' back in their original positions!

Hooray!

---

