---
title: "Maximise"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-15
Always open nopepad (er... gedit) maximised?

---

### Post by Klin'Targ on 2005-06-15
I think it saves the size of the window when you close it, so maximizing it then closing it should make it maximized when you open it again.

---

### Post by Dave_is_sexy on 2005-06-15
Yeah you'd think... :) nope

---

### Post by professor_chaos on 2005-06-16
weird....Klin'Targ's stategy works for me.

---

### Post by Klin'Targ on 2005-06-16
Perhaps one of gedit's preference files is not writable to you?

Try removing one or all of these files (if you have them):
~/.gnome2/gedit-2
~/.gconf/apps/gedit-2
~/.gconf/apps/gnome-settings/gedit
~/.gnome/accels/gedit
~/.gnome/gedit

I took this info from a very old version of gedit, so you may have others as well... you can use the find command to find any others you might have in your home directory.
```
find ~ -iname "*gedit*"
``` 
should do the trick

---

