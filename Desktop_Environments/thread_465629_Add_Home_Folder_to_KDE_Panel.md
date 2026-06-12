---
title: "Add Home Folder to KDE Panel"
date: 2007-06-05
forum: Desktop Environments
---

### Post by VoodooSteve on 2007-06-05
I am trying to add the home folder applet to my panel in KDE, but I am unable to find it. It is not in the "Add Applet to Panel..." menu. Anyone know how I could add it? I am using KDE 3.5.2 with Ubuntu 6.06.

---

### Post by Nythain on 2007-06-05
i believe what you would be looking for is the applet called system menu... not sure if its available by default, if not try installing this package
sudo apt-get install kicker-applets
then it should be available... and if thats not the one you are wanting you should look into quick file browser... a cool applet that will list files in a given location in a fun drop down menu (i use this one a lot)

---

### Post by VoodooSteve on 2007-06-05
Thanks, system menu is there and I added it. However, on many KDE desktops, I notice that there is a Home Folder icon specifically in the panel (See the KNOPPIX screenshot below).

Edit: I booted up to KNOPPIX and looked at the "Add Applet to Panel..." menu. A Home Folder applet is not there. It seems it's similar to a Home.desktop file, but how do I add one of these to the KDE panel?

---

### Post by Nythain on 2007-06-06
that would be the "Quick Launcher" applet... just change the icon size, and remove the default ones you dont want, like kate, and help etc

---

### Post by VoodooSteve on 2007-06-06
Okay, thanks.

---

