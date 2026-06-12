---
title: "Removing taskbar tooltip in GNOME"
date: 2007-12-07
forum: Desktop Effects &amp; Customization
---

### Post by Izek on 2007-12-07
How can I remove the tooltip (the yellow-looking one) from the bottom taskbar panel? On KDE, they tell me to go to customize via the right click or something, but that doesn't exist in GNOME (It's Properties instead.) There is no "Show Tooltips" checkbox when I go to the panel's properties.

CRTL+F1 like in the help for ubuntu doesn't work either by the way.

---

### Post by SpiritIsReality on 2007-12-08
howdy
any help here?
[http://www.google.ca/search?hl=en&q=ubuntu+remove+tooltips&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=ubuntu+remove+tooltips&btnG=Search&meta=)
trails

---

### Post by Izek on 2007-12-08
> **SpiritIsReality said:**
> howdy
any help here?
[http://www.google.ca/search?hl=en&q=ubuntu+remove+tooltips&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=ubuntu+remove+tooltips&btnG=Search&meta=)
trails

No, not much. I tried going to Apps > Panel > Global in the gconf editor, but it didn't work.

---

### Post by Ub1476 on 2007-12-08
> **Izek said:**
> No, not much. I tried going to Apps > Panel > Global in the gconf editor, but it didn't work.

Yes, a bug which nobody cares to fix. You can use Compiz-Fusion to hide it though. Go to General>Opacity>add "tooltips" then set it to be 100% invisible. 

Might be the name is something like: "name=tooltip", "name=tooltips", "tooltip", "tooltips".

 
This will hide all tooltips though:(

---

### Post by Izek on 2007-12-10
Only tooltips from Ubuntu, and if you have a low processor, you'll see them for a flash as compiz sets the opacity. Web page tooltips still show.

---

