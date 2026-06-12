---
title: "e-uae"
date: 2011-08-10
forum: Gaming &amp; Leisure
---

### Post by liquid boy on 2011-08-10
i'm a bit lost, using 3-uae, playing gods, it sort of works when i use the mouse option, but when i check "curser keys", they don't work.

i've looked ofr a guide on the interblag but found nothing helpful, maybe i havn't looked for the right phrases?

anyone have a beginners guide to how to assign keys (as far as i can see this cant be done?)

---

### Post by Brebs on 2011-08-12
As a bit of a hint, to use the Ctrl key on the left of the keyboard (instead of the right), I change the sourcecode:
```
# Use left side of keyboard instead of right, for player 1
sed -i -e "s:RCTRL:LCTRL:" -e "s:RALT:LALT:" -e "s:RSH:LSH:" src/keybuf.c &&

# Add missing definition for left CTRL
sed -i -e "s:#define AK_RCTRL:#define AK_LCTRL 0x63\n#define AK_RCTRL:" src/include/keyboard.h
```

Also check your ~/.uaerc - I think the relevant line is:
```
joyport0=kbd2
```

---

