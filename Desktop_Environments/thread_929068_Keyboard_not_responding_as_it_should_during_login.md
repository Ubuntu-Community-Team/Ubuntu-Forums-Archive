---
title: "Keyboard not responding as it should during login"
date: 2008-09-24
forum: Desktop Environments
---

### Post by Kieeps on 2008-09-24
Ok so this is the thing...
I have a big problem here when i try to log in to ubuntu, the keyboard won't let me write anything. no letters turn up when i hit a key while "enter" works, the number 5 works and the "+" key works along with the entire numpad, i tryed going in with a LiveCD and that made the entire kayboard work again, what i wanna know now is where ,exept for the xorg.cong and console-setup, the layout is deffined, i don't know WHY this happend, the only thing i realy changed was the login screen to the one where the username is pickable with the mouse.

Hardy (latest atm)
Gnome

/etc/X11/Xorg.conf
```

Section "InputDevice"
        Identifier       "Generic Keyboard"
        Driver           "kbd"
        Option           "CoreKeyboard"
        Option           "xkbRules"      "xorg"
        Option           "xkbModel"      "pc105"
        Option           "xkbLayout"     "se"
EndSection

```

/etc/default/concsole-default
```

XKBMODEL="pc105"
XKBLAYOUT="se"
XKBVARIANT=""
XKBOPTIONS=""

```

PS. If anything from the configs are spelled wrong it's probably just 'cus i wrote it by hand :P

Any ideas? I hate that this error makes me boot windows all the time :(

---

### Post by Kieeps on 2008-09-26
is there a way to make grub load ubuntu without gnome? so i'll just end up with the terminal, seems like it has something to do with the login screen i changed to. i'f i can get in to the terminal i could go on from there and try to change it manualy. 
Guess this would be doable with a LiveCD....but i kinda left it at my friends place yesterday :/

---

