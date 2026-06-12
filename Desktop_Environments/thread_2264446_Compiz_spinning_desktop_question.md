---
title: "Compiz spinning desktop question"
date: 2015-02-07
forum: Desktop Environments
---

### Post by ray field on 2015-02-07
under Compiz, I like using the mousewheel to spin the desktop. sometimes, not all the time, I'd rather not have to move the cursor to an empty spot over the desktop in order to do so -- say by holding down the Alt key while turning the wheel. I don't see anything in CCSM that suggests I could -- or, am I missing something?

---

### Post by mc4man on 2015-02-07
What you're using now is "Desktop-based Viewport Switching" which requires focus on Desktop

You can also set some bindings for rotate itself - in this case see screen. So for rotate right (mouse) have set to shift & button 5, for rotate left (mouse) to shift & button 4 which dupes the same scrollwhell direction I use for Desktop-based... (scroll on desktop switching

---

### Post by ray field on 2015-02-07
big thanks, mc4man!

---

### Post by CantankRus on 2015-02-07
If you prefer to use just the mouse, you can set up a command to
be initiated when left clicking on the right screen edge.
Need to install xdotool and the command to use in ccsm > general > commands is...
```
xdotool key ctrl+alt+Right
```

---

