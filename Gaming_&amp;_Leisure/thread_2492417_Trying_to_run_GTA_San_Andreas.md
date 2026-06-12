---
title: "Trying to run GTA San Andreas"
date: 2023-11-10
forum: Gaming &amp; Leisure
---

### Post by gtasalover on 2023-11-10
Hey there,

So, I've switched to Linux since the last year since I've got involved with programming and overall i like it,
You surely have more access than windows and it allows me to run and test different codes such in python directly since i'm going to use most of them on some Linux server,

In the meanwhile, I've tried to download and play a couple of Windows games using Wine, but sadly encountered some problems for each of them,
For example, I've downloaded several PC Games from [this website]("https://thebroadswords.com/"), but most of them will run with black screen,
The same games are running well on my friend's PC, but can't run using Wine for some reasons,

Do you have any recommendations? How can i solve this?

---

### Post by Rubi1200 on 2023-11-10
You need to check the Wine database to see what works and what doesn't.

Start here:
[https://appdb.winehq.org/](https://appdb.winehq.org/)

---

### Post by rectec794613 on 2024-01-22
Try using Proton, which is based on Wine but has many enhancements. I use the GloriousEggroll version which has even more enhancements and fixes on top of that. It can be downloaded [here]("https://github.com/GloriousEggroll/proton-ge-custom/releases"). Try the latest version and if that fails try an older one like 7.55.

Extract GE-Proton to a folder that you prefer. Open a terminal in the folder for your game's EXE. Then you'll want to type the *path-to-proton/files/bin/wine64* (or *path-to-proton/files/bin/wine* for 32-bit games), and a space followed by the name of the game's EXE file. For example, this is how I would do it on my system. I have the releases of GE-Proton stored in .proton in my home folder:
```
~/.proton/Proton-7.55/files/bin/wine64 game.exe
```

A trick I like to use when having trouble running games with Wine/Proton is to rename .wine in the home directory to .wine.old and let Wine start from a clean slate.

---

### Post by maximge on 2024-05-21
You can find the procedure here: [https://steamcommunity.com/sharedfiles/filedetails/?id=2206594453](https://steamcommunity.com/sharedfiles/filedetails/?id=2206594453)

---

