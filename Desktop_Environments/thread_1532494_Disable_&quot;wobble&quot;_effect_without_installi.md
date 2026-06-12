---
title: "Disable &quot;wobble&quot; effect without installing new porgram"
date: 2010-07-16
forum: Desktop Environments
---

### Post by usersock on 2010-07-16
Is there a way to disable the wobble visual effect without installing an additional program, such as simple-ccsm?

EDIT: My bad, I should add that I would like to keep the visual effects set to "Extra", if at all possible.

---

### Post by potat on 2010-07-16
Try going into gconf-editor and changing /apps/compiz/general/allscreens/options/activeplugins and removing "wobbly" from the list. Don't know if that will keep you in "Extra" mode. If it doesn't work, try modifying the settings (thru gconf or ccsm) so that there is no wobbling even if the plugin is enabled.

---

### Post by potat on 2010-07-16
One question though, why do you want it to be set to Extra? Just curious.

---

### Post by usersock on 2010-07-17
I wanted it set to Extra so I could use docks, like Gnome Do or Cairo. I didn't realize I could still use them with the visual setting set to Normal, which does not have the wobbly feature. 

Thanks for your help potat  :)

---

### Post by digitalcitizenx on 2010-07-17
> **usersock said:**
> I wanted it set to Extra so I could use docks, like Gnome Do or Cairo. I didn't realize I could still use them with the visual setting set to Normal, which does not have the wobbly feature. 

Thanks for your help potat  :)

Metacity has a compositing feature also.

If all you need is the docks to display normally then stop Compiz and start Metacity - then enable compositing in Metacity. I believe this will use less system resources also.

---

