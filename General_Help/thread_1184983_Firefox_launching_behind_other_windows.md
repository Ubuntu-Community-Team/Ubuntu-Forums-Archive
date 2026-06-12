---
title: "Firefox launching behind other windows"
date: 2009-06-11
forum: General Help
---

### Post by willthebold on 2009-06-11
Hey all,
The problem I'm having is that when I launch Firefox, if there's any other window open (Pidgin, Terminal etc.) it launches behind them. Is there a preference somewhere to tell it to launch on top all the time? Or maybe compiz has some kind of customized thing to tell it how to launch. Ideas?

Thanks,
-Will

---

### Post by lovinglinux on 2009-06-11
Use the compiz "Window Rules" plugin to select which windows should be always on top. It also provides several options like preventing a window from being minimized and so on.

---

### Post by colau on 2009-06-11
> **willthebold said:**
> Hey all,
The problem I'm having is that when I launch Firefox, if there's any other window open (Pidgin, Terminal etc.) it launches behind them. Is there a preference somewhere to tell it to launch on top all the time? Or maybe compiz has some kind of customized thing to tell it how to launch. Ideas?

Thanks,
-Will
Do you find any option from right clicking the bottom  tab of firefox?
```

sudo aptitude install compizconfig-settings-manager

```

---

### Post by willthebold on 2009-06-12
Thanks for the replies, but that's not quite what I'm looking for. It used to work, and now I'm trying to figure out what changed. I don't want firefox to always be on top, but it should default to being on top when I first open it. Other things do this right, like F-spot, but not firefox. Chrome seems to act the same way. If there's something already open, it launches behind it. It's not a huge deal, but it's kind of annoying, and it never used to do that. Any ideas about what might be causing it? I guess I could maybe try turning off Compiz and seeing if the behavior changes.

-Will

Update- I just disabled window effects, and the behavior went away. I guess it's something to do with desktop effects. Maybe I'll start digging through Compiz and disabling things one at a time to see what the cause is.

---

