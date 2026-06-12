---
title: "How to make icons show on the desktop?"
date: 2005-03-05
forum: Desktop Environments
---

### Post by joplass on 2005-03-05
How can one make gnome show icons on the desktop?  Right now I don't even have a single one on there and it seems the usual right-click is not available either.
Thank you in advance,

---

### Post by doitashimashite on 2005-03-05
You mean, like

Applications /
Internet /
Mozilla Firefox /
right mouse click
Add this launcher to panel

Then push the icon from the panel to your desktop with left mouse button.

Alternative way to do the same thing is right mouse click on your desktop,
"Create Launcher"

---

### Post by bored2k on 2005-03-05
[QUOTE=joplass]How can one make gnome show icons on the desktop?  Right now I don't even have a single one on there and it seems the usual right-click is not available either.
Thank you in advance,[/QUOTE]
 > Q: How to show Desktop Icons (Computer, Home, Trash)?

   1. Read General Notes
   2. Applications -> System Tools -> Configuration Editor
   3. GConf editor -

      / -> apps -> nautilus -> desktop ->
      computer_icon_visible (Checked)
      home_icon_visible (Checked)
      trash_icon_visible (Checked)

[http://ubuntuguide.org/#showdesktopicons](http://ubuntuguide.org/#showdesktopicons)

---

### Post by landotter on 2005-03-05
Well if you're not getting a context menu from right clicking, perhaps you need to kill and respawn nautilus (the file manager which draws the desktop)

open a terminal and type "killall nautilus"

---

### Post by joplass on 2005-03-05
Damn!
You guys rock.  I am up and running.  This forum is making my migration to Ubuntu and from Kde really flawless.  =D>  =D>  =D> 
Thank you very much.

---

