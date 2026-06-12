---
title: "Custom Panel Launcher Via Script"
date: 2009-07-14
forum: Desktop Environments
---

### Post by Trapper on 2009-07-14
U-904-64
Gnome


Is there a way I can add a custom application launcher to the panel via a script or from the command line in a term? I have a .desktop for the app that I can copy into ~/.gnome2/panel2.d/default/launchers but that doesn't load it into the panel.

Apparently there was once a process called gnome-panel-add-launcher that could be utilized to create a launcher via the command line or a script. That doesn't seem to be available anymore.

This launcher needs to be created without any interaction from the user other than running the script itself, so dragging a .destop file from ~/.gnome2/panel2.d/default/launchers to the panel, etc. is not an option.

---

### Post by Trapper on 2009-07-17
Bump

---

### Post by fredyboy10 on 2010-05-04
You can use gconftool-2, but the details are still fuzzy to me. Let me know what you find out.

---

### Post by kerry_s on 2010-05-04
why not just put it on the desktop?
that way it works no matter if not running a panel or even gnome for that matter.

---

