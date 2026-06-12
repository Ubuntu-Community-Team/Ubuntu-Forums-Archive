---
title: "Menus are too wobbly"
date: 2006-09-17
forum: Desktop Environments
---

### Post by 3rdalbum on 2006-09-17
I just upgraded my Compiz from one about a month old, to the latest one from Quinn's.

It's very nice, someone has done some optimising of the code and many of the effects are set to sane defaults. However, on my older version I had customised the menu animation so the menus don't wobble much. On this new version, they give me seasickness.

I had an extensive play around with that new Compiz settings manager, but nothing I do seems to stop the menus from wobbling.

How can I restrain the menu animation? (I still have gset-compiz, if this will help).

---

### Post by oldmanstan on 2006-09-17
i found that the compiz settings tool is still a little buggy and often when i would change settings using it, the settings wouldn't actually change.

i used the configuration editor (should be in the system menu, you might have to install it) to directly change the settings.

---

### Post by ayoli on 2006-09-17
here is my settings for menus
in csm > wobbly windows > numeric values tab:
map friction: 2.4
map spring: 4.0

@oldmanstan: i dunno how your store settings in gconf since compiz doesnt use anymore gconf plugin.

---

### Post by Lord Illidan on 2006-09-17
> **ayoli said:**
> here is my settings for menus
in csm > wobbly windows > numeric values tab:
map friction: 2.4
map spring: 4.0

@oldmanstan: i dunno how your store settings in gconf since compiz doesnt use anymore gconf plugin.


Try using csm.

---

### Post by ayoli on 2006-09-17
> **Lord Illidan said:**
> Try using csm.

**I** use csm :)

---

