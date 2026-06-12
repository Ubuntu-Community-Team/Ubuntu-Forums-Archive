---
title: "Disable Compiz Drop Shadow"
date: 2011-07-13
forum: Desktop Environments
---

### Post by Lancelot59 on 2011-07-13
I'm running 11.04 with Gnome 2. I have to have the window decorations on in order to have a menu bar on my programs. The drop shadow settings appear to affect nothing. It only responds to a colour change, and that only to the RGB values. Changing the alpha does nothing. Is there another way to disable the drop shadow?

---

### Post by Lancelot59 on 2011-07-14
Got help in the IRC. To fix the issue you need to change the command in compiz config settings manager under the decorator plugin to:
```
gtk-window-decorator --replace
```
For some reason gnome 2 mode starts using the unity plugin. After doing this I had total control over the shadows.

---

