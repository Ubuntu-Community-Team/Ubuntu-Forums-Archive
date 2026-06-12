---
title: "Hiding mounted devices icons"
date: 2006-05-30
forum: Desktop Environments
---

### Post by DanielArdelian on 2006-05-30
Can anyone please tell me how I could hide the icons for mounted devices that appear on the desktop ? (sda1 ... sda7, etc) ?

  I really like my desktop completely clean, but I need those devices mounted and I could not find a way to get rid of the icons completely. I prefer accesing them from the "Places" menu, where I'd like to keep them :D

  Running Ubuntu 5.10 Breezy

  Thanks !

---

### Post by aysiu on 2006-05-30
Press Alt-F2 and type ```
gconf-editor
``` Then go to Apps > Nautilus > Desktop

There should be an option to not have them appear on the desktop.

Alternatively, you could try not mounting them in the /media folder.

---

### Post by DanielArdelian on 2006-05-30
Yes, found it, it's called "volumes_visible".
Thanks !

---

