---
title: "undo blacklist fix"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by gerfuls on 2007-10-20
i tried the blacklist fix that Amaranth posted. Now i can't log in at all. If i try to login everything comes up and then it boots me out to the login screen again. I can get into the Failsafe Terminal but that is it! the command the Amaranth suggested was:
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
``` how can i undo this in the terminal?

---

### Post by FuturePilot on 2007-10-20
```
nano -w /home/USER/.config/compiz/compiz-manager
```
Look for SKIP_CHECKS=yes and delete it. Press Ctrl+X then, Y to save, and Enter to write the changes.

---

### Post by gerfuls on 2007-10-20
thank you!!!

---

### Post by FuturePilot on 2007-10-20
No problem.:)

---

