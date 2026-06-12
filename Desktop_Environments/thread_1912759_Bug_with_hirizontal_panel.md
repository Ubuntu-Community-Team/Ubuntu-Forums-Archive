---
title: "Bug with hirizontal panel"
date: 2012-01-21
forum: Desktop Environments
---

### Post by nxhoaf on 2012-01-21
Hi there, 
   I've just installed Ubuntu11.04, As I'm familiar with vertical panel, I changed the horizontal panel (the default one) to the vertical. But it seems not to work with me. And here is the bug:
[http://www.youtube.com/watch?v=6Gc0gk5_c9U](http://www.youtube.com/watch?v=6Gc0gk5_c9U)
  Can anyone tells me how can I fix it ?

---

### Post by Frogs Hair on 2012-01-21
Is this in Classic Ubuntu with or have you disabled Unity enabled the gnome panel in Unity ? If using Classic Ubuntu try the following command to reset the panel .```
gconftool --recursive-unset /apps/panel && killall gnome-panel 
```

---

