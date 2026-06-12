---
title: "Can't edit the menus anymore"
date: 2007-09-02
forum: Desktop Environments
---

### Post by Mark Phelps on 2007-09-02
My apologies for multiple posts -- but I don't know what happened ...

Anyway, once again, a basic function in Ubuntu 7.04 has stopped working!  This time, I can't edit the menus anymore.  I right-click the top menu area, select edit menus, wait while the rotating cursor spins -- and then, nothing!!

This worked the last time I used it two days ago, and I haven't installed or changed anything since then.

Anything I can do?

---

### Post by matthew.lns1 on 2007-09-02
Try opening a gnome-terminal and typing 'alacarte' and pressing enter.

---

### Post by Mark Phelps on 2007-09-02
OK -- this is what I got:
alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 22, in <module>
    from Alacarte.MainWindow import MainWindow
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 19, in <module>
    import gtk, gtk.glade, gmenu, gobject, gnomevfs, gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

What now?

---

### Post by Mark Phelps on 2007-09-02
OK -- tracked it down to a package upgrade -- OSS-linux from v1004 to v1006, at least, I think that's the culprit because when I purged the newer package and reinstalled the older one, and then tried to edit the menus, it works again.

Will have to post this to the 4Front forums -- and see what they say.

---

