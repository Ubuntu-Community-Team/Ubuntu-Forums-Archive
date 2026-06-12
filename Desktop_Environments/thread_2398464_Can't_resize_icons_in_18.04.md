---
title: "Can't resize icons in 18.04"
date: 2018-08-12
forum: Desktop Environments
---

### Post by steve169 on 2018-08-12
I just upgraded Ubuntu to 18.04 and now have these desktop icon problems (see attachment):

A. All my drives are mounted automatically when I boot up, but I don't want their icons on the desktop. How can I prevent this?

B. I'd rather that the trash icon be in the launch bar on the left side. If this can't be done, I'd like it off the desktop entirely.

C. Previously, the icons across the bottom were the same size as the task bar's on the left side. Now when I click "Resize icon..." I'm allowed to enlarge the icons but not shrink them.

Also, when I insert a USB flash drive, an icon appears on the desktop. I'd prefer to have it appear in the launch bar on the left side.

---

### Post by Frogs Hair on 2018-08-12
A/B. Mounted volumes can be disabled in the Tweak Tool under desktop along with Trash. Trash would then be accessed in the file manager and not on the left panel. Keep show icons activated though.```
 sudo apt install gnome-tweaks
```

---

### Post by steve169 on 2018-08-12
Dear Frogs Hair: Bingo! Very simple, but I'd never have figured it out myself. Many thanks.

---

