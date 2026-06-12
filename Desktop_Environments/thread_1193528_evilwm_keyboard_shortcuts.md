---
title: "evilwm keyboard shortcuts"
date: 2009-06-21
forum: Desktop Environments
---

### Post by PurposeOfReason on 2009-06-21
Does anybody know a way to remap evilwm keyboard shortcuts? I find it really silly that close is ctrl+alt+esc. It is really out of the way. I'd settle for a way to do it with xbindkeys that when something like super+c is pressed, the current window is closed.

---

### Post by hrod beraht on 2009-09-02
You can remap the ctrl+alt combo by using the **-mask1** modifier when starting Evilwm. The super key is *mod4*.
For example, here's my ~/.xinitrc line, which starts Evilwm with a 10-pixel snap to other windows distance, a border width of 2, an active window border color of red, and the ctrl+alt key-combo changed to the super key:
```
exec evilwm -snap 10 -bw 2 -fg red -mask1 mod4
```

Although, this won't remap the *esc* part of the key-combo.
Usually, I find it's easiest to just close the window via the actual app that's running. That is, ctrl+f (file) and x (exit) or c (close) for gui apps, or just *exit* or ctrl+d for a terminal.

Bob

---

### Post by PurposeOfReason on 2009-09-02
Thanks for this but I found it easier to grab the source (using gentoo here) and changing the keybindings file. It is actually a pretty readable file.

---

