---
title: "Permanent screen rotation"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by blazej on 2007-11-02
Hi,

My monitor is rotated 90 degrees to the right.  So in Ubuntu I go to System > Preferences > Screen Resolution and change the rotation, and it works like a charm.  The problem is that this setting is not remembered, so every time I power my computer up I have to navigate to the dialog box and change the setting.

Is there a way to make Ubuntu permanently remember the screen rotation?

BTW, I'm using 7.10.

Best,
Michal Blazejczyk

---

### Post by gsiliceo on 2007-11-02
Try in terminal
> xrandr -o right
or
> xrandr -o left
Wichever works add it to system/preferences/sessions

---

