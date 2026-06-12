---
title: "GNOME Main Menubar gtkrc"
date: 2008-03-29
forum: Desktop Effects &amp; Customization
---

### Post by dbbolton on 2008-03-29
I'm customizing a gtkrc file and I want to create a new style that applies ONLY to to gnome-panel menubar (Applications Places System).

Is that possible, and if so, what is the name of the class or widget that the style would be applied to?

---

### Post by dbbolton on 2008-03-30
After playing around, I think it is one of the following:

```

widget "*PanelWidget*"

class "*Panel*"

```

but I'm not sure.

---

