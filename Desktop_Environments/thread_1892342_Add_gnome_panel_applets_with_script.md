---
title: "Add gnome panel applets with script"
date: 2011-12-07
forum: Desktop Environments
---

### Post by rpinsky on 2011-12-07
I have a script that creates a new user. (Using ubuntu 10.10) As part of that script, I'd like to add an applet to their gnome toplevel panel. The applet is a custom written applet and work correctly when added to the panel by right clicking the panel and selecting "Add to Panel", however, I don't want to have to log into their user account and manually have to click on their panel to add the applet. For every new user that I create, I'd like them to have that applet.
 
I have tried to use gconftool-2 to add key values under /apps/panel/applets/applet_0 but the applet doesn't appear (I created the same keys that are created when adding the icon using the right click "add to panel").
 
Does anyone know how to add an applet to a user's gnome panel using a shell command/script?
 
If that is not possible (or easily done), is there a way to change the default set of applets that are loaded onto a new user's toplevel panel when the user is created?
 
Thanks for the help,
Robert

---

