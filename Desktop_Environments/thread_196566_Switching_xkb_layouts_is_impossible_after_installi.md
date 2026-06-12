---
title: "Switching xkb layouts is impossible after installing xgl/compiz on kde"
date: 2006-06-14
forum: Desktop Environments
---

### Post by angem1 on 2006-06-14
Hi everyone!

I installed XGL/Compiz on KDE, and everything works great except of 
switching keyboard layouts on kde:
setxkbmap always resturns:

```
Couldn't interpret _XKB_RULES_NAMES property
Use defaults: rules - 'xorg' model - 'pc101' layout - 'us'
Segmentation fault
```

The Kxkb icon always shows "err"....


Some info that might help you helping me :p  :
* server command in kdmrc: 
```
ServerCmd=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo +kb
```
* kb options in xorg:```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection
```
layouts configuration in kxkb: 
```
* setxkbmap -model pc104 -layout us
* setxkbmap -model pc104 -layout us,il
```
* When I used compiz on gnome, I had no such problems.

---

### Post by angem1 on 2006-06-14
I succeeded solving the problem by running gnome-keyboard-properties,
and then:
killall kxkb
kxkb

But it is very annoying to do this process every boot....

Does someone have any idea of a more elegant solution?

---

### Post by angem1 on 2006-06-16
[just for a case that someone else had the same problem: ]

I solved the problem by adding

gnome-settings-daemon &

to the script that runs compiz, and then I could switch keyboard layouts in kde. 
- not the best solution, but still a comfortable one.

---

