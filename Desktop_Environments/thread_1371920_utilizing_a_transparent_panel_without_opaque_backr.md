---
title: "utilizing a transparent panel without opaque backrounds"
date: 2010-01-03
forum: Desktop Environments
---

### Post by PatrickMoore on 2010-01-03
ok so i have a theme on my panels that is transparent but the backround of my tools (notification area, window switcher etc.) are opaque is there a way to make all backrounds transparent?

---

### Post by stinkeye on 2010-01-04
> **PatrickMoore said:**
> ok so i have a theme on my panels that is transparent but the backround of my tools (notification area, window switcher etc.) are opaque is there a way to make all backrounds transparent?
I usually delete the panel-bg.png in the current theme folder,
but I just had a play around with the gtkrc file and this seems to work.
Go to ~/.themes 
(May have to go to /usr/share/themes and edit as root,
depending on where you installed the theme.)
Open the gtkrc file in the folder of your current theme,search for panel
 and Hash out *[COLOR="Red"]include"styles/panel"[/COLOR]* to give you...
```
#include"styles/panel"
```

You can also change the colour of your panel font with *gnome-color-chooser*.

---

