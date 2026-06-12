---
title: "Gnome Terminal command in KDE/Konsole"
date: 2009-08-30
forum: Desktop Environments
---

### Post by Intrepid Ibex on 2009-08-30
Hi,

  I'd just like to know that what is the correct alternative of Gnome/Gnome Terminal...:
```
gnome-terminal -x bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
``` ... with KDE/Konsole.

---

### Post by oldos2er on 2009-08-30
I believe you would simply replace gnome-terminal with konsole, i.e.  
```
konsole -x bash -c "sudo apt-get update && sudo apt-get dist-upgrade;read -n1"
```
 Not sure if **-x** is applicable to konsole though.

---

### Post by Intrepid Ibex on 2009-08-31
Yeah, but you see I use arch linux so I tested that a long ago before I created this topic ^^.

---

