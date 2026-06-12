---
title: "I've lost my window manager!"
date: 2009-11-08
forum: Desktop Environments
---

### Post by AussieGuy on 2009-11-08
I downloaded and installed enlightenment to use as a window manager within gnome, but when I logged out and in again - no matter what option I choose - I get a gnome session but with no window manager running!

What's going on, and how do I start a window manager?

I even installed kde (from synaptic), but now when I attempt to login, KDE is not listed as a possible session.

Any help would be most gratefully received!

Thanks,
-A.

---

### Post by John Bean on 2009-11-08
Have you tried going to System->Preferences->Appearance and checking the "None" button on the "Visual effects" tab? This should make Metacity the default window manager and you can take it from there.

Edit: meant to add that you can run a wm (metacity in this case) from a terminal with something like```
metacity --replace &
```

---

### Post by AussieGuy on 2009-11-08
Thank you very much!- that's most helpful.

-A.

---

