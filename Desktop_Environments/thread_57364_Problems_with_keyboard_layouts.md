---
title: "Problems with keyboard layouts"
date: 2005-08-16
forum: Desktop Environments
---

### Post by Mataanin on 2005-08-16
Hello,

I have problems with switching between Keyboard Layouts then there are 3 of them.
I can do it by clicking on "Keyboard Indicator" on gnome-panel, however it wont work properly with alt+shift (as it is in xorg, and gconf) or any other combination (I tried some). 

If it not the first (as in sequence 'us,lt,ru') language it wont switch, ant if it is second or third, it will switch till it reaches us, and stops.

the output of `xprop -root | grep XKB'

_XKB_RULES_NAMES_BACKUP(STRING) = "xorg", "pc105", "us,lt,ru", ",winkeys,", "grp:alt_shift_toggle"
_XKB_RULES_NAMES(STRING) = "xorg", "pc105", "us,lt,ru", ",,", "grp:alt_shift_toggle"

Everything works properly while there are only two keyboad layouts.

Does anybody have any idea?

---

