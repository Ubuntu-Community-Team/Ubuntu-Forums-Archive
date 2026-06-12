---
title: "inside windows in beryl"
date: 2006-12-17
forum: Desktop Environments
---

### Post by hougtimo on 2006-12-17
Hi,

I have just installed beryl and it is quite impressive. Although it does not theme the insides of the windows (scrolbars, buttons etc...) so they look akin to windows 9x controls. I have tried using the normal theme manager for stuff, but that doesn't work. Please tell me there is a way for me to get the insides of the windows themed to?
Thanks

Tim

---

### Post by ayoli on 2006-12-17
the "inside windows" or controls (scrollbar, buttons, ...) are themed by gnome-theme-manager which is under administration>preferences>themes. if themes don't work, maybe you don't have the needed gtk-engine.
Try to run a gtk app from console and look at the output (maybe paste it here) for errors about theme.

---

### Post by mcduck on 2006-12-17
The GTK themes should work with Beryl just like with any window manager. Try running 'gnome-settings-daemon', and if it helps add it to your startup programs (in System/Preferences/Session.

---

