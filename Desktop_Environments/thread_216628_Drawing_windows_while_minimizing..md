---
title: "Drawing windows while minimizing."
date: 2006-07-15
forum: Desktop Environments
---

### Post by whiterussian on 2006-07-15
Call me picky,

Is there any way to disable drawing of windows when you minimize them? I mean that little chain of boxes that is drawn between the active window and its task bar item.

I assume tis in gconf-editor somewhere, but thus far no luck finding it.

They just look out of place with my translucency settings at the moment.

Merci!

---

### Post by aysiu on 2006-07-16
In *gconf-editor*, Apps > Metacity > General > Reduced Resources

---

### Post by Anduu on 2006-07-16
I would use gconf-editor and go to /desktop/gnome/interface/enable_animations and uncheck it.

Using reduced resources also disables other things like showing window contents while dragging.

---

