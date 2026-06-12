---
title: "Setting the enable/disable touchpad keycodes"
date: 2009-05-25
forum: General Help
---

### Post by Nakor BlueRider on 2009-05-25
The following is what I get from dmesg after pressing the enable/disable touchpad button on my laptop twice.

```
[  737.687323] atkbd.c: Unknown key pressed (translated set 2, code 0xd8 on isa0060/serio0).
[  737.687327] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[  737.693558] atkbd.c: Unknown key released (translated set 2, code 0xd8 on isa0060/serio0).
[  737.693561] atkbd.c: Use 'setkeycodes e058 <keycode>' to make it known.
[  739.196950] atkbd.c: Unknown key pressed (translated set 2, code 0xd9 on isa0060/serio0).
[  739.196953] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.
[  739.203202] atkbd.c: Unknown key released (translated set 2, code 0xd9 on isa0060/serio0).
[  739.203206] atkbd.c: Use 'setkeycodes e059 <keycode>' to make it known.

```

e058 is when it should disable the touchpad, e059 to enable it.  SHMConfig is on, and the options interface from the gsynaptec package works fine, just the button isn't mapped and I'm not sure how to map it (or rather, what keycode to map it to).

Thanks in advance!

---

