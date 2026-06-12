---
title: "Dell mini 10v Ubuntu hotkeys"
date: 2009-07-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by OldJohnB on 2009-07-01
Does anyone know how the volume (up down & mute) hotkeys are configured in Ubuntu 8.04 on the Dell mini 10v. I can see from the code that LCD brightness is controlled through acpi but the volume hotkeys do not produce acpi key codes so I assume they are working directly with X in some way? Any ideas?

---

### Post by coffeeaddict22 on 2009-07-01
System/Preferences/Keyboard Shortcuts also has a selection of options that may be of use.
If that doesn't work, try going into System/Preferences/Keyboard and checking you've got the right Keyboard set in there.  There's a button for layout options you need to check under.  

Any x inputs can be seen by using xev.  type it in a terminal, and you'll see what the output is when you hit a key.

---

