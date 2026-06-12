---
title: "upgrade, restart =&gt; Couldn't load XKB keymap, falling back to pre-XKB keymap"
date: 2005-07-30
forum: Desktop Environments
---

### Post by X_FISH on 2005-07-30
After a couple of days I ran an update. Turned off the computer last night, turned it on and now i dont have the possibility to enter [ or ] or other keys using "AltGr". 

Don't think "but they are there" - I clicked on the "Size" dropdown and deleted the not needed stuff. :)

```
cat /var/log/Xorg.* | grep keymap
Couldn't compile keymap file
(EE) Couldn't load XKB keymap, falling back to pre-XKB keymap
Couldn't compile keymap file
Couldn't compile keymap file
(EE) Couldn't load XKB keymap, falling back to pre-XKB keymap
Couldn't compile keymap file
Couldn't compile keymap file
(EE) Couldn't load XKB keymap, falling back to pre-XKB keymap
```

Found a soulution:

```
xmodmap -e "keycode 113 = Mode_switch"  #AltGr als Mode_switch
xmodmap -e "keycode 16 = 7 slash braceleft" #geschweifte Klammer auf
xmodmap -e "keycode 17 = 8 parenleft bracketleft" #eckige Klammer auf
xmodmap -e "keycode 18 = 9 parenright bracketright" #eckige Klammer zu
xmodmap -e "keycode 19 = 0 equal braceright" #geschweifte Klammer zu
xmodmap -e "keycode 20 = ssharp question backslash" #Backslash
xmodmap -e "keycode 24 = q Q at" #@
xmodmap -e "keycode 26 = e E currency" #Euro
xmodmap -e "keycode 35 = plus asterisk asciitilde" #Tilde
xmodmap -e "keycode 54 = c C cent" #¢
xmodmap -e "keycode 94 = less greater bar" #bar
```

But: xmodmap is not installed. Should be a part of xbase-clients, but that's the newest version and I don't have any xmodmap on my machine.

Any idea for a working solution?

Regards, Martin

---

### Post by stoffe on 2005-08-03
Installing xkbutils seems to have solved it for me.

---

