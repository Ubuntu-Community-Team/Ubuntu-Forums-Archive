---
title: "Gnome panel appears to be broken"
date: 2011-02-02
forum: Desktop Environments
---

### Post by kiransripathy on 2011-02-02
For few days I'm having problem with the gnome panel. It appears to be distorted. The turn off button is invisible forcing me to visit the login window to use the turn off option. I uploaded the screenshot of the desktop with the malfunctioning panel. Any help regarding this will be appreciated.

---

### Post by Frogs Hair on 2011-02-02
Try right clicking the panel icons and moving them to the left or reset panels to defaults```
gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by kiransripathy on 2011-02-02
Restarted the panel using the above code. Thanks for the immediate reply.

---

### Post by Frogs Hair on 2011-02-02
Your Welcome I hope it stays put.

---

