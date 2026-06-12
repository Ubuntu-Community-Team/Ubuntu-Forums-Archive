---
title: "opening nautilus in fluxbox"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Rule on 2006-09-24
hey, I have a link to open nautilus using idesk, but when I click on it my wallpaper goes away and starts to use metacity, the only way I found to fix it is to use "killall -9 nautilus" and then set the wallpaper again. Is there away I can open nautilus without have to go through all this?

TIA
Rule

---

### Post by ayoli on 2006-09-24
nautilus handles desktop by default, if you don't want that launch it like this:
```
nautilus --no-desktop
```

---

### Post by Rule on 2006-09-24
ahh thank you that was getting very annoying :D

---

