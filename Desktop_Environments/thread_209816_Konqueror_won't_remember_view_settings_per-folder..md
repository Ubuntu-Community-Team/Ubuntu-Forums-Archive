---
title: "Konqueror won't remember view settings per-folder."
date: 2006-07-05
forum: Desktop Environments
---

### Post by eXCeSS on 2006-07-05
Is there a way to have konqueror remeber my view settings, for specific folders?
I want my /home in tree view and my music folder in column view.
Is this possible? If not are there other things I can use to replace Konqueror that would let me do this?

---

### Post by cilynx on 2007-07-30
Konqueror can save views locally, yes.  I don't think there is any nice, graphical way to enable this feature, however, fire up your favorite text editor and open:
```
~/.kde/share/config/konquerorrc
```
You're going to add a new section to the bottom of the file with one rule:
```
[MainView Settings]
SaveViewPropretiesLocally=true

```
Close any remaining Konqueror windows and fire it up again.  From here on out, all of your view settings will only stick to the directory you assign them in.

---

