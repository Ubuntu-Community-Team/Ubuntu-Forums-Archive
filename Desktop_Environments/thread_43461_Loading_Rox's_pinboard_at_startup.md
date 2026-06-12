---
title: "Loading Rox's pinboard at startup"
date: 2005-06-22
forum: Desktop Environments
---

### Post by AlexandreP on 2005-06-22
Hi all,

(I didn't really know if this message should have been better posted in "Other applications support", but since XFce4 is a wm manager...)

I'm runnning XFce 4.2.1, installed using Synaptic.  I would like to have the Rox-Filer's pinboard automatically launched when I start XFce.

I did some search.  The solution described in lot of tutorials and forums' topics is to delete references to Xfdesktop and add the following command in xinitrc file:
```
rox -p xfce4&
```
This file is supposed to be located in ~/.config/xfce4/ or /etc/xfce4/ or maybe in /usr/local/xfce4/.

The problem is, I don't find this famous xinitrc file!  Worse: I don't have the said above directories!  I've used the search tool for an xinitrc file, and found one in /etc/xdg/xfce4/.  Removing references to xfdesktop in it and adding the said command did not work, the pinboard is not lauched when I start XFce :?

I hope there is some XFce4 users that could help me with this problem :) 

@+
Alexandre P.

---

