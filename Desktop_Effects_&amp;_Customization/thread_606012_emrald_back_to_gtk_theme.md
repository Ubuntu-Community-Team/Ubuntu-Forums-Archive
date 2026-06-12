---
title: "emrald back to gtk theme"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by fedex1993 on 2007-11-07
okay well i booted up my system and it auto switched to the defualt ermrald theme is there anyway that i can switch back to gtk i am using 7.10

---

### Post by amadeus266 on 2007-11-07
```
gtk-window-decorator --replace
```

I put a link on my panel so I can switch back and forth.

---

### Post by Forlong on 2007-11-08
If you don't want to do this manually, just remove emerald.

If you want to keep Emerald, try this:
```
gedit ~/.config/compiz/compiz-manager
``` put this in there
```
USE_EMERALD="no"
```
And save.

If you do, please let me know if it worked.

---

### Post by fedex1993 on 2007-11-08
ty it worked

---

