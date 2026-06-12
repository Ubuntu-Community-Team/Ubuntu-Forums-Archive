---
title: "Accidentally removed Window Manager from sessions"
date: 2009-03-16
forum: General Help
---

### Post by LondoMollari on 2009-03-16
Hi.

this is embarrasing... :oops: I was trying to set up emerald theme manager when I accidentally removed the Window Manager entry in system -> preferences -> sessions. This basically means that the borders around all the windows are gone, and I only have one desktop. I tried to restore it by making a new entry with the same name and with the code gtk-window-decorator (or something like that, i'm on another computer right now)... anyone who would be kind enough to tell me how I restore that entry to the original state? I've tried a couple of solutions I've come across on this forum, but they don't seem to relate to this problem...

thx. :-)

---

### Post by geirha on 2009-03-16
remove or rename ~/.config/autostart/, and System -> Preferences -> Sessions will be reset to default.
```
mv -v ~/.config/autostart{,.old}
```

---

