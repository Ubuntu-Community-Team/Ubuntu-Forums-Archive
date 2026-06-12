---
title: "Desktop Embedded Terminal"
date: 2008-12-16
forum: General Help
---

### Post by Soupcan on 2008-12-16
I'm attempting to make one by using the steps in [this guide.]("http://ubuntuforums.org/showthread.php?p=3254093")But I can't find the "Cursor Blinks" option in my edit menus.

---

### Post by Wartender on 2008-12-16
you don't need to do that, actually i 'm not sure what it does really, but i did it without that option and it came out fine.

---

### Post by Locutus_of_Borg on 2008-12-16
use the ~/.Xdefaults file
insert something like ```
XTerm*cursorBlink:false
```
modify for whichever terminal you wish to use.

---

### Post by Soupcan on 2008-12-16
> **Locutus_of_Borg said:**
> use the ~/.Xdefaults file
insert something like ```
XTerm*cursorBlink:false
```
modify for whichever terminal you wish to use.

Okay, I'll try it out when I get back on my laptop.

Wartender:
I'll try that too.

---

