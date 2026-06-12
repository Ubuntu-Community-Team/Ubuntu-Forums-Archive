---
title: "When I quit, my applications and panels disappear but then it hangs"
date: 2008-07-30
forum: Desktop Environments
---

### Post by detrate on 2008-07-30
When I go to log out, shutdown or restart, my applications and panels disappear but then it hangs with but a desktop and icons.  I'm able to function with my trusty terminal keybind and **gnome-session --failsafe** but I'm stuck inside this (corrupt?) session.

---

### Post by Ataris on 2008-07-30
I have this problem every once in a while. Honestly I think there's no way to fix it unless you reinstall the OS, and that would cause more problems for you, no doubt. I think it's just Linux, and you have to live with it.

Even so, do you have the latest drivers?

---

### Post by detrate on 2008-07-30
Yes, most likely the culprit... unless it was the apparent memory overflow I had.  All of a sudden gnome flickered and I lost my bookmarks right before I noticed the other problem, so I obviously think they are related.

---

### Post by detrate on 2008-07-31
Thanks to a hot tip from a cool friend I was able to rectify this situation by removing my '**./gnome2/session**' file, then **sudo shutdown -r now**.  Did a reboot after coming back successfully just to make sure and all systems are go :).

---

