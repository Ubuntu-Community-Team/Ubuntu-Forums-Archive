---
title: "GNOME hangs on re-login"
date: 2007-02-24
forum: Desktop Environments
---

### Post by Pat.Hat on 2007-02-24
First off, let me say that I recently upgraded from Dapper to Edgy and it worked pretty much flawlessly; I expected issues and was aware of the risks, I'm learning. I'm not the most avid of Ubuntu users, so these forums have proven themselves invaluable, thank you everyone!

Unfortunately, I haven't been able to find an answer for my issue here. Everything with Edgy works smoothly (I'm talking my Nvidia drivers and all) until I try to ctrl+alt+backspace and **re-login**. At this point, I'm able to boot into a 'failsafe terminal', but neither 'GNOME Session' nor 'Failsafe GNOME' will work for me. I'll attempt to login, the startup sound will play, but the splash screen never shows. I am still able to ctrl+alt+backspace and reselect a session.

I've attempted "dbus-launch gnome-session" in the terminal window, and I get the following:

```
SESSION_MANAGER=local/bud-desktop:/tmp/.ICE-unix/6447
```

Immediately after, the system hangs. Ok, so maybe this really isn't a huge issue to anyone but me, but having to reboot everytime I want to login to GNOME really doesn't do it for me ;) . On a side note, the screensaver still comes on, but window manager, gnome-panel, and nautilus never load.

---

### Post by ComplexNumber on 2007-02-24
> until I try to ctrl+alt+backspace and **re-login**
i don't understand why you need to do that.

---

### Post by Pat.Hat on 2007-02-24
Well, perhaps I'm making an incorrect assumption (most likely), but I'm using it so I can switch users (more than one person will use this computer, and I don't want more than one session running) and also to restart GNOME after I've made changes. Logging out using the panel doesn't bring me back to the login screen, I just see "waiting for X server to shut down".

---

### Post by Pat.Hat on 2007-03-04
I don't know what happened, but the problem seems to have disappeared for now. Perhaps it was that last update...

---

