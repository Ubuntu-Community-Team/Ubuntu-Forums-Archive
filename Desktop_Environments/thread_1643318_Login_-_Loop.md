---
title: "Login - Loop"
date: 2010-12-11
forum: Desktop Environments
---

### Post by Piro24 on 2010-12-11
Hello all.

I was playing with my desktop settings (I think in Themes, but also messing with icons/etc) in the XFCE settings manager, and after selecting a certain one, X seemed to crash. After a reboot, all seemed to be fine up to the login window.

I Click on my username, and type in my password, at which point, everything is going fine. However, instead of going onto my desktop, it kicks me back onto the login window.

I'm typing this by getting into recovery mode, booting into a root shell, and starting x from there. How can I fix this? 

I think resetting all the settings back to default should do it, but how can I achieve this? I've looked around online, and there doesn't seem to be any immediate fix.

Thanks!

---

### Post by Piro24 on 2010-12-11
Shameless bump.

Any suggestions are welcome guys.

---

### Post by Piro24 on 2010-12-12
Alright, so I managed a "fix", but this is certainly not a good one.

I basically gave up on trying to find a way to manually reset the current theme, which was, indeed what was causing the whole problem(I was able to recreate this). My solution was to simply create a new user, migrate everything from my old account to the new one, and nuke the other one.

However, this is obviously a major issue.

---

### Post by Atrus6 on 2011-01-07
I ran into the same problem while going through the window themes. All of the sudden X crashed. I restarted, and got stuck in the same login loop as you.

---

