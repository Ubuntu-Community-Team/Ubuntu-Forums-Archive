---
title: "Up-Arrow key problem in Terminal"
date: 2005-10-18
forum: Desktop Environments
---

### Post by blastus on 2005-10-18
Whenever I press the up-arrow key in a terminal to repeat/edit a previous command, four messages are added to /var/log/messages every time.

```
Oct 18 19:37:51 localhost kernel: [4302242.876000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
Oct 18 19:37:51 localhost kernel: [4302242.876000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
Oct 18 19:37:51 localhost kernel: [4302242.961000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
Oct 18 19:37:51 localhost kernel: [4302242.961000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
```

What does this mean? The up-arrow key seems to work. :???:

---

