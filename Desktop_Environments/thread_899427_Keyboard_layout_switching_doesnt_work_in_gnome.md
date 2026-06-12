---
title: "Keyboard layout switching doesnt work in gnome"
date: 2008-08-24
forum: Desktop Environments
---

### Post by Mizipzor on 2008-08-24
I recently decided to switch from kde to gnome. The problem Im having that keeps me from doing that is keyboard layout switching. 

I dont normally run the qwerty layout, but when playing games I quickly switch to it, since the game expects it and its convenient to not have to rebind everything to get the regular wasd movement layout.

In kde I have the kde keyboard tool which sits in tray and nicely let med do that. But in gnome, Ive found no such tool. I did enable an option that lets me switch layout with alt+shift.

But now to the real problem, when pressing alt+shift, the game doesnt recognize the change in layout in gnome. But it does in kde. Although, gnome does know about the change in layout when I type in the games console, but not when Im actually playing.

Whats the cause of this? And whats the best way to fix it?

---

### Post by Mizipzor on 2008-08-25
Ok, now Im on to something. In kde4 and gnome, the keyboard switcher command looks like this:
```
setxkbmap -model pc104 -layout se,se -variant dvorak,
```

Both layouts in one line. But in kde3 (where it works) I actually get one commandline per layout.
```
setxkbmap -model pc104 -layout se -variant dvorak
setxkbmap -model pc104 -layout se -variant basic
```

Note also that in the above example, the "basic" layout isnt even selectable, so I set that to "default". Which seems to make the variant option empty.

I verified this by manually running the two commands above with the keyboard layout switcher disabled. It works as intended! 

So my question now is simple; how do I make the switcher in kde4/gnome work like the one in kde3? I.e. one command per variant, rather than all variants in one command.

---

