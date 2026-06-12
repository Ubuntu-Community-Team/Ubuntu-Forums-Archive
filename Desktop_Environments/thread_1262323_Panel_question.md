---
title: "Panel question"
date: 2009-09-09
forum: Desktop Environments
---

### Post by WetWired on 2009-09-09
I have a custom image set on my gnome panel. It has some transparency, but when I try to add, for instance, the clock, to the panel, the clocks background doesn't follow the panel background. So the background of the clock is not transparent. Is there a way I can fix this? I'd like anything I add to the panel to follow the panels background, not the theme background.

---

### Post by earthpigg on 2009-09-09
hi,

if i remember correctly from when i used to use gnome...

logging out and back in will fix this.

---

### Post by mcduck on 2009-09-10
Most likely the problem is that the GTK theme you are using is defining background for panel applets.

To solve that you'll have to edit the GTK theme and remove all panel themeing from it. Quite often themes have a separate panel.rc (or similar) file, in that case simply removing or renaming that file does the trick. Otherwise you'll just have to read through the main gtkrc file.

Once panel themeing is removed from the GTK theme changes made directly in Gnome-Panel's options will affect all applets running in the panel correctly.

---

