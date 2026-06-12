---
title: "Fixed Half Life 1"
date: 2013-02-08
forum: Gaming &amp; Leisure
---

### Post by gerowen on 2013-02-08
So the Half Life 1 forums are ablaze with Linux and Mac users that have no more save files after the latest update.  The problem is an easy fix, for some reason they just changed where the saves go and you have to move them to where it wants them to be.  I've written a small script to automate the process and attached it to this topic.  If you're a Linux user and run Steam and have had these issues with Half Life 1, give this a shot.  No need to run it as root or anything crazy, and it even backs up your game folder to your Desktop in case it doesn't work.

---

### Post by Bölvaður on 2013-02-08
What is the new path to the save directory?
What was the old path?

---

### Post by gerowen on 2013-02-08
The saves are currrently in ~/.steam/steam/SteamApps/common/Half-Life/valve_hd/SAVE .  Just copy the whole "SAVE" folder from there, up one directory to just ~/.steam/steam/SteamApps/common/Half-Life so that your saves are in ~/.steam/steam/SteamApps/common/Half-Life/SAVE.

---

### Post by Bölvaður on 2013-02-08
Thank you, will do when I will play the game over the weekend.

---

### Post by Bölvaður on 2013-02-08
> **gerowen said:**
> The saves are currrently in ~/.steam/steam/SteamApps/common/Half-Life/valve_hd/SAVE .  Just copy the whole "SAVE" folder from there, up one directory to just ~/.steam/steam/SteamApps/common/Half-Life so that your saves are in ~/.steam/steam/SteamApps/common/Half-Life/SAVE.

The correct destination for me was ~/Steam/SteamApps/common/Half-Life/**valve**/SAVE

---

