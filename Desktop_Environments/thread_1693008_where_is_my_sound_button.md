---
title: "where is my sound button?"
date: 2011-02-22
forum: Desktop Environments
---

### Post by wilander on 2011-02-22
It disappeared from the up-right corner! I also lost the turn-off button :-/
Is there a place where I can find all the gnome-buttons? When I click "add to panel" I only get the possibility to add some other buttons, but not the original once!

---

### Post by Frogs Hair on 2011-02-22
The sound indicator is included with the indicator applet on the add to panel menu. To restore panel to defaults use the code in the terminal.
```

gconftool --recursive-unset /apps/panel && killall gnome-panel
```

---

### Post by wilander on 2011-02-22
thanks!! :)

---

