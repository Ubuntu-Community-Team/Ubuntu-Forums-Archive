---
title: "Configure Cinnamon lock screen login box"
date: 2016-08-10
forum: Desktop Environments
---

### Post by CatKiller on 2016-08-10
The login box to unlock the locked screen is horrible. So flat and completely different to the style of the default lock screen and the default login screen. Plus it sometimes comes up twice, with one the wrong size, for some reason. I haven't found a way to customise this part. I'm running Cinnamon on Ubuntu 16.04.

Please note, I don't want to change the login screen, or the lock screen. Those are both fine. I just want to change the actual box that comes up when you want to unlock the screen.

Thanks for any pointers.

---

### Post by CatKiller on 2016-08-11
I suspect that the appearance of that login box may be affected by the GTK theme that's selected. I'll investigate on that front when I get an opportunity.

If someone could confirm that that's the case, and indicate how that portion is configured, that would be really helpful.

---

### Post by CatKiller on 2016-08-13
OK, it seems like that unlock window is controlled by the GTK theme, and the reason it looks so bad is because it get counted as a dialogue box and has no border for some reason. I've tried looking round for a better GTK theme, but it seems like everyone has become obsessed with making everything look flat and ugly.

---

