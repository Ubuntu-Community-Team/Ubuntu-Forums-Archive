---
title: "Ugly white shadows with compiz fusion"
date: 2007-10-17
forum: Desktop Effects &amp; Customization
---

### Post by sammydee on 2007-10-17
Hi All

Got compiz fusion running on an nvidia geforce go 7400 on Ubuntu Gutsy.

It works great, the only problem is that every time I boot up, the top and bottom menu bars, and any menus dropped down have a horrible white border that looks like a bug in the rendering of shadows. Also, if I change virtual desktops using ctrl-alt-left/right/up/down the box that appears to show which desktop you are on shows as solid white.

The really weird thing is, if I system/preferences/appearance and change the system effects setting from "Extra" to "custom" the white borders go away...!? If I enable then disable motion blur in advanced settings, the change desktop box renders correctly.

The effects setting is always set to "extra" on bootup instead of "custom" but all the customised effects I use stay the same whichever I select.

Anybody got any ideas on this rather bizarre bug?

Sam

Edit: It seems as if merely opening the appearance application from system/preferences is enough to get rid of the white bits. Go figure.

---

### Post by ShinyMcShine on 2007-10-19
I've just remove the shadow effect till it's fixed. For the Compiz settings choose the Window Decorator plugin. In the Decoration Windows change the setting "any" to "none".
Ugly shadows is removed till the shadows in Compiz can be shown correctly. But Gutsy is pretty new.

---

### Post by Forlong on 2007-10-19
> **sammydee said:**
> Anybody got any ideas on this rather bizarre bug?
Yes, I reported a bugreport about this, which includes a workaround: [https://bugs.launchpad.net/bugs/141361](https://bugs.launchpad.net/bugs/141361)

---

### Post by sammydee on 2007-10-25
Aah thanks.

I fixed the problem by using the emerald window decorator instead of gtk in the end.

Sam

EDIT: BTW I see the bug report lists the problem as happening with intel and radeon drivers only. I am using nvidia proprietary drivers.

---

