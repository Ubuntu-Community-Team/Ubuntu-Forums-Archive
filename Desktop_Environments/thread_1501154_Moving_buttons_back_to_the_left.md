---
title: "Moving buttons back to the left"
date: 2010-06-03
forum: Desktop Environments
---

### Post by andrewdied on 2010-06-03
Bottom line up front: I'd like to move my window controls from the right corner to the left corner in 10.04.

All of my window controls (minimize, close, etc) are back on the right hand corner of the window, and after my upgrade from 9.10 to 10.04 they were on the left.  I briefly tried E16 with gnome, didn't like it, and removed all.  This caused metacity to become unconfigured, and now all of the themes have window controls on the right.

Where can I fix it so the window controls are back where the 10.04 ubuntu wanted them?  Thanks for the help.

---

### Post by wilee-nilee on 2010-06-04
> **andrewdied said:**
> Bottom line up front: I'd like to move my window controls from the right corner to the left corner in 10.04.

All of my window controls (minimize, close, etc) are back on the right hand corner of the window, and after my upgrade from 9.10 to 10.04 they were on the left.  I briefly tried E16 with gnome, didn't like it, and removed all.  This caused metacity to become unconfigured, and now all of the themes have window controls on the right.

Where can I fix it so the window controls are back where the 10.04 ubuntu wanted them?  Thanks for the help.

alt-f2 enter gconf-editor go to apps-metacity-general-button_layout and edit the key by right clicking to this,
close,minimize,maximize:
this is the stock setup you can put the buttons in whatever order you would like, note the : is the indicator to R or L side.

---

### Post by elliotn on 2010-06-04
The other themes have not changed the buttons, plus i love the new change

---

### Post by andrewdied on 2010-06-04
wilee-nilee, that was it.  Thanks, I would never have found that value!

---

### Post by wilee-nilee on 2010-06-04
> **andrewdied said:**
> wilee-nilee, that was it.  Thanks, I would never have found that value!

the gconff-editor is a excellent way to tweak things once you know what it offers and can do.

---

### Post by blur xc on 2010-06-04
that's good to know- I knew it was easy but haven't gotten around to looking it up.  

I've been slightly annoyed that switching themes was tossing my window controls left and right and back again...  

thanks,
BM

---

