---
title: "enable transparency in xfce"
date: 2010-08-26
forum: Desktop Environments
---

### Post by v1nsai on 2010-08-26
I've been looking around for a while now for the answer to a pretty simple question.  I'm normally a gnome user but I'm setting up an old computer with xubuntu for a friend, and I can't figure out how to get transparency to work for guake.  In gnome I just go to appearance > visual effects, don't see anything like that in xfce.

I downloaded compizconfig-settings-manager (which I assume downloaded the rest of compiz) and did "compiz --replace" but that didn't work.  What would I need to do to get basic opengl effects?

---

### Post by xdemo on 2010-08-26
Try enabling compositing in:
```
Settings > Xfce 4 Settings Manager > Window Manager Tweaks
```
go to the *compositor *tab, and enable  display compositing.

I think that should do the trick.

---

### Post by v1nsai on 2010-08-26
That did it, thanks a bunch!

---

