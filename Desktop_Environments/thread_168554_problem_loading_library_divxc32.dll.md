---
title: "problem loading library divxc32.dll"
date: 2006-04-30
forum: Desktop Environments
---

### Post by ekravche on 2006-04-30
I'm having this issue. When I try to open wmv files I get problem loading library divxc32.dll error message in Totem. Anyone, knows how to address this?

---

### Post by ekravche on 2006-04-30
[QUOTE=ekravche]I'm having this issue. When I try to open wmv files I get problem loading library divxc32.dll error message in Totem. Anyone, knows how to address this?[/QUOTE]

After looking at my ~/.xine/catalog.cache I've noticed that I had 2 similar entries for section 

[/usr/lib/xine/plugins/1.0.1/xineplug_decode_w32dll.so]

By deleting one section that seem to have fixed the divxc32.dll error message, and now I can load wmv files again.

---

