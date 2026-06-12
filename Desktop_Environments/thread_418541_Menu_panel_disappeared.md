---
title: "Menu panel disappeared"
date: 2007-04-22
forum: Desktop Environments
---

### Post by SRTS on 2007-04-22
Help, Im using KUbuntu 7, installed wine and played WoW, when the game crashed and I did a hard reset. Also I changed my monitor from "plug and play" to "hp 2035".
After rebooting I didnt get any kdm, but just black screen. i found out I had to revert monitor settings to "plug and play" (although my monitor IS a hp 2035...) and it worked again.

But now in KDE my menu panel with the pager, apps, tray, and K-menu has completely disappeared. help!

thanks in advance


edit: i just tried killall -9 kicker && kicker & and saw my task bar appear again for a split second, then it immediately vanished again :(

---

### Post by SRTS on 2007-04-22
Ok after an annoying trial-by-deletion process I finally discovered that all I had to do was to delete two ~/.kde/share/config/kicker* files.

Stuff like this should not randomly happen in a modern OS that is out of beta though, it appears to be a "common" problem.

---

### Post by venik212 on 2007-05-02
"Stuff like this should not randomly happen in a modern OS that is out of beta though, it appears to be a "common" problem."

AMEN!

---

