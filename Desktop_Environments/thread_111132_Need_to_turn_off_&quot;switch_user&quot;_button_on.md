---
title: "Need to turn off &quot;switch user&quot; button on screen lock"
date: 2006-01-01
forum: Desktop Environments
---

### Post by GreyFox503 on 2006-01-01
Does anyone know how to disable the "switch user" button that appears on the screen locked dialogue?  I'd really rather not have it there.  This "feature" was added to Breezy, but was not in Hoary.

And on a side note, what's up with the guy with the goatee?  Any way to change him?  The "about me" page's picture has no effect.

EDIT:  Worked around it by installing and using the gnome-screensaver package instead of xscreensaver.  It fixes both problems.

---

### Post by chocolatemintmocha on 2007-02-08
Go to synaptic and download pessulus. After that click on system-administration-lockdown editor, or type pessulus into the command prompt and press return.

---

### Post by cube3x3 on 2007-10-04
To disable "switch user" in terminal:

$ gconf-editor

When gconf-editor opens, go to 'desktop -> gnome -> lockdown'
In that select 'disable_user_switching' .

Let me know if this works or not.

---

### Post by 6205 on 2008-06-13
> **cube3x3 said:**
> To disable "switch user" in terminal:

$ gconf-editor

When gconf-editor opens, go to 'desktop -> gnome -> lockdown'
In that select 'disable_user_switching' .

Let me know if this works or not.


THANKS !!!! Working fine in Ubuntu Hardy :guitar:

---

