---
title: "Steam error in Wine"
date: 2007-08-09
forum: Gaming &amp; Leisure
---

### Post by ninjad on 2007-08-09
I just installed half-life 2 and all the other games that came with the game of the year edition. But when i run steam it just sits saying "Updating Steam...".

After a few minutes the steam window will close and i get this error:

> Steam.exe (main exception): Unable to load library Steam.dll

Thanks

---

### Post by frodon on 2007-08-09
Hum this is an annoying problem.

First look that the partition where is stored your steam directory don't have any problem then try to delete your clientregistry.blob file in your steam directory and restart steam.

---

### Post by splintercellguy on 2007-08-09
What version of Wine are you running? If desired, you may re-do the Steam install by doing rm -rf ~/.wine (if you don't have anything in the Wine folder to keep) and following the instructions in the AppDb: [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

---

### Post by frodon on 2007-08-09
i think he can just delete the steam directory if he want to try your suggestion, "rm -rf ~/.wine" sounds a bit too drastric to me.

---

