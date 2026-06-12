---
title: "Keyboard Backlight breaks shell"
date: 2013-06-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hencelence on 2013-06-18
Hey there!
I've encountered an issue with my backlit keyboard and I was wondering if you could help me.
I have a backlit keyboard that I can switch via keybind (Fn + &#8594;) to OFF, dim and bright.
Whenever I try to switch it, my keyboard becomes unresponsive in the gnome shell and the shell itself (including WM) become unresponsive.


I am on a Dell Studio 1537 and I'm running Ubuntu Gnome 13.04, fully updated.

lshw gives:
```

...
62: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  Unique ID: c3zD.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:68
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
...
65: PS/2 00.0: 10800 Keyboard
  [Created at input.161]
  Unique ID: eBDb.aMdf3yTkH79
  Hardware Class: keyboard
  Model: "MCE IR Keyboard/Mouse (ite-cir)"
  Device: "MCE IR Keyboard/Mouse (ite-cir)"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event10
  Device Number: char 13:74
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown
...

```

---

### Post by hencelence on 2013-06-27
No one?

---

