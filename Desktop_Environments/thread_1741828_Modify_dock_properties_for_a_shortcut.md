---
title: "Modify dock properties for a shortcut?"
date: 2011-04-28
forum: Desktop Environments
---

### Post by Mainer82 on 2011-04-28
I need to modify the shortcut for etherape to start in root/sudo mode.

Normally I would do this: -- su-to-root -X c /usr/bin/etherape

But I can't go to the properties of a shortcut in that bar/dash/dock in 11.04.

Is this possible?

---

### Post by Copper Bezel on 2011-04-28
Although I'm not using Unity, I *think* you can create a launcher (a .desktop file, a copy of the one from the app you want) and drag and drop it onto the dock. To make it run in root, change the exec line to gksu [executable].

---

### Post by nilarimogard on 2011-04-28
> **Mainer82 said:**
> I need to modify the shortcut for etherape to start in root/sudo mode.

Normally I would do this: -- su-to-root -X c /usr/bin/etherape

But I can't go to the properties of a shortcut in that bar/dash/dock in 11.04.

Is this possible?

Navigate to /usr/share/applications, look for the application shortcut you want to modify and change it to whatever you want...

---

