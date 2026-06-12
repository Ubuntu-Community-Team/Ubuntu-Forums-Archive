---
title: "how do I turn off the screen dimming when asked for my password?"
date: 2006-06-12
forum: Desktop Environments
---

### Post by jnoreiko on 2006-06-12
When GNOME asks me for the admin password (eg running synaptic), the screen goes dark around the dialog box. It's a nice effect, but it **doesn't work properly** -- when it undims afterwards, there's a really horrible flash effect that's unpleasant.

How can I turn this off?

(And anyway, does the password dialog really need to block all my other apps?)

---

### Post by traveller.ct on 2006-06-12
If you go into gconf-editor, you can find an option under /apps/gksu called "disable-grab". Ticking this will disable the screen dimming, but BEWARE! According to the description, ticking this option > will make it possible for other X applications to listen to keyboard input events, thus making it not possible to shield from malicious applications which may be running.

---

### Post by jnoreiko on 2006-06-12
Thanks :)

Another problem that causes actually is that you can't return focus to the dialog box once you've moved from it.

---

### Post by traveller.ct on 2006-06-12
The gksu dialogue box doesn't have an item in the window list. I suppose the only way to retrieve it if it's lost under other windows is to minimise everyone of those obstructing windows.

---

