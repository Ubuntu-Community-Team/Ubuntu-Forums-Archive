---
title: "[SOLVED] sometimes desktop not loaded after login"
date: 2008-08-30
forum: Desktop Environments
---

### Post by MasterSander on 2008-08-30
Sometimes ubuntu doesn't load my desktop (my icons to hard drives etc). I also run awn and that doesn't show anymore either, unless I minimize everything to desktop. If I right click on my desktop, nothing happens. Anyone got a solution or has the same problem?

---

### Post by sayakb on 2008-08-30
Goto System->Preferences->Sessions and add **nautilus** to it.

---

### Post by Keith Hedger on 2008-08-30
I have a similar problem every so often my desktop wont load (but awn will) and I have to open a console and run ```
killall nautilus
``` then nautilus runs ok this only started after an upgrade to Hardy 64Bit

---

