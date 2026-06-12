---
title: "How to automatically adjust xorg.conf based on number of displays present?"
date: 2009-04-30
forum: General Help
---

### Post by lurikeen on 2009-04-30
Is there a way to do this? It's for a laptop that is sometimes plugged into an external display, which is the only active monitor in that case.

---

### Post by veloce on 2009-05-07
> **lurikeen said:**
> Is there a way to do this? It's for a laptop that is sometimes plugged into an external display, which is the only active monitor in that case.

I've seen scripts that use xrandr to do what you want. They used the information functions to find out what was connected, then ran appropriate commands to set them up how you want them.  This was several versions of Ubuntu ago - not sure of current status.

How useful these are depends on which version of Ubuntu you are using.  Jaunty seems to recognise the changes in the screens but makes it's own call as to how to use them!

---

