---
title: "Mapping Caps Lock for Shortcuts"
date: 2007-08-21
forum: Desktop Environments
---

### Post by Exploid on 2007-08-21
I'd like to be able to make shortcuts in Ubuntu(Gnome) with the Caps Lock key. Something like <Caps_Lock>r or <Caps_Lock>t because I don't like to make shortcuts that could be used by a program.
I'm sorry if I didn't post in the right section but I think some keyboard stuff has something to do with gnome so I'm trying.

---

### Post by Chymera on 2007-08-21
as far as i know that doesn't work. its kind of like making shortcut keys with the reset button on your computer. caps has a function on its own, and will fulfill that function when being hit, rather than list itself in the shortcut string.

however if your concern is not to override shortcut keys within apps use super+alt or super+ctrl combinations, since those are used only outside of apps, and thus you will be prompted by the system if you override anything.

---

### Post by kuja on 2007-08-21
Not true chymera. It's possible to make it an extra meta key (I know how to do that in kde at least). What I've done with my laptop is make my caps_lock an additional control key (it's easier to reach, so that's kind of handy). If you want exploid I could dig up how I did it. It's really not all that hard.

---

### Post by Exploid on 2007-08-22
Thanks Kuja, but I don't want to overwrite applications shortcut so using ctrl would not really be useful. I would still need to use shift and alt. My goal was to make two key shortcuts with caps lock.

---

### Post by kuja on 2007-08-22
Like I said, it could also become a meta key. It involves using xmodmap.

The procedure would be the same as in [this post](http://ubuntuforums.org/showthread.php?t=490402&highlight=xev), but you'll want to use Meta_L instead of Shift_L.

---

### Post by Exploid on 2007-08-22
Allright, I looked up the post and this gave me an Idea. In the keyboard shortcut screen I tried to create a shortcut with my right alt and a letter and it does Mod5 compared to my left Alt which does Alt. I'd like to switch my caps lock and right alt. I prefer using caps lock than my right alt for comfort.

here you remove Shift = Shift_L
I'd like to remove my right alt which is Mod5 and I don't know how.

```
xmodmap -e "remove Lock = Caps_Lock"
xmodmap -e "remove Shift = Shift_L"
xmodmap -e "keycode thecapslockkeycodenumber = Shift_L"
xmodmap -e "keycode theshiftlkeycodenumber = Caps_Lock"
xmodmap -e "add Lock = Caps_Lock"
xmodmap -e "add Shift = Shift_L"
```

---

