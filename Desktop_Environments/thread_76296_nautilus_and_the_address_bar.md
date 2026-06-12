---
title: "nautilus and the address bar"
date: 2005-10-14
forum: Desktop Environments
---

### Post by mrt on 2005-10-14
CTRL + L restores the address bar in Nautilus "per session".  Is there a way to make this permanent?

---

### Post by codejunkie on 2005-10-14
[quote=mrt]Its hard enough to believe they took the address bar out of nautilus, but even harder to believe that it is not easily restorable.  Does anyone know how to restore the address bar in nautilus?[/quote] press alt+F2 and enter ```
gconf-editor
``` then navigate to apps/nautilus/prefferences then check the box that says always_use_location_entry.

---

### Post by mrt on 2005-10-14
thats it....thank you very much

---

