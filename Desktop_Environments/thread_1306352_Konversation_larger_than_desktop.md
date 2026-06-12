---
title: "Konversation larger than desktop"
date: 2009-10-30
forum: Desktop Environments
---

### Post by fusa on 2009-10-30
After upgrading to 9.10 Konversation's window is currently larger than my desktop.  This hides the window boarders, and makes it hard to switch to other open programs and desktops.  I ran into this problem before, and having a terrible time finding where the setting was.  I think KDE stores a programs size and if I closed the progam and edited the file to set the window to a size lesser than my desktop it fixed the problem.  Does anyone have any ideas?  I checked a few files ~/.kde/ with konversation in the filename, but no luck, or I missed the setting.

---

### Post by fusa on 2009-10-30
I found the file, and had overlooked the setting, it is a setting in ~/.kde/share/config/konversationrc  The setting was set to the same size of my desktop, changing it to a lesser value fixed the problem.

---

