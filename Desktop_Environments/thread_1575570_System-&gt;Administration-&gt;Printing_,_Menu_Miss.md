---
title: "System-&gt;Administration-&gt;Printing , Menu Missing"
date: 2010-09-15
forum: Desktop Environments
---

### Post by Delgo Thex on 2010-09-15
Well like the title Implies, In my Administration menu in Gnome I don't have a "Printing" option. So I can't search for/install printers right now.
 
I'm running 10.04 Server. I installed the gnome-desktop-environment package to get a GUI up and running for manipulating the filesystem, But not all the menu's I was expecting appeared. Is this because I used the gnome-desktop-environment instead of the ubuntu-desktop-environment package? 
 
Because I have two PC's setup next to each other. One using the ubuntu-desktop-environment, and one using the gnome-desktop-environment package and the two desktops are clearly different. 
 
All I want to know is how to add the Printers menu to my PC running the gnome-desktop-environment package. I already looked at gconf-editor and the printing menu isn't hidden or anything, it's just not there. And me being a new user to Linux, I don't know how else to get to those printer abilities without the GUI, because I wouldn't mind using the Command Line.

---

### Post by Reechani on 2010-10-13
You have to install the package system-config-printer-gnome. This doesn't automatically install all the drivers so you might have to look for the correct package for that though.

---

