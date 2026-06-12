---
title: "Swap minimize and restore buttons"
date: 2010-03-19
forum: Desktop Environments
---

### Post by sabrehagen on 2010-03-19
Hi Everybody,

I have moved my restore+minimise+close buttons to the right hand side of the screen, but the restore and minimise buttons are swapped. I would like to have them in the same layout as Windows i.e. in the order of minimise+restore+close.

Thanks for your help!


sabrehagen

---

### Post by mcduck on 2010-03-19
Press Alt-F2 and run "gconf-editor". USe that to browse to apps/metacity/general, and set the "button_layout" to "menu:minimize,maximize,close". (you can leave the "menu" away from the string if you don't want the menu button in the left side of the title bar)

Note that if you use the new themes included in 10.04 (Ambiance & Radiance) they will look bit nasty with that button order, since the button images were made to be used in different order. Any older themes will of course work just fine.

---

### Post by sabrehagen on 2010-03-19
Thank you for your help! There is so much about Ubuntu I've yet to learn, but I look forward to learning none the less!

---

### Post by zipperback on 2010-04-28
> **mcduck said:**
> Press Alt-F2 and run "gconf-editor". USe that to browse to apps/metacity/general, and set the "button_layout" to "menu:minimize,maximize,close". 

No need for people to use gconf-editor to modify it, they can download and install Ambiance_R

[http://ubuntuforums.org/showpost.php?p=9186310&postcount=1](http://ubuntuforums.org/showpost.php?p=9186310&postcount=1)

- zipperback

---

### Post by Skaperen on 2010-04-28
Things like this really should be more simply configured by right click on the object or holder of objects of interest, and select properties.  That should bring up whatever allows configuration of that.  In the case of buttons on window decorations, doing the right click on the title bar to get the properties selection should be enough.  That doesn't mean there shouldn't be a general configuration manager for everything (there still should be).  But there should be all these shortcuts to them (unless intentionally disabled in the general configuration).

---

### Post by RCRedneck on 2010-10-14
Muchas Gracias Muchachos.....

---

