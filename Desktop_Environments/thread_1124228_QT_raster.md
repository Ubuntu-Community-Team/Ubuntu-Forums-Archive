---
title: "QT raster"
date: 2009-04-13
forum: Desktop Environments
---

### Post by ikkefc3 on 2009-04-13
Hello,
I saw that the QT raster graphics system boosts the drawing performance a lot. In Kubuntu Jaunty, which I use, you can let an individual QT program  use the QT raster system by adding " -graphicssystem raster" to the shortcut or command (via ALT+F2). How can I let all the programs launch with the QT raster system? (set it default or something)

---

### Post by ikkefc3 on 2009-08-14
> **ikkefc3 said:**
> Hello,
I saw that the QT raster graphics system boosts the drawing performance a lot. In Kubuntu Jaunty, which I use, you can let an individual QT program  use the QT raster system by adding " -graphicssystem raster" to the shortcut or command (via ALT+F2). How can I let all the programs launch with the QT raster system? (set it default or something)

Is there still no one that knows the answer?

---

### Post by L_V on 2010-08-20
1. go to /usr/share/autostart
2. make a backup of plasma-desktop.desktop
3. open for edit plasma-desktop.desktop
4. add **--graphicssystem raster** at the end of =plasma.desktop

---

