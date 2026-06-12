---
title: "how to install GTK+ and glib?"
date: 2009-03-04
forum: General Help
---

### Post by mahela007 on 2009-03-04
I want to install wxPython in order to learn about GUI programming in python. However the Wx python website [http://www.wxpython.org/download.php](http://www.wxpython.org/download.php)
says that I need two packages called GTK+ and glib.The website also says that I probably have them installed. How do I check if they are installed and if they are not how do I install them?

---

### Post by lykwydchykyn on 2009-03-04
you definitely have them.  You can also get wxpython from the repitories and have all the dependencies handled automatically.  Just crack open Synaptic and install python-wxgtk2.8

---

### Post by mahela007 on 2009-03-04
I use kubuntu. Aren't GTK and glib associated with gnome?

---

### Post by lykwydchykyn on 2009-03-04
Hrm... you might have mentioned that ;-)

You still most likely have them installed, because it's almost impossible not to have some kind of gtk app even in Kubuntu; if not, installing the wxgtk from the repositories will pull in whatever you lack.

I think the packages to install for glib and gtk would be libglib2.0 and libgtk2, but I can't check on that at the moment 'cause I'm doing a massive upgrade so apt is locked (upgrading to KDE 4.2.1!!!!)

---

