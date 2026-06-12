---
title: "Disable Windows Key"
date: 2005-09-03
forum: Desktop Environments
---

### Post by steve0921 on 2005-09-03
I have a WIndows key on my laptop keyboard (not easily replaced) that is frequntly stuck, even without being pressed.

In windows I could edit the registry to permanently filter out the windows key for all users. Is there something similar I can do in Ubuntu? I've looked at the keyboard layout options for the alt and win key, but I haven't found an option to have it disabled.

---

### Post by kahping on 2005-09-03
is it even enabled in the first place? have you tried?

far as i know, the Windows Key has no function in Ubuntu by default.

kahping

---

### Post by steve0921 on 2005-09-03
It's true that the key appears to do nothing, but the fact that it is pressed seems to have an effect. This is what I need to disable.

Keyboard shortcuts like Alt-Tab and Alt-F4 don't work sometimes nor can I type in firefox. When I press the key a few times though (to unstick it), all funcitonality is restored.

Would using a keyboard layout without a windows key work? If so, what layout should I try?

---

### Post by steve0921 on 2005-11-08
I have tried using the 101 key models of keyboard available in ubuntu (which from counting on my desktop I believe do not have windows keys, nor the menu key), but have had no luck.
It also looks like the keyboard preferences are set by default to have win mapped to super, but switching this mapping seems not to have helped either.

I might be able to fix the keyboard shortcut issue simply by including the super key (set super+alt+F4 to close window so that pressing alt+F4 would have that effect), but I would still be unable to type in firefox.

I've put up with this problem for a while, but it has gotten worse and is now entirely unbearable.

Does anybody have any idea how I can make my computer ignore the key completely? I'm willing to try anything to avoid giving up on ubuntu!

-Steve

---

### Post by ashmew2 on 2008-02-14
type in the terminal

xmodmap -e "keycode 115 = 0x0000"

to permanently disable the Win Key.

---

