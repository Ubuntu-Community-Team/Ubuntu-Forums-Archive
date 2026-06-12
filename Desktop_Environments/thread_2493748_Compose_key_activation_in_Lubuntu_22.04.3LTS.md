---
title: "Compose key activation in Lubuntu 22.04.3LTS"
date: 2023-12-23
forum: Desktop Environments
---

### Post by goemonburo on 2023-12-23
I've found several walkthroughs on this for** Ubuntu** 22.04LTS, but so far nothing on **Lubuntu**, which has no Settings -> Keyboard -> Options -> Position of Compose Key.  I have looked in the Preferences > LXQt Settings > Keyboard & Mouse, downloaded gnome-tweaks, checked the Openbox settings, and I have tried what used to work (though it was a pain to do it each boot), by typing ```
setxkbmap -option compose:ralt
```

In 22.04LTS I haven't gotten anywhere.  If anyone knows the secret, thank you in advance for sharing!

---

### Post by goemonburo on 2023-12-23
Okay, so it appears ONE of those things I did above actually worked, what confused me is that 22.04 apparently no longer displays any "you're in Compose key mode" character to show it's active.  Thus, I was hitting r-alt and nothing was happening and I assumed it wasn't working.  However, it just seems to silently start working, and when I typed n and ~ it turned into ñ as I'd hoped.  So that's essentially solved.

---

