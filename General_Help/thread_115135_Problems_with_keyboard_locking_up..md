---
title: "Problems with keyboard locking up."
date: 2006-01-09
forum: General Help
---

### Post by bb002 on 2006-01-09
I think this may actually be a prelude to my keyboard failing but let's make sure.

My keyboard will randomly freeze up. Sometimes once a month. Sometimes three times in a day (those are rare). All I have to do to fix is reach around back and remove/reinstert the ps/2 keyboard. Just now I did some looking around my log files and "dmesg" has 
```

[4303152.399000] atkbd.c: Unknown key pressed (translated set 2, code 0xaa on isa0060/serio0).
[4303152.399000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.
[4303152.482000] atkbd.c: Unknown key released (translated set 2, code 0xaa on isa0060/serio0).
[4303152.482000] atkbd.c: Use 'setkeycodes e02a <keycode>' to make it known.

``` repeated over and over with only the part in square bracket changing.

I looked up the keycode 0xAA and that seems to be "successful power-on test".  Nice...My keyboard is powering on after powered on? O__0

---

