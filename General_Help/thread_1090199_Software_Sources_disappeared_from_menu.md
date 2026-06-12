---
title: "Software Sources disappeared from menu"
date: 2009-03-08
forum: General Help
---

### Post by alexbrand09 on 2009-03-08
Software Sources disappeared from my System -> Administration menu.

The Main Menu tool in System -> Preferences -> Main Menu doesn't seem to help either. When I check the Software Sources, it un-checks again. 

Any ideas?

I'm on Ubuntu 8.10

---

### Post by dzark on 2009-03-08
try pressing alt-f2 or in a terminal and running

```
gksu software-properties-gtk
```

---

### Post by adult swim on 2009-03-08
if you press alt+f2 and enter in ```
gksu software-properties-gtk
``` does it work then?
EDIT: too slow for dzark :)

---

### Post by dzark on 2009-03-08
1

---

### Post by alexbrand09 on 2009-03-08
Yeah it does work from the terminal.

But I want to add it back to the menu.

I noticed now that any change I do in the Main Menu editor (System->Preferences->Main Menu) gets unchecked after 1 second I check it.

Thanks for the help!

---

