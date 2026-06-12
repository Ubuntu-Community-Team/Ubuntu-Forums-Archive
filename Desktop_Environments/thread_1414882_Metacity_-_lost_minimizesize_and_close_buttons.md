---
title: "Metacity - lost minimize/size and close buttons"
date: 2010-02-24
forum: Desktop Environments
---

### Post by madtom1999 on 2010-02-24
After a recent update the minimize/size and close buttons (-0X) in the top bar of every window have been replaced with a radiobutton.

I've tried:
metacity --replace &

but this gives:
Window manager warning: "(null)" found in configuration database is not a valid value for mouse button modifier
Window manager warning: Could not parse font description "(null)" from GConf key /apps/metacity/general/titlebar_font
Window manager warning: 0 stored in GConf key /desktop/gnome/peripherals/mouse/cursor_size is out of range 1 to 128


and does not fix the problem

---

### Post by ajgreeny on 2010-02-24
In nautilus go to **~/.gconf/apps/metacity** and rename it to **~/.gconf/apps/metacitybak** then logout and back in again.  Metacity should now have reset to the default and given you back your buttons.

---

### Post by madtom1999 on 2010-02-24
That just seems to remove the whole title bar!

---

### Post by madtom1999 on 2010-02-26
I tried logging in as a different user - that couldnt even get the panel up and running.
Switched to XFCE - that seems to be OK.

---

