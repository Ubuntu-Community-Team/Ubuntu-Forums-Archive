---
title: "How to empty Trash box"
date: 2009-04-11
forum: General Help
---

### Post by satimis on 2009-04-11
Hi folks,


Ubuntu 8.04 workstation.


I can't find the Trash box on desktop. There is NOTHING there only the background. I can find it on terminal running;

# ls -l /root


Please advise how to empty Trash box with gui on desktop? TIA.


B.R.
satimis

---

### Post by Paul41 on 2009-04-11
Look at the very bottom right of your screen on the panel. By default there is a trash bin there. If yours is missing you can add one to a panel by right clicking and choose "Add to panel...". There is a option to add a trash bin there.

---

### Post by neu2buntu on 2009-04-11
also anyone wanting to add the wastebasket to their desktop for example if using "awn" open terminal and do:. ```
gconf-editor
``` then goto >apps>nautilus>desktop and tick "trash_icon_visible" this will place it on desktop ,where it can be dragged to preferred place.  only 1 problem is when you realign your desktop icons the wastebasket also moves,so it needs dragged back.

---

### Post by satimis on 2009-04-11
> **Paul41 said:**
> Look at the very bottom right of your screen on the panel. By default there is a trash bin there. If yours is missing you can add one to a panel by right clicking and choose "Add to panel...". There is a option to add a trash bin there.
Hi Paul41,


I found it there, a small icon.  Thanks


B.R.
satimis

---

### Post by satimis on 2009-04-11
Hi neu2buntu,


Thanks for your advice.

> **neu2buntu said:**
> also anyone wanting to add the wastebasket to their desktop for example if using "awn" open terminal and do:. ```
gconf-editor
``` then goto >apps>nautilus>desktop and tick "trash_icon_visible" this will place it on desktop ,where it can be dragged to preferred place.  

It has been checked already.

> 
only 1 problem is when you realign your desktop icons the wastebasket also moves,so it needs dragged back.
Whether dragging it back from the "waste_basket" icon on the right bottom corner?


B.R.
satimis

---

### Post by neu2buntu on 2009-04-11
im using "awn" avant-window-navigator .. and i have no bottom panel as i removed it for this purpose (so no wastebasket) . so this is probably why my "trash_icon_visible" was unchecked. then checking it without a bottom panel must default it to go to the desktop instead.  heres a screenshot of my Desktop........

---

### Post by satimis on 2009-04-11
> **neu2buntu said:**
> im using "awn" avant-window-navigator .. and i have no bottom panel as i removed it for this purpose (so no wastebasket) . so this is probably why my "trash_icon_visible" was unchecked. then checking it without a bottom panel must default it to go to the desktop instead.  heres a screenshot of my Desktop........
Noted with thanks

B.R.
satimis

---

