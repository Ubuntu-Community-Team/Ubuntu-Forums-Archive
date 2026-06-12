---
title: "Gnome2-like experience in Gnome Shell"
date: 2011-08-23
forum: Desktop Environments
---

### Post by sahayes on 2011-08-23
Hey everyone,

I was googling this morning, and found out some ways to get GNOME Shell to behave more like GNOME 2.

**Show Desktop Icons:** Install dconf-editor, then open it up.  Go to org>gnome>desktop>background, and there is a checkbox called Show-Desktop-Icons.  Click it, then log out and back in to apply changes.

**Minimize/Maximize Buttons**: Open up gconf-editor (not dconf) and go to desktop>gnome>shell>windows.  Change the button layout to :minimize,maximize,close and close gconf-editor.  Logout and back in to apply.

**Add Gnome 2 Features:** I found a pack that installs extensions that add a panel, moves the clock to the right, and adds an Applications Menu in place of the Activities button (you can still access the Activities menu by moving the mouse to the upper left corner) [http://www.webupd8.org/2011/05/new-gnome-shell-extensions-that-provide.html](http://www.webupd8.org/2011/05/new-gnome-shell-extensions-that-provide.html)

**Bottom Panel**: [http://www.webupd8.org/2011/06/bottom-panel-gnome2-like-panel-gnome.html](http://www.webupd8.org/2011/06/bottom-panel-gnome2-like-panel-gnome.html)

I didn't see this info anywhere else in the forums.  Sorry if it's a repeat.

---

### Post by cbowman57 on 2011-08-23
Gnome-tweak-tool is a lot easier to use than dconf-editor for the first two items.

But, the information is scattered everywhere, it hasn't been consolidated yet.

Apparently you're having a good time exploring gnome-shell. :)

---

