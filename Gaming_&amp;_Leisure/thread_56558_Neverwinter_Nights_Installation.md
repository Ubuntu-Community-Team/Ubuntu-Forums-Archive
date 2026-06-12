---
title: "Neverwinter Nights Installation"
date: 2005-08-13
forum: Gaming &amp; Leisure
---

### Post by ItIsMe on 2005-08-13
I just downloaded the Ravage installer for Neverwinter Nights but when I try to run it I get a message saying


error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


Does anyone know how to fix this?

---

### Post by rpgcyco on 2005-08-13
It seems as if you haven't got the GTK1 libraries installed. Try this.

```
sudo apt-get install libgtk1.2
```

- Rpg Cyco

---

