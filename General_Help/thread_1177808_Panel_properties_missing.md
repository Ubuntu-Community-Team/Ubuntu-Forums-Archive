---
title: "Panel properties missing"
date: 2009-06-03
forum: General Help
---

### Post by Pappy-D on 2009-06-03
For some unknown reason, the properties for the top panel are missing. When I right-click on the panel all I get is 'help' and 'about'.
Have looked everywhere but can't find them. Advise please.

---

### Post by ddixonr on 2009-06-03
Have you tried restarting?: $ killall gnome-panel

---

### Post by Pappy-D on 2009-06-03
Tried that, no change.

---

### Post by Pappy-D on 2009-06-05
Found the answer to this problem on another thread. The following commands restored the properties.

gconftool-2 --recursive-unset /apps/panel
killall gnome-panel

Pappy-D

---

