---
title: "how to remove only gnome panel (using cairo)"
date: 2010-12-17
forum: Desktop Environments
---

### Post by slixz85 on 2010-12-17
hi i just started using cairo and its alright for the time being gonna keep using it. i switch stuff like this off and on. but i am just trying to remove the gnome panel. everything added on is removed from it but it is still there. it is definitely taking away from the cairo look i am tryin to do. anyone know how to remove this let me know the delete this panel button is grayed out.

thanks to any post

---

### Post by hhh on 2010-12-17
Open the Run dialog (Alt+F2), run gconf-editor, navigate to desktop >> gnome >> session >> required_components, double click "panel" make the field blank (remove "gnome-panel"), log out and back in.

---

### Post by Kognit on 2010-12-17
When you remove gnome panel i advise you to install "grun" or something similar, because if you remove gnome-panel the "Run Application" dialog won't work. After that go to keyboard shortcuts and define ALT+2 for grun.

---

### Post by slixz85 on 2010-12-17
> **hhh said:**
> Open the Run dialog (Alt+F2), run gconf-editor, navigate to desktop >> gnome >> session >> required_components, double click "panel" make the field blank (remove "gnome-panel"), log out and back in.


in case of complications is it easy to put gnome back on by putting gnome-panel back into the text if i have to or will this remove it alltogether and gotta reinstall it or kde or something?

still learning....;)

---

### Post by slixz85 on 2010-12-17
oh and by doing this besides the run dialog is there anything else that could ruin me lol and thanks btw for quick response

---

### Post by Kognit on 2010-12-17
There should not be any complications but you never know:)

Yes, if anything happens just write gnome-panel in gconf-editor where you erase it before. 

Beside that nothing important as i know should be mentioned.

Enjoy

---

### Post by hhh on 2010-12-18
Kognit's right, just re-enter "gnome-panel" and log back out and in.

Good catch on the Run dialog by him too, I had forgotten about that (I use Xfce these days).

---

