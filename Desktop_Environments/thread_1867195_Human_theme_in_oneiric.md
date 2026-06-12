---
title: "Human theme in oneiric"
date: 2011-10-22
forum: Desktop Environments
---

### Post by korb on 2011-10-22
I have installed the human theme in oneiric (apt-get install human-theme) and have logged in to the GNOME classic desktop, but I can't seem to get the new theme to show up in the list of themes when I try to customize my desktop. How can I opt to use this theme?

Thanks,
Bill

---

### Post by merlinus on 2011-10-22
Don't know if this will help, but 11.10 only uses gtk3+ themes.  I also installed the human theme, but it will only show up under Window and Icon themes, not desktop.

---

### Post by ajgreeny on 2011-10-22
I think you need gnome-tweak-tool to do it.  Install that and then try again using it to change the theme.

Here's a lot of info I found by bob-linux-user in another post at [http://ubuntuforums.org/showthread.php?t=1865912](http://ubuntuforums.org/showthread.php?t=1865912)

> The Gnome that is available on Ubuntu 11.10 is I find a good alternative to Unity and as far as I can see it looks and feels like classic gnome. The instructions below let you use a panel, get rid of the diabolical overlay scrollbars and put the window controls back at top right.This is what I did:

Install ubuntu 11.10 in normal way
In a terminal type
sudo apt-get install synaptic
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0
sudo apt-get install gnome-session-fallback
sudo apt-get install gconf-editor
sudo apt-get install gnome-tweak-tool
log out and log back in gnome classic
In a terminal type
gksudo gconf-editor
Browse to apps/metacity/general. Double click on button_layout and gconf-editor and set value to
:minimize,maximize,close
Alt right click on panel at top.
-Set orientation to bottom and size to 36
Alt right click on time and move to extreme right
Alt right click on panel and add
-Main Menu
-Window List
Alt right click on "Applications Places" menu and remove
Alt right click on the "speech bubble" at bottom right and remove
Remove the slim top panel by alt right clicking and deleting
Alt right click on panel and add
-Show desktop icon
On a general area of desktop right click and change the background to what you want ( I chose Jardin Polar)
in a terminal type
sudo apt-get install ubuntustudio-theme
sudo apt-get install ubuntustudio-icon-theme
sudo apt-get install human-theme
sudo gnome-tweak-tool
Set Theme:Icon theme to Ubuntu Studio
Set GTK+ theme to Raleigh
Set window theme to human
I hope that helps.

PS:  Great thanks to bob-linux-user as well for this great tutorial.

---

