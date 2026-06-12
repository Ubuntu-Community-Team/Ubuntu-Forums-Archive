---
title: "desktop effects killed KDE :("
date: 2009-03-24
forum: General Help
---

### Post by spyder0101 on 2009-03-24
I just enabled desktop effects in Kubuntu and the screen went white. Since I have disabled it via changing enabled to false under compositing in ~/.kde4/share/config/kwinrc and running ```
sudo apt-get remove --purge compiz-core
```, however I still get my white screen on rebooting.  Is there any way to get X back?

---

### Post by spyder0101 on 2009-03-24
*sigh*

Seems I can't spell false. Setting it to "flase" does nothing, "false" fixes it.  Problem solved.

---

### Post by PetterDK on 2009-03-24
You could try to change which window decorator is used by the system..

To do that from the console try:

```
sudo gtk-window-decorator --replace
```

---

