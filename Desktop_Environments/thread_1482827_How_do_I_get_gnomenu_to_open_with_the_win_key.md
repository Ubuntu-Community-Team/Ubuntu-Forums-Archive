---
title: "How do I get gnomenu to open with the win key?"
date: 2010-05-14
forum: Desktop Environments
---

### Post by Peace_n_Pedals on 2010-05-14
Hi,

I'm really new to ubuntu and I'm still on that steep learning curve but have been enjoying playing around with the desktop environment. I've installed gnomenu and would like my win key to open it. 

How do I manage to do this? I notice in the Gnomenu Settings that the "Bind keyboard key ex: Super_L" is ticked but not sure what this means exactly.

Any help would be much appreciated.

Thanks!
:)

---

### Post by wojox on 2010-05-14
Try:

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

---

### Post by Peace_n_Pedals on 2010-05-14
Thanks wojax. That kind of worked. Although it opens the default main menu in ubuntu (still quite useful) rather than the gnomenu that I've added to the panel instead.

I'm not very confident using the terminal so any tips would be great.

Thanks

---

### Post by Peace_n_Pedals on 2010-05-14
It seems I can't have it all! Now I can't use other keyboard shortcuts that use the win key that I'd set up via the Keyboard preferences.

How do I reverse the above?

Thanks!

---

### Post by wojox on 2010-05-14
Run

```
gconftool-2 –set /apps/metacity/global_keybindings/panel_main_menu –type string "<Alt>F1"
```

---

### Post by vodkasolution on 2010-12-17
sorry, wrong post!

---

