---
title: "New windows are garbled for a moment or two"
date: 2009-02-24
forum: Desktop Environments
---

### Post by TygerFish on 2009-02-24
I've noticed that in all of the KDE/Qt applications I use, new windows are temporarily filled with garbage for up to a second until the window contents begin to render.  The annoying thing is that this interim content is made up of recently-used screen elements.  For example, if a new dialog box pops up, it might temporarily be filled with random patterns, part of a "forward" button from a different open window, and an X button from a window I recently closed, in no particular arrangement.  It would be better if the windows would just be blank until the content started rendering.  Is there a way to get them to do this?

---

### Post by Monsieur Gonzalez on 2009-02-24
If with an NVIDIA card, then check you're using the latest drivers (nvidia-glx-180, I think).

---

### Post by TygerFish on 2009-03-03
Not using the latest drivers; there's a bug with the installation.  But I highly doubt this is related to that, since it's a problem I've seen in KDE for a long time.  I seem to recall there was something I did to fix it at one time, but I can't recall what that might have been.

---

### Post by benerivo on 2009-03-03
It's been a bug in kde for a long time. See these trackers...

[ubuntu]("https://bugs.launchpad.net/ubuntu/+bug/254468"), [kde]("http://bugs.kde.org/show_bug.cgi?id=170462")

Not everyone seems to get it, and it looks like there is a patch.

---

