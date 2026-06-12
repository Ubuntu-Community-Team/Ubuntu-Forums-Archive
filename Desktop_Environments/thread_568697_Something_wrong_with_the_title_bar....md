---
title: "Something wrong with the title bar..."
date: 2007-10-06
forum: Desktop Environments
---

### Post by glutama on 2007-10-06
The maximize/minimize/close buttons and the little icon are misplaced in the title bar.
Also, I can't see anything in the bottom panel where all my open applications should be
How can I fix this?

---

### Post by nikkiddl on 2007-10-06
First back up /etc/X11/xorg.conf

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_back up

(to revert back to original xorg.conf - sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf)

In terminal, run the following command:

sudo gedit /etc/X11/xorg.conf

Then scroll down to the "Screen" section, and insert the following line:

Option "AddARGBGLXVisuals"

Save, close, and restart your X session. Should do the trick.

if that doesnt work try adding - Option "AddARGBGLXVisuals" "true" to xorg.conf

to re-start your x session press ctrl - alt and backspace together.

cheers


Or see this link
[http://ubuntuforums.org/showthread.php?p=3474053](http://ubuntuforums.org/showthread.php?p=3474053)

---

