---
title: "[Gnome] turn off &lt;alt&gt;&lt;rightmouse&gt; on window"
date: 2006-11-11
forum: Desktop Environments
---

### Post by zwaardmeester on 2006-11-11
Hi all,

my problem with playing the game Warcraft III using Wine is the following:

I need to hold Alt (displays unit health) and right click simultaneously (move/attack order). Every time i do this, a Gnome popup appears.

This is obviously a bug of Wine, but for now, how can i turn off the popup? (i.e. the same popup you get when <alt><rightclick> in every other window.)

Thanks in advance,

Leo

---

### Post by testube_babies on 2006-11-12
```
gconf-editor
```

You might want to change /apps/metacity/general/mouse_button_modifier

---

