---
title: "xmodmap script breaks alt-tab to switch windows"
date: 2010-08-14
forum: Desktop Environments
---

### Post by dewdrop_world on 2010-08-14
I'm using this xmodmap script to move the modifiers the way I like them.

```
!note: This disables iso_level3_shift/mode_switch, maybe fix later
clear control
clear mod1
clear mod4
clear mod5
keycode  37 = Super_L
keycode 133 = Alt_L
keycode  64 = Control_L
keycode 108 = Control_R
keycode 135 = Alt_R
keycode 105 = Menu
add control = Control_L Control_R
add mod1    = Alt_L Alt_R
add mod4    = Super_L
```

After running the script, though, window manager keyboard shortcuts using Alt no longer do anything. Apps can pick up Alt just fine, but Alt-Tab just makes the cursor blink but nothing happens.

Why would that be? Is there a way to change the script so it doesn't break things like Alt-Tab?

Currently using ctrl-f12 instead of alt-tab for window switching, but I don't like it and would like to go back to the standard shortcut.

Thanks.

---

### Post by sa-mejia on 2010-08-19
Have had similar issue, and am curious to know what went wrong.

bump

---

