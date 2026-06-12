---
title: "running gnome panel on xfce (Solved)"
date: 2006-10-29
forum: Desktop Environments
---

### Post by raul on 2006-10-29
i'm a gnome user and decided to give xfce a try. i read that  one could run some gnome stuff on xfce, so i tried running gnome panel (typed `gnome-panel' in the terminal). but now i can't run xfce without the gnome stuff. i already tried killing all gnome processes (nautilus, wallpapoz, gnome volume and power managers, etc) and restarting the session. but they all load up again when i start xfce. i even removed and reinstalled xfce, but i still got the same thing.

any ideas on how i can get back to xfce?

---

### Post by aysiu on 2006-10-30
Try not saving your session when you log out?

---

### Post by raul on 2006-10-30
i tried that but didn't work. also tried killing all the processes and saving the session, but didn't work either. also, just checked my startxfce4 in /usr/bin, but there's nothing there about gnome panel...

---

### Post by aysiu on 2006-10-30
Can you try this?

1. Log out.
2. Control-Alt-F1
3. Log in.
4. ```
mv ~/.config ~/.config.old
```
5. Log out
6. Control-Alt-F7
7. Log in again.

Did it work?

---

### Post by raul on 2006-10-30
it didn't work; still have nautilus and the gnome managers running. on the other hand, it did something: i had costumized the toolbars, and now they're back to their original state.

i don't know if this is relevant, but my gnome startup also got modified somehow, and cannot return it to how it was. maybe i screwed something up when i was trying to fix things, as it happens to many newbies i guess.

---

### Post by raul on 2006-10-30
another bit of info that might be relevant: when i typed `gnome-panel' in the terminal, i got an error message and neither of my two gnome panels actually loaded. at first they were superimposed with the xfce ones, but they disappeared when i exited the terminal.

---

### Post by aysiu on 2006-10-30
Maybe in addition to moving ~/.config, you may also want to do the same for these folder, too:

~/.nautilus
~/.gnome2
~/.gnome
~/.metacity
~/.gconf
~/.gconfd

---

### Post by raul on 2006-10-30
ok, just moved all of them and still get the gnome processes going on. maybe now i should try again killing them and saving the session?

---

### Post by kerry_s on 2006-10-30
Run in terminal

rm -r ~/.cache/sessions

If that don't work delete it manually, it's a hidden file in your home directory. Then ctrl+alt+backspace that should give you a clean xfce4 session.

---

### Post by raul on 2006-10-30
great, thanks, that worked! thanks a lot to you too, aysiu.

---

### Post by aysiu on 2006-10-30
> **raul said:**
> great, thanks, that worked! thanks a lot to you too, aysiu.
Well, none of my suggestions worked, but now you know where all the other config folders live for Gnome and XFCE.

Glad it worked out for you eventually.

---

### Post by kerry_s on 2006-10-30
Great, let us know if you need anything else. I haven't used xfce4 in a while, but i just installed it 2 days ago and i am quickly getting to know it again. ;)

---

