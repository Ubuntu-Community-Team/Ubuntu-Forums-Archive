---
title: "KDE SC Games in Lubuntu"
date: 2014-01-10
forum: Gaming &amp; Leisure
---

### Post by nLpPyXR on 2014-01-10
I've got two simple questions:

1. is it possible to get a single game rather than the entire "kdegames" package? for example sudo apt-get install KGoldrunner.

2. would installing kdegames, a single game, or a couple of them also install the entire KDE package and/or a bunch of extra stuff? I had that happen once when I installed KTorrent :(

---

### Post by R33D3M33R on 2014-01-10
1.) look here for package names contained in the kdegames metapackage: [http://packages.ubuntu.com/saucy/kdegames](http://packages.ubuntu.com/saucy/kdegames)
2.) this depends ... click on the package (for example: [http://packages.ubuntu.com/saucy/bomber](http://packages.ubuntu.com/saucy/bomber)) and you will see what it needs (depends). Alternatively, just run:

```
sudo apt-get install your_game_name_here
```

and apt-get will show you which packages will be installed. 
All kdegames have probably the same dependencies: once you install one, the other one probably won't need additional packages.

---

### Post by nLpPyXR on 2014-01-10
oh man, 240+ Megs of extra space needed = hundreds of packages.

Not worth it; I wish someone with the appropriate skill-set would translate a few or all of those games to LXDE though. Thanks for the fast reply R33D3M33R.

---

### Post by dannyboy79 on 2014-01-10
not that this matters but 240+ megabytes of space is nothing for game(s)

---

### Post by nLpPyXR on 2014-01-10
> **dannyboy79 said:**
> not that this matters but 240+ megabytes of space is nothing for game(s)

for modern or not-so-old games? sure

but we're talking about NES-level casual stuff here

---

### Post by R33D3M33R on 2014-01-11
Well, the problem is that these games were developed with core KDE libraries. Even if a game doesn't need to display HTML content, the libraries that allow this, must be installed on disk because of dependencies. This is the reason why the installation would be so big. The game files alone are pretty small, under 10 MB.
I do agree that this is quite a lot to install, especially if you have a small SSD/disk or running the system off a SD card. But on the other hand: i think I saw somewhere that games included with Windows 7 (solitaire, minesweeper, ...) take up ~150 MB. In comparison to the Windows XP version that required a few MB is this enormous, and it's basically the same stuff.

---

### Post by oldrocker99 on 2014-01-11
The KDE team is working on KDE programs **not** needing lotsa libraries, so do stay tuned. Unlike GNOME developers (who appear to be fooling themselves about what makes their interface "better"), the KDE developers actually are trying to make the K Desktop Environment just plain **better**.

---

### Post by PaulW2U on 2014-01-11
> **oldrocker99 said:**
> The KDE team is working on KDE programs **not** needing lotsa libraries, so do stay tuned. Unlike GNOME developers (who appear to be fooling themselves about what makes their interface "better"), the KDE developers actually are trying to make the K Desktop Environment just plain **better**.

I'm assuming you're referring to KDE5 here?

---

### Post by nLpPyXR on 2014-01-11
> **oldrocker99 said:**
> The KDE team is working on KDE programs **not** needing lotsa libraries, so do stay tuned. Unlike GNOME developers (who appear to be fooling themselves about what makes their interface "better"), the KDE developers actually are trying to make the K Desktop Environment just plain **better**.

sweet; I'll most definitely stay tuned.

---

