---
title: "Auto-symlink whenever a file is added to a directory?"
date: 2009-05-27
forum: General Help
---

### Post by WindPower on 2009-05-27
Hello,
I'm trying to get a certain game to work with both Wine and Windows. I actually have succeeded, the game runs perfectly on both OSes using the same installation files. What I thought I'd do was to create a symlink in "$WINEPREFIX/drive_c/Program Files", named with the default folder name fo the game, pointing to its equivalent on my Windows partition (/media/Windows/Program Files/Game name). This worked except for one thing: sound. The game in question required a DLL override for the sound to work, so one of the game files had to be replaced. Sadly, doing so broke the game on Windows. So what I did was to delete the symlink I had created, and replace it with a standard folder with the same name, then adding a symlink of every file in that folder, except that darn DLL file. So far so good, it works perfectly on both OSes and I'm fine with that. My question is not about getting that game to work (because it does), but rather, how to make this setup "auto-update" itself. If the game files ever change (they get renamed or deleted or some files get added) because of an update or something, some symlinks will be broken or missing. The broken symlinks don't bother me much because the game is not going to use them anyway, but the missing symlinks will.
So, how can I make it so that whenever a file is added in the "real" game folder, a symlink to it is created in my Wine game folder? This wasn't a problem by symlinking the whole directory, but now that I'm symlinking each file in this directory, it could become one. It's not a major one, though; I guess each time there's a change, I could reinstall the game completely in Windows, then recreate the symlinks in Linux. I just want to know if there's a better and mroe elegant way of doing so :)
Also, while broken symlinks don't bother me, I'd like to know if there's a way to auto-delete them, that'd be cool too.

---

### Post by KeyserSoze93 on 2009-05-27
it's not automatic, but lndir may well be what you want.

```
man lndir
```

---

### Post by WindPower on 2009-05-27
That's fine, I could change the game's launcher in Linux so that it runs lndir before launching the game. Thanks~
(For the record, lndir requires the xutils-dev package)

---

