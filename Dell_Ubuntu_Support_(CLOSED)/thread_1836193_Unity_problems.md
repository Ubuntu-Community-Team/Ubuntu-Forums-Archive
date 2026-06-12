---
title: "Unity problems"
date: 2011-08-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rbwilley on 2011-08-30
I just installed Ubuntu 11.4 on my Dell Inspiron Laptop, when I boot into Ubuntu I get the login screen, when I log in I get a blank splash screen and then nothing else, no toolsbars, no nothing.  I tried to remove compiz like I had read on a forum and when I did that and logged in I got the same thing, only this time I get a notification saying there are available internet connections, but still no toolbars, buttons, icons, nothing.  I have a Mobility Radeon HD 4200 video card.  Anyone have any ideas?

Oh, Ubuntu classic seems to run just fine.

---

### Post by rectec794613 on 2011-08-30
Try starting in recovery mode from the boot menu, select "Drop to root shell prompt", then type this in:
```
unity --reset
```

---

### Post by mikewhatever on 2011-08-30
At the login screen, under the session menu, try selecting the option with 'No desktop effects'.

---

