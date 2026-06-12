---
title: "Change resoution from another user"
date: 2019-11-16
forum: Desktop Environments
---

### Post by ragge1234 on 2019-11-16
After restart the resolution of my normal user in ubuntu was abysmally big. I couldnt even see more than one line of text if i opened terminal. After booting into recovery mode and making a new user to log into, it works fine. Now my question is.Is it possible to change the res of my old user through my new user?

---

### Post by CatKiller on 2019-11-16
The resolution settings for when you're in a desktop environment are generally stored in ~/.config/monitors.xml.

You can use sudo and su to run commands as any other user, not just root, depending on security policy. An alternative would be doing it from recovery mode or the live environment.

Deleting that file for the problematic user or overwriting it with the one from the other user will change the resolution. 

Of course it might not be an incorrect resolution: you might have accidentally triggered one of the accessibility zoom features.

---

