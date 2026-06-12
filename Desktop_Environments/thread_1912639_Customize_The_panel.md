---
title: "Customize The panel"
date: 2012-01-21
forum: Desktop Environments
---

### Post by ilmkidunya on 2012-01-21
Ubuntu includes a top panel and a bottom panel by default. If you prefer to keep only one panel at the bottom just like the Windows Taskbar, then these are the steps to follow:

Delete the bottom panel: right-click over it and click "Delete This Panel".
Move the top panel to bottom: right-click over it, select "Properties" and change Orientation from "Top" to "Bottom".
Add running program buttons: right-click the panel, select "Add to Panel", scroll down and select "Window List", click "Add".
Replace the Menu Bar ("Applications-Places-System") with the "Main Menu" to save space in the panel:
Right-click the "Menu Bar" and select "Remove From Panel".
Right-click the panel, select "Add to Panel" and choose "Main Menu", click "Add".
Right-click the items (Firefox, etc) and untick "Lock to Panel".
Right-click the added "Main Menu", select "Move" to relocate it to the far left.
These are basic changes. The panels are much more flexible than the Windows Taskbar in that many items in the panels can be easily added, removed or configured.

   The Main Menu shows the "Lock Screen", "Log Out" and "Shut Down" items if you remove the "Indicator Applet Session" item (which shows your username and the shutdown button to the right of the panel). These three items are hidden from the Main Menu when the Indicator Applet Session item is on the panel.

   If you need to restore the panels to the original state, enter the following commands into the Terminal and re-start the system:

sudo gconftool-2 --shutdown   [IMG]http://www.techsupportalert.com/files/images/Ubuntu_10_04_full.jpg[/IMG]
sudo rm -rf .gconf/apps/panel
sudo pkill gnome-panel
   At any point if your customized desktop settings caused a problem and you wish to reset all back to their defaults, then enter this command sudo rm -rf .gnome .gnome2 .gconf .gconfd .metacity in the Terminal, log out and log back in to the system.

---

