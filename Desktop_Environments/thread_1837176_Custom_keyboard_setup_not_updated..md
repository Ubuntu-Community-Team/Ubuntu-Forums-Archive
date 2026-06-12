---
title: "Custom keyboard setup not updated."
date: 2011-09-01
forum: Desktop Environments
---

### Post by rylleman on 2011-09-01
I have two keyboards connected and 2nd one setup with a custom keyboard layout as [[COLOR="Red"]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1560537").

It does work but keyboard layout doesn't update when I try to reload it with setxkbmap.

If I save the keymap file in /usr/share/X11/xkb/symbols with a different name and change my name in evdev.xml accordingly I can update to the modified version of the layout. 
It is like the actual file is not used when applying it but some version stored in memory.

What is happening?

---

