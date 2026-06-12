---
title: "Deactivate redraw when resizing windows (graphic performance)"
date: 2012-05-02
forum: Desktop Environments
---

### Post by ghope on 2012-05-02
About a year ago I applied a config change to Nautilus (or was it Gnome?) but just lost it when I upgraded to Natty. This change deactivates the redraw that occurs while a window is being resized. Instead, the window goes temporarily blank and a simple grid is shown in place of the content. When the mouse button is released, the window is then redrawn, and this change makes a significant difference in graphic performance on my old system. I have run gconf-editor but cannot find the setting. If anyone can refresh me on how to do this, I'll be grateful.

Greg

---

### Post by stinkeye on 2012-05-02
For metacity...
```
gconf-editor /apps/metacity/general/reduced_resources
```

---

### Post by ghope on 2012-05-02
> **stinkeye said:**
> For metacity...
```
gconf-editor /apps/metacity/general/reduced_resources
```

That was the setting I had in mind. It was already checked, so the setting got carried over during the upgrade. Seems like a restart was needed, because the wireframing is working now. Thanks!

---

