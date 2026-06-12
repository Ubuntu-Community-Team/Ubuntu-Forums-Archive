---
title: "Remove shadows for panels only"
date: 2008-02-10
forum: Desktop Effects &amp; Customization
---

### Post by timzak on 2008-02-10
Is there a way in compiz-fusion to disable the shadows for the panels, but leave the shadows for the windows?  Under CCSM in Window Decoration, there's a place to type inclusions/exclusions for "shadow windows" but I have no idea what to put here to accomplish what I want.

The reason I want to remove the shadows for the panels only is I want transparent panels, but the shadow kind of makes it pointless to make the panel transparent.  It's like being invisible but still casting a shadow.  You'll still be spotted.  ;)

---

### Post by cwgannon on 2008-02-10
Short answer:

Run ccsm.  Go to Window Decorations.  For both decoration and shadow windows, replace **any** with **!name=gnome-panel**.  (If you already have something other than **any** in there, just append **!name=gnome-panel**, separating it from the last entry with **|**.)

For a better explanation that will help you in your future endeavours:
[http://wiki.compiz-fusion.org/WindowMatching]("http://wiki.compiz-fusion.org/WindowMatching")

---

### Post by timzak on 2008-02-10
Thank you very much.  That was exactly what I was looking for!

---

