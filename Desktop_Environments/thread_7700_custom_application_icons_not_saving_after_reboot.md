---
title: "custom application icons not saving after reboot"
date: 2004-12-10
forum: Desktop Environments
---

### Post by taygan on 2004-12-10
I've install gxine, and added its icon to the Applications menu, but after each restart the icon is gone.  What's going on?  I did remove my .gnome configuration files to fix another problem.. I also installed (and uninstalled) some other themes.. Could these actions be affecting the icons?

---

### Post by randy on 2004-12-10
You'll need to change the desktop files for each application under /usr/share/applications for the changes to be permiminent.

---

### Post by taygan on 2004-12-10
hmm.. there is no Desktop Configuration File for /usr/share/applications/gxine

I've googled and looked at gnome.org, but I haven't found how to make a Desktop Configuration File, and I haven't found where else the darn thing could be hiding..

Any ideas?

---

### Post by randy on 2004-12-10
You'll want to create one then.  You'll need to name it gxine.desktop and you can look at the other .desktop files for examples.  They are pretty simple to setup.

---

### Post by taygan on 2004-12-11
Thanks! after creating /usr/share/applications/gxine.desktop that reads;

[Desktop Entry]
Encoding=UTF-8
Name=gxine
Comment=
Exec=gxine
Icon=gxine-logo.png
Terminal=false
Type=Application

the launcher disappeared from the Applications menu, after making another launcher it stayed!

---

### Post by dany084691 on 2007-05-15
> **taygan said:**
> I've install gxine, and added its icon to the Applications menu, but after each restart the icon is gone.  What's going on?  I did remove my .gnome configuration files to fix another problem.. I also installed (and uninstalled) some other themes.. Could these actions be affecting the icons?


[American Idol Skin care plants Debt Consolidation demonstrate](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/latin-porn.html)

---

