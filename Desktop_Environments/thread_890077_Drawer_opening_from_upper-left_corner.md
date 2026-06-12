---
title: "Drawer opening from upper-left corner"
date: 2008-08-14
forum: Desktop Environments
---

### Post by VOLKOV9 on 2008-08-14
I right-clicked a launcher in my Applications menu and said Entire Menu->Add this as a Drawer to Panel, and everything worked fine.  I customized it a little via right clicking it and going to Properties.  All was well.  I wanted to change more options, so after reading a couple threads here, I opened up Applications->System Tools->Configuration Editor (which I perhaps should note was initially not shown in the Applications menu), and went to /->apps->panel->toplevels->panel_6, which seems to describe this particular drawer.  I started by unchecking enable animations, and exiting gconf-editor.

Now, when I click the drawer (found in the panel on the bottom of my screen), the drawer opens in the upper left corner (though animation, I note, is successfully disabled).  Whenever I change any setting via Properties, it comes out in the correct place the first time I click it, and reverts to the corner for all clicks thereafter.

Anyone have any clue on how I can get it to consistently open in the correct location?

Thanks.

PS:  The subdrawers still animate, which I imagine is because they are controlled by other entries in gconf-editor.  The interesting part is that it seems that their horizontal position corresponds to the misplaced drawer, but their horizontal position is correct (about 1/3 from the left of the screen, where the button for the drawer is on my panel).

---

### Post by VOLKOV9 on 2008-08-18
*bump*

---

### Post by VOLKOV9 on 2008-09-05
...bump?

---

