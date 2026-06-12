---
title: "any themes with right side buttons?"
date: 2011-10-18
forum: Desktop Environments
---

### Post by ottosykora on 2011-10-18
It seems that no previous themes do work under 11.10

Are there any themes with buttons on the right side for download somewhere?

---

### Post by jmate24 on 2011-10-18
you can change the side and the size of the buttons and also the transparancy of the top bar if you install in a terminal:

```
sudo apt-get install gconf-editor
```

then open the application "Configuration Editor" then in the left pane click on apps>compiz-1>unityshell>screen0>options then in the right top pane change the 'launcher_reveal_edge' from 'Left' to 'Right' and make sure the 'R' is capitalized. then you can change the size of the icons where it says icon_size from 48 to 32 if you want more screen real-estate. then the opacity of the top panel: panel_opacity from 1 to .5 or less depending on preference.

p.s. always hit enter after you enter a new value to set it the new settings will go in effect when you restart.

---

