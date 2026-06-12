---
title: "&quot;Open Terminal&quot; in right-click menu"
date: 2009-06-04
forum: General Help
---

### Post by theturbanator on 2009-06-04
Hi,

I would like to have an "Open Terminal" option in my right-click menu.  I installed the "nautilus-open-terminal" package, which gave me an "Open **In** Terminal" option, which opens, when I right-click on the Desktop, a terminal with the path set to the Desktop, so I have to cd into my home directory (i.e. the location specified by '~' in command-line scripting).  I use the terminal a lot, and, after using redhat at work, I see how much easier it is to right click to open a terminal rather than double-click on the terminal icon.  So is there a way to just get an "Open Terminal" option, which would open a terminal with the path set to ~, instead of "Open in Terminal"?  And if there is such an option for Ubuntu, then how can I get rid of the "Open in Terminal" option?

Thanks a lot!

---

### Post by Tibuda on 2009-06-04
Open the gnome configuration editor (Alt+F2, gconf-editor). Browse to /apps/nautilus-open-terminal and check the "desktop_opens_home_dir", and every time you use "Open in terminal" in the Desktop, a terminal will open in yout home dir.

---

### Post by michy99 on 2009-06-04
What I did is add a terminal launcher to my top panel. A single left-click on it opens a terminal in the home directory. To add it, click on Applications->Accessories. Right click on Terminal and choose 'Add this launcher to panel.' Very handy and always available.

---

### Post by theturbanator on 2009-06-04
Thank you to both of you! I ended up doing both -- though, for some reason, I feel that the right-click menu is easier and faster to access.

---

