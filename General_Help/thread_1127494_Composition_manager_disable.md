---
title: "Composition manager disable"
date: 2009-04-16
forum: General Help
---

### Post by crhis on 2009-04-16
I tried installing gnome do and awn. When I try to install a theme for gnome, I get the error "your display is not properly configured for theme and animation support. To use these features, you must enable compositing". I searched all over and could not find an answer. I went into gconfig editor and then metacity->general, and checked off compositing manager, but it did not work. Is there an option for compiz maybe? Awn does not work either, presumably for the same reason

---

### Post by Tim Sharitt on 2009-04-16
Your video card driver may not support compositing. Open a terminal and enter
```
compiz --replace &
```

to see if it gives any errors.

---

### Post by GBCG on 2009-05-03
Ubuntu is still new to me... is this an error?

Input: compiz --replace &

Output:
[1] 5752
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

The rest is something like "Warning: " " found in configuration database is not a valid keybinding to the command "switch panels"

(I just won't post the rest of the output because it's all in portuguese)

---

### Post by Richard9795 on 2009-05-03
try putting this in: SKIP_CHECKS=yes compiz --replace. if no effects, then your graphics card may not be capable.

---

### Post by GBCG on 2009-05-05
Tried that and the only thing I get is a white blank screen... guess my card is just some piece of s*** then... :(

---

