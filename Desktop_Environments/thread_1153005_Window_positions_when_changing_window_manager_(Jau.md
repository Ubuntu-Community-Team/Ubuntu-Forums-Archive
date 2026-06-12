---
title: "Window positions when changing window manager (Jaunty)"
date: 2009-05-08
forum: Desktop Environments
---

### Post by mrchan on 2009-05-08
Hi,

When changing window managers in Jaunty i.e. from metacity to compiz using compiz -replace and vice versa, all window positions are set to the top right corner. In Hardy, this is not the case; windows will keep their relative positions to the workspace when changing the window manager. Also I had been writing a script using wmctrl to change window positions after changing window managers. The script worked perfectly in Hardy, but did not work in Jaunty. I found out that in Hardy, the window IDs returned by wmctrl -l stay the same after changing window managers, however in Jaunty the window IDs all change when the window manager is changed. Could someone please explain this and how I can keep window positions the same?

---

