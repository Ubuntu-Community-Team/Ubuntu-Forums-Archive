---
title: "bottom of window &quot;sticks&quot; to panel when dragging it downwards"
date: 2007-10-24
forum: Desktop Environments
---

### Post by shimrah on 2007-10-24
Hi,

I just upgraded to Gutsy, and it's looking good. Just one thing I'm noticing that's driving me a bit crazy.

If I drag a window down so that the bottom of the window touches the panel at the bottom of the screen, the window doesn't move if I continue to drag it downwards. Then, at some point, the window jumps to the point where the bottom of the frame is past the bottom of the screen (and the panel), and I can continue to drag it downwards.

It's kind of hard to describe. I can try harder if nobody understands what I'm trying to say. 

:)

Thanks,
Shimrah

---

### Post by mannih2001 on 2007-10-25
To me it seems pretty clear what you are referring to.

Have you enabled desktop effects?

If yes, you need to install compizconfig-settings-manager. You should then be able to choose System -> Preferences -> Advanced Desktop Effects Settings. 

Search for the "Move Window" applet and turn off "Lazy Positioning" . If that doesn't help then please take a look at the "Snapping Windows" applet.

---

### Post by shimrah on 2007-10-25
You definitely pointed me in the right direction.

It was the "Snapping Windows" applet; I unchecked "Edge Resistance" and the behaviour ceased. I guess that was by design.

Many thanks!

---

### Post by mannih2001 on 2007-10-25
> **shimrah said:**
>  I guess that was by design.

Some might even call it a feature.

---

