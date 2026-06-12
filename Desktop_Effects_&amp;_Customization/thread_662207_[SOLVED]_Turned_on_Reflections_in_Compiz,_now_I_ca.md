---
title: "[SOLVED] Turned on Reflections in Compiz, now I can't login to my computer without it"
date: 2008-01-08
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2008-01-08
A friend of mine was messing around with his Advanced Desktop Effects Settings and did something that his video card doesn't want to do.  It locked his computer up.  He then killed the power, restart, and because the account is set to auto-login, it tries, but freezes with the tan background.

What's the best way to fix this?  Is there a conf file I could edit to disable compiz.  Or perhaps have it revert to "Normal" mode, or something like that.  Perhaps remove Compiz and switch to Metacity?  Perhaps create a new user account?

---

### Post by overdrank on 2008-01-08
> **diablo75 said:**
> A friend of mine was messing around with his Advanced Desktop Effects Settings and did something that his video card doesn't want to do.  It locked his computer up.  He then killed the power, restart, and because the account is set to auto-login, it tries, but freezes with the tan background.

What's the best way to fix this?  Is there a conf file I could edit to disable compiz.  Or perhaps have it revert to "Normal" mode, or something like that.  Perhaps remove Compiz and switch to Metacity?  Perhaps create a new user account?

HI and you can try and boot into recovery mode from the grub and use the command startx  then disable the effect in compiz.

---

### Post by diablo75 on 2008-01-10
I solved the problem on my own with this:

I hit escape in Grub and went to the recovery terminal.  I then browsed to the users home folder and entered the following:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

This resets gnome to its defaults.  I was able to login no problem, after typing "exit" at the terminal to shut down, and then restart the PC. I could then re-enable compiz with no problem.

---

