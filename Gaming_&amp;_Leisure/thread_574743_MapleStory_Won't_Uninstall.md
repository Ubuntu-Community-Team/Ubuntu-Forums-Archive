---
title: "MapleStory Won't Uninstall"
date: 2007-10-13
forum: Gaming &amp; Leisure
---

### Post by GoldenChaos on 2007-10-13
Hey there everybody - I've been searching this all over the internet, but haven't found a solution. I recently installed MapleStory with Wine (big mistake), and after noticing GameGuard is indefinitely incompatible with Wine, I chose to uninstall it.

Seems that uninstalling MapleStory in Wine means reinstalling it. I've even deleted the directory and all MapleStory-related files, then tried "uninstalling" it from Wine's menu, hoping it would tell me that the setup.exe could not be found and remove it from the uninstall menu. Yet somehow, it found setup.exe and brought up the dialog - from a file I was sure I deleted!

So, I did the uninstall that way, and lo and behold - all the MapleStory files came back!

I desperately want this pile of trash removed. Completely and utterly removed - from Wine, from the menus, from my HDD. Help?

---

### Post by TidusBlade on 2007-10-13
I really got no solution, but In this case I would try getting on root account and trying a few things, or maybe reinstalling WINE if it's not too much of a problem.

---

### Post by GoldenChaos on 2007-10-14
I don't quite understand what I could do as root, but I don't want to uninstall Wine - I spent too long getting WoW onto there. ;)

---

### Post by cogadh on 2007-10-14
Are you using Wine's uninstaller interface or directly using the uninstall shortcut the game added when it was installed?

---

### Post by GoldenChaos on 2007-10-14
I tried both, and each gave the same result.

I went and uninstalled Wine, then reinstalled it after deleting the .wine and .xine directories. That did the trick.

Unfortunately, it took forever to install WoW again :/... and no sound, either!

---

### Post by cogadh on 2007-10-14
I've had that happen with Steam before and the only way I could get rid of it (other than wipe out my entire .wine directory) was to manually rip out all of the related registry entries, then delete to program directory.

---

