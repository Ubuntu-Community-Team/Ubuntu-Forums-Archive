---
title: "Gnome Panel set to Auto Hide with no Apps/Launchers"
date: 2010-02-17
forum: Desktop Environments
---

### Post by De4dSpace on 2010-02-17
I created a new panel and set it to orientation left, unchecked expand, checked autohide and didn't add any apps or launchers.  When I Closed Panel Properties, the panel hid itself but would not respond to mouse hover.  I could see a bit of the panel two pixels thick, but could not right click it.  
I fixed this by creating a second new panel, setting it to orientation left, and now I could show / access the hidden panel.

It was getting annoying, fullscreen programs would not "hug" the left side of the screen.

I would like to know where ubuntu stores panel settings as a txt or config file, to manually set autohide to false.

---

### Post by kouberl on 2011-02-20
open gconf-editor in terminal (or alt-f2)
settings are in /apps/panel/toplevels/<your panel>

---

