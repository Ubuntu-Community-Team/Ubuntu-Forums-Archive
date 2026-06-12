---
title: "Konqueror vs. Metacity"
date: 2007-07-28
forum: Desktop Environments
---

### Post by TeeAhr1 on 2007-07-28
One of my favorite features of Metacity is its ability to remember the view settings I chose for a particular folder.  For instance, in my "incoming media" folder, the icons are very large and preview the file, and it's sorted by date.  My "tagged music" folder displays as a tree and is sorted alphabetically.

My question is: can Konqueror do this?  Any tips always greatly appreciated.

best-
pete

---

### Post by cilynx on 2007-07-30
First off, I'm going to assume that when you say Metacity, you mean Nautilus.  Nautilus is the Gnome file manager just as Konqueror is the KDE file manager.  Metacity is the Gnome window manager just as kwin is the KDE window manager.

To get to the point of your question:

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

### Post by TeeAhr1 on 2007-07-31
"First off, I'm going to assume that when you say Metacity, you mean Nautilus."

LOL Durrr, yep.  My mistake.

"Konqueror can save views locally, yes. I don't think there is any nice, graphical way to enable this feature, however..."

Sweet!  Thank you so much!

-p.

---

### Post by TeeAhr1 on 2007-08-07
Hit a snag here.  Every time I log out, the changes I make to konquerorrc are erased...

-p.

---

