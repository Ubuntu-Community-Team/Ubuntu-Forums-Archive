---
title: "Multiple desktops not working"
date: 2009-07-24
forum: Desktop Environments
---

### Post by starbase1 on 2009-07-24
One of the features I really like is being able to switch between mutiple desktops.

But recently it's stopped working. This happened after I tried to increase the number from 2 to 4. Now I only have one! I can click to get the settings, and try to get others, but it does not work.

Is there a way to reset this, or something similar?

I am running Ubuntu 64 bit, 9.04, with the latest updates applied.

---

### Post by wojox on 2009-07-24
Right click and remove it from panel.

Then right click panel +Add to panel scroll down to Workspace switcher.

---

### Post by SteveDee on 2009-07-24
> **starbase1 said:**
> One of the features I really like is being able to switch between mutiple desktops.

But recently it's stopped working. This happened after I tried to increase the number from 2 to 4. Now I only have one! I can click to get the settings, and try to get others, but it does not work.

Is there a way to reset this, or something similar?

I am running Ubuntu 64 bit, 9.04, with the latest updates applied.

You could try resetting this using the Configuration Editor (under Applications > System Tools).

From this editor navigate to: /apps/compiz/general/screen0/options/number_of_desktops  and check or change settings.

---

### Post by starbase1 on 2009-07-26
Right click remove did not work, but once I'd worked out that I needed to start gconf-editor from a command line (hey I'm getting techie here! :D), that did the trick!

Thanks

---

### Post by starbase1 on 2009-07-26
Hmmm... Looks like a spoke too soon.
I have multiple desktops now, but the top left drop down program menus only appear on the first one, and the tiny previews seem bust...

---

