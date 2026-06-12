---
title: "Difference between &quot;gnome-session-fallback&quot; and &quot;gnome-shell&quot; ...?"
date: 2011-10-15
forum: Desktop Environments
---

### Post by scorp123 on 2011-10-15
I hate Unity. Seriously. I hate it. I've been using Linux since 1996 and there were always changes sooner or later, but never *this* drastic ... (and no, the change from KDE 3.x to KDE 4.x a few years back was not that drastic!)

Sooo ... I was reading on how to get "Gnome Classic" back and there seem to be three different methods ...?:

Method 1):
```
sudo apt-get install gnome-session-fallback
``` ... I imagine that afterwards there will be an option in the login manager, someting like "Gnome Classic" ...?

Method 2):
```
sudo apt-get install gnome-shell
``` ... and then select "Gnome Classic" in the login manager.

Method 3)
```
sudo apt-get install gnome-panel
``` ... not sure what exactly this does and what dependencies this pulls in??


So my question is: What's the difference between these? Are they really the same or do different packages get installed? And which one really does give the user a Gnome 2.x like experience?

Can anyone who's already installed Ubuntu 11.10 be so kind and respond please? Thank you in advance.

---

### Post by mcduck on 2011-10-15
I don't know about the gnome-panel one, but what comes to installing gnome-shell or gnome-session-fallback, the thing is simply that they depend on each other. Doesn't matter which one you install, you'll get both anyway. :)

Gnome-session-fallback is the one that gives you the interface similar to old Gnome 2, but it's part of (and thus depends on) gnome-shell.

---

### Post by scorp123 on 2011-10-15
> **mcduck said:**
> Doesn't matter which one you install, you'll get both anyway. :)

Gnome-session-fallback is the one that gives you the interface similar to old Gnome 2, but it's part of (and thus depends on) gnome-shell.

:lolflag: ... guess that explains it then :D

Thanks!

---

