---
title: "[SOLVED] Window manager features disabled"
date: 2008-01-04
forum: Desktop Environments
---

### Post by Saghaulor on 2008-01-04
I have been messing around installing and testing various window managers.
I installed Compiz and then opened terminal and typed Copmiz.
Suddendly, things changed and I'm not sure how, except that the top window features, such as maximize, minimize, et cetera were missing. Also, the window seemed to be tacked to the top left corner and non movable.. Well I restarted, and completely removed Compiz and all it's cronies, and the problem is still lingering. Also I've noticed that I can no longer cut/copy and paste.

Any ideas on how to revert my setting back to the old way? I don' t want to have to format and reinstall, but if I must, then I will as this is highly annoying.

I thank you in advance for you assistance.

---

### Post by PeterJS on 2008-01-04
Assuming you're runnging gnome, press alt+f2 to open the run dialog, and run:
```

metacity

```
Metacity is the default window manager for gnome, sometimes when compiz doesn't work it boots the other WM but doesn't load itself, and then when the session manager restarts it doesn't know to load a window manager as it there wasn't one when it shut down.

---

### Post by Saghaulor on 2008-01-04
I'm using Xubuntu with Xfce, does that matter?

---

### Post by PeterJS on 2008-01-04
It might work if you have gnome installed but, the default wm for Xfce is xfwm4, so you might try that instead.

---

### Post by Saghaulor on 2008-01-04
Thank you Peter!

---

