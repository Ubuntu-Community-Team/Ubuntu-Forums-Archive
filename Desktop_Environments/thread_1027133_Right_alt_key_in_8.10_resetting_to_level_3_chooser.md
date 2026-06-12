---
title: "Right alt key in 8.10 resetting to level 3 chooser"
date: 2008-12-31
forum: Desktop Environments
---

### Post by dhasenan on 2008-12-31
Hi,

I'm using E17 as my window manager (no GNOME / KDE / what have you). In 8.04, I changed my xorg.conf to use the right alt key for Alt_R. In 8.10, this entire section of xorg.conf was commented out, with the note "HAL is now used".

I tried using xmodmap to get my beloved Alt_R back, but this resets every few minutes. I really don't want to run xmodmap continuously. How do I tell HAL not to mess with my right alt key?

---

### Post by dhasenan on 2008-12-31
On further reflection, this option is getting erased whenever I change keyboard layouts. I want it to apply always.

I can add something like "e06C:rightalt" to input.keymap.data:
```

<?xml version="1.0" encoding="UTF-8"?>
<!-- /etc/hal/fdi/policy/10-keyboard.fdi -->
  <deviceinfo version="0.2">
    <device>
      <match key="info.capabilities" contains="input.keymap">
        <merge key="input.keymap.data" type="strlist">e06C:rightalt</merge>
      </match>
    </device>
  </deviceinfo>
```

This doesn't do what I want, though.

---

