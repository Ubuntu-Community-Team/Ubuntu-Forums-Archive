---
title: "Disappeared window borders after deleting e16"
date: 2010-09-28
forum: Desktop Environments
---

### Post by walkingbeard on 2010-09-28
Hi,

I've just had enough of Enlightenment e16, so I uninstalled it.  Now my window borders have disappeared and I can only input to one window - the first one I opened.  If I want to input to another, I have to close the first one.

I thought maybe gdm wasn't running (I'm using GNOME), but this is the output of ps -A | grep dm:

```

gdm-binary
gdm-simple-slav
gdm-session-wor

```Any ideas?  Thanks.

---

### Post by walkingbeard on 2010-09-29
The solution is to run metacity from the terminal.  I'm going to post separately about how to make that happen automatically.

---

