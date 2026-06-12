---
title: "Win/menu-key as an extra alt-gr?"
date: 2009-01-26
forum: Desktop Environments
---

### Post by sjl on 2009-01-26
Title says it all, actually.

I'd like to turn the left win-key on my Acer laptop into a second alt-gr and do the same to right menu-key too. In this particular case the key I'm referring as win-key is situated between left control and left alt keys, menu-key on the other hand is situated between alt-gr and right control keys.

I've been playing with keyboard settings found under System -> Administration -> Keyboard without much of a success. Maybe someone here has already accomplished what I'm still trying to figure out?

---

### Post by Boludinux on 2009-08-30
bump

I also would like to know this!

---

### Post by nathan726 on 2009-11-15
You can make any key do anything you want by using the xmodmap command.
For example, if I wanted to set the menu key to be an alt-gr key instead, I would use:```
xmodmap -e 'keycode 135 = ISO_Level3_Shift'
```

All you need to know is the keycode of the key and the value you wish to assign to it.
The "xev" command can help you find such info.

---

### Post by santq on 2010-04-14
Thank you, this should be sticky or something. Also if you want to set auto repeat on/of, use *xset r [keycode]* or *xset -r [keycode]* correspondingly.

---

