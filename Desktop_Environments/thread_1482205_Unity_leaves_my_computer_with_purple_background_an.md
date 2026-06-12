---
title: "Unity leaves my computer with purple background and large X for mouse cursor"
date: 2010-05-13
forum: Desktop Environments
---

### Post by Jeff Anthony on 2010-05-13
I added the unity ppa and installed unity to check it out thinking I could just switch back with ```
dpkg-reconfigure gdm
```

Unity left me with just the purple familiar backdrop and a large black X as the mouse cursor. In running the above statement I'm left with the background and cursor only.

Does anyone have a pointer as to how to get unity working and/or how to get back to gnome?

Thank you.

---

### Post by Jeff Anthony on 2010-05-13
I just did

```
sudo apt-get remove unity
sudo apt-get autoremove
```

to get back into gdm successfully.

I still would love to check out unity.

---

