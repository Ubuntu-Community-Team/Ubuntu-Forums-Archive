---
title: "Xubuntu's mouse-sized but greatly annoying flaw..."
date: 2011-05-07
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-05-07
It seems that users have been asking for an "Always on Top" button for over half a decade. Seems like it would be a silly, easy thing to do. There's not even a keyboard shortcut for it.

Has anyone found a workaround?

---

### Post by Toz on 2011-05-07
1. sudo apt-get install wmctrl

2. Goto "Application Shortcuts" in Keyboard Settings.

3. Create a new shortcut:
     Command = wmctrl -r :ACTIVE: -b toggle,above
     Shortcut = whatever key combination you want

---

### Post by neu5eeCh on 2011-05-07
> **Toz said:**
> 1. sudo apt-get install wmctrl

2. Goto "Application Shortcuts" in Keyboard Settings.

3. Create a new shortcut:
     Command = wmctrl -r :ACTIVE: -b toggle,above
     Shortcut = whatever key combination you want

:shock: You. Are. A. Linux. Deity.

---

