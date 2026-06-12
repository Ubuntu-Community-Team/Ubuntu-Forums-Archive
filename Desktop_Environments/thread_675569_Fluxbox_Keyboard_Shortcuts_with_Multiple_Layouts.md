---
title: "Fluxbox Keyboard Shortcuts with Multiple Layouts"
date: 2008-01-22
forum: Desktop Environments
---

### Post by mbsullivan on 2008-01-22
Hi All,

I have a question for the Fluxbox users...my Fluxbox keyboard shortcuts are based on ease-of-use in QWERTY.   When I switch to other keyboard layouts on my laptop, by default the keys move to their modified positions, which makes my shortcuts less efficient.

Is there any way to make Fluxbox hotkeys operate NOT using a key name (such as 'a'), but rather by the keycode for a key (such as 38, for the 'a' key)?  Thus, if Alt+s does something in QWERTY, the same key (though it is now a different letter) would perform the same key action in Dvorak.

Is this possible? If not, can you think of any way to easily migrate my keys (only other thing I can think of is a keymodes hack).

Thanks!
Mike

---

### Post by cknight on 2008-01-23
Keycodes can be used in place of the key literal.  Type 'xev' on the command line.  Hit the key you are interested in and look for this line in the output:
```
state 0x10, keycode 38 (keysym 0x61, a), same_screen YES,
```

Thus, you should be able to use the keycode 38 in place of the literal 'a'.  

So, 
```
Mod4 a :rootMenu
```
is the same as
```
Mod4 38 :rootMenu
```

Good luck!

---

### Post by mbsullivan on 2008-01-23
Hah, thanks! I made this post because that didn't work for me, but I must have somehow messed it up. 

That solves my problem.
Mike

---

