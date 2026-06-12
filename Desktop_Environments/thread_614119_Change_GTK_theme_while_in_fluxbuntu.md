---
title: "Change GTK theme while in fluxbuntu"
date: 2007-11-15
forum: Desktop Environments
---

### Post by mike868y on 2007-11-15
I just installed fluxbox and I love it, however I was wondering how to change the gtk theme while in fluxbox I know it must be possible, just not sure how. Also, how do i change the icon theme that appears in thunar while in fluxbox

---

### Post by mike868y on 2007-11-15
k i installed gtk-theme-switch via synaptic, however I can't figure out how to launch it. How would i do this?

---

### Post by spupy on 2007-11-15
The executable of gtk-theme-switch is called switch2. But gtk-theme-switch is used when you dont run the gnome-settinghs-daemon. If you run that deamon, you can change the theme and icons with gnomes theme chooser. gtk-theme-switch can't change the icon set you use. For this you have to edit .gtkrc-2.0 by hand (or use gnome-settings-daemon).

---

