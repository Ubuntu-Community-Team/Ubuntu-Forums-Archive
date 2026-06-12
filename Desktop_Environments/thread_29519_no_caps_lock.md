---
title: "no caps lock"
date: 2005-04-24
forum: Desktop Environments
---

### Post by IdoMcFly on 2005-04-24
My caps lock just does nothing.
```

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "keyboard"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr-latin9"
EndSection

```

until i do this in terminal 
```
setxkbmap -rules xorg -model pc105 -layout fr-latin9 -variant basic
```

any idea ?

---

### Post by IdoMcFly on 2005-04-24
forget it... it was because I add dvorak_fr in the gnome keyboard configuration. Having it present makes my caps lock key acting weird.. I'll contact the dvorak_fr creator.

---

