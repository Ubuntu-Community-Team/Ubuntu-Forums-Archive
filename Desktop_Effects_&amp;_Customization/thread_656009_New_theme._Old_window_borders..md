---
title: "New theme. Old window borders."
date: 2008-01-02
forum: Desktop Effects &amp; Customization
---

### Post by Roasted on 2008-01-02
I just changed to a new theme. My last one was mostly reddish/silver, which was nice. This one is black/bright steal blue, yet my window borders on the active windows are still the reddish color which looks ridiculous. How can I switch it back? Under appearance, when I go to window border, the icon preview of what I have selected is black. Yet, my window borders are red. 

Blah. :(

---

### Post by FuturePilot on 2008-01-02
Either remove Emerald or create this file
```
gedit .config/compiz/compiz-manager
```
Put this line in there
```
USE_EMERALD="no"
```
The next time you login, Emerald will be disabled.

---

